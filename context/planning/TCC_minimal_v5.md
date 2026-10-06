# Planejamento de TCC — v5-Minimal
 
## Avaliação experimental dos dois custos de uma camada arquitetural desacoplada (harness) para integração de modelos de IA em aplicações web
 
> **Versão 5-Minimal — escopo reduzido a dois benchmarks, cronograma replanejado.**
> Derivada de `Full-Research_v5.md`. Curso: Engenharia de Software. Prazo: 12 meses.
>
> **Decisão central desta versão:** o trabalho passa a medir **duas** dimensões — substituibilidade (B1) e eficiência energética (B2) — em vez de quatro. Recuperação de falhas (B3) e auditabilidade (B4) **permanecem implementadas no artefato**, mas saem dos objetivos e dos resultados. A justificativa não é apenas prazo: B1 e B2 são as duas metades de um mesmo argumento — **o benefício alegado da camada e o preço que ela cobra**. B3 e B4 são benefícios adicionais, não o trade-off central.
 
---
 
## 1. Título provisório
 
**"Projeto e avaliação experimental de uma camada arquitetural desacoplada agêntica (harness) para integração de modelos de IA em aplicações web: custo de substituição de provedor e custo energético"**
 
*(O subtítulo é opcional, mas torna o recorte explícito já na capa — útil para evitar a pergunta "por que só duas dimensões?" na banca.)*
 
---
 
## 2. Contexto e definição operacional
 
A integração de LLMs em aplicações web costuma ser feita por chamadas diretas à API do provedor espalhadas pelo código de negócio, sem separação entre o que o modelo decide e o que o sistema garante. A literatura chama de **harness** a camada de software ao redor do modelo responsável por execução de ferramentas, gerenciamento de estado e recuperação de erros.
 
**Definição operacional:** harness é a **camada arquitetural intermediária entre a aplicação web e o provedor de IA**, que abstrai e centraliza as interações da aplicação com modelos e agentes. A aplicação não acessa SDKs de provedores diretamente.
 
**Aplicação Web → Harness → Provedor/Modelo de IA**
 
Responsabilidades atribuídas ao harness:
 
| Responsabilidade | Papel no v5-Minimal |
| :---- | :---- |
| Abstração e padronização da comunicação com provedores | **Medida** (B1) |
| Orquestração de chamadas e execução autônoma de ferramentas | **Medida** (B2 — é a carga de trabalho do nível 2) |
| Gerenciamento de contexto e estado da interação | Implementada, não medida |
| Tratamento e recuperação de falhas | Implementada, não medida |
| Registro estruturado de eventos e auditoria | Implementada, não medida |
 
O harness **não** implementa lógica de negócio, não substitui a interface com o usuário e não treina modelos.
 
**Ancoragem teórica:** as responsabilidades acima são mapeadas contra o catálogo de padrões arquiteturais de **Liu et al. (2025, R21 — JSS, Q1)**; a camada é tratada como *middleware* no sentido de **Issarny et al. (2007, R12)**; a terminologia "agêntico" segue **Sapkota et al. (2026, R8)**, que posiciona este harness como "AI Agents" (execução controlada de ferramentas), não "Agentic AI" (multiagente).
 
**Hipótese, não pressuposto:** não se assume que o harness melhora o sistema. A tese a testar é que **a camada reduz o custo de trocar de provedor e cobra por isso um custo energético**; se ela reduz o custo de troca **sem** custo energético relevante, ou se cobra um custo alto sem reduzir nada, ambos são resultados válidos e publicáveis.
 
### 2.1. Posicionamento da lacuna
 
A literatura de "harness" ainda é dominada por *gray literature* e preprints; a base validada deste trabalho não depende deles (§7).
 
**Formulação defensável:** Liu et al. (R21) discutem trade-offs dos padrões agênticos **qualitativamente, a partir de literatura**; Kandogan et al. (R10) e Zhu et al. (R11) propõem e comparam arquiteturas **sem avaliação empírica controlada**. Este trabalho **mede quantitativamente**, em estudo controlado com e sem a camada, dois desses trade-offs. Afirmar que "a literatura não discute trade-offs da camada" é falso e derrubável em banca.
 
**Consequências:** a fundamentação se apoia em conceitos consolidados de arquitetura (estilos, ADRs, C4, atributos de qualidade); preprints arXiv aparecem **rotulados como preprint** e não sustentam nenhuma afirmação central; o histórico de *gray literature* do termo é declarado abertamente — postura com precedente Q1 no próprio R21, construído incorporando literatura cinzenta de forma declarada.
 
---
 
## 3. Problema de pesquisa
 
> A introdução de uma camada arquitetural intermediária entre uma aplicação web e um provedor de IA reduz o custo de substituição do provedor, e qual é o custo energético dessa redução?
 
---
 
## 4. Objetivos
 
*Conforme os critérios da Aula 3 (Prof. Emanuel Coutinho) e de Wazlawick (2009): verbo único no objetivo geral, específicos verificáveis ao final do trabalho, separação entre objetivo técnico e objetivo de pesquisa.*
 
### Objetivo geral
 
> **Avaliar** experimentalmente o trade-off entre desacoplamento e eficiência introduzido por uma camada de harness entre aplicações web e provedores de modelos de IA, confrontando o custo de substituição de provedor com o custo energético de execução, em comparação com uma integração direta sem essa camada.
 
Projetar e implementar a camada continuam necessários, mas como **metodologia** (§6.1), não como verbos do objetivo geral.
 
### Objetivos específicos
 
1. **Quantificar** o custo de substituição de provedor de IA com e sem a camada, por métricas comportamentais e estruturais objetivas — casos de uso preservados após a troca, arquivos/linhas alterados, dependências diretas ao SDK, testes quebrados (Benchmark 1).
2. **Mensurar** o impacto da camada sobre a eficiência energética da aplicação, comparando energia por requisição, energia por token e potência de GPU com e sem harness, sob critério de gating de corretude funcional (Benchmark 2).
3. **Confrontar** os dois resultados para caracterizar em que condições o desacoplamento obtido compensa o custo energético cobrado.
**Realocados:** definição operacional do harness → §2; documentação arquitetural e implementação → §6.1; disponibilização de código e artefatos → §10.
 
---
 
## 5. Escopo
 
### 5.1. Dentro do escopo
 
**Uma aplicação web de domínio único** que: tenha ao menos um fluxo usando LLM **com chamadas de ferramenta**; permita repetir requisições de forma determinística; permita simular/injetar falhas (ex.: timeout, erro de conexão, rate limit, resposta inválida) — **condição de viabilidade do plano B (§9.2)**, que depende de um injetor de falhas configurável; não exija dados sensíveis; tenha lógica de negócio simples o bastante para separar a integração de IA.
 
**Duas versões funcionalmente equivalentes** — a condição experimental:
 
- **Versão H (com harness):** aplicação → harness → provedor.
- **Versão D (direta):** aplicação → SDK do provedor, sem camada intermediária.
A paridade funcional entre H e D é **pré-condição de validade** de ambos os benchmarks e deve ser verificada por uma suíte de testes comum antes de qualquer coleta (§6.1).
 
**MVP do harness — cinco componentes**, dos quais três não são medidos mas são **pré-requisito técnico** dos que são:
 
| # | Componente | Por que está no MVP |
| :---- | :---- | :---- |
| 1 | Interface abstrata para dois provedores/adaptadores | Objeto do B1 |
| 2 | Execução autônoma de ferramentas (2–3 determinísticas) | Carga de trabalho do nível 2 do B2 |
| 3 | Normalização de requisições e respostas | Sem ela, a troca de provedor do B1 não é comparável |
| 4 | Política de retry para falhas transitórias | Sem ela, uma falha de rede contamina a medição energética do B2 |
| 5 | Registro estruturado de eventos | Sem ele, não há como correlacionar cada janela de telemetria à requisição correspondente, nem verificar a métrica comportamental do B1 |
 
Os componentes 4 e 5 entram como **decisão arquitetural documentada em ADR**, não como objeto de medição.
 
### 5.2. Fora do escopo — e o que isso custa
 
| Item | Destino | Custo declarado |
| :---- | :---- | :---- |
| **B3 — Recuperação de falhas** | Protocolo redigido e mantido em apêndice como **reserva ativa** (§9.2); retry implementado, não medido | Não se afirma nada sobre a eficácia da política de retry |
| **B4 — Auditabilidade** | Log estruturado implementado e justificado por ADR (R18, R19, R20); nenhuma medição | Não se afirma nada sobre completude ou reconstrução causal |
| Sistemas multiagente, fine-tuning, segurança geral de IA, MCP, persistência complexa, guardrails | Trabalhos futuros | — |
| Estudo de usabilidade | Fora | Valida-se a arquitetura, não a experiência de uso |
 
**Limitação a escrever explicitamente no TCC:** o trabalho mede dois dos quatro atributos usualmente atribuídos a uma camada de harness. A escolha não é arbitrária — B1 mede o **benefício** mais alegado da camada e B2 mede o **preço** que ela cobra; juntos formam um trade-off fechado. B3 e B4 medem benefícios adicionais, cuja ausência não invalida o argumento central, mas restringe a conclusão a "vale a pena pelo desacoplamento?" e não a "vale a pena de modo geral?".
 
---
 
## 6. Metodologia
 
### 6.1 Fase de solução
 
- **Documentação arquitetural antes da implementação:** C4 (contexto, containers, componentes) e ADRs para cada decisão relevante — incluindo ADRs para retry e logging, que justificam sua presença sem medição.
- **Implementação** do harness como biblioteca separada da aplicação, com interface estável e encapsulamento dos detalhes de provedor.
- **Implementação da versão D** (controle), com paridade funcional verificada por suíte de testes comum. Sem paridade verificada, nenhum dos dois benchmarks é válido.
- **Congelamento de versões** de dependências a partir do início da implementação.
- **Para o B2:** congelar driver/firmware de GPU e versão do modelo local a partir do início da coleta — a coleta é fragmentada em meses e qualquer atualização intermediária vira variável de confusão entre sessões.
- Desenho experimental e taxonomia de validade conforme **Wohlin et al. (2024, R1)**.
### 6.2 Benchmark 1 — Substituibilidade
 
**Mede:** custo de trocar o provedor/modelo de IA.
**Variável independente:** presença/ausência da camada (H vs. D).
**Não depende de GPU** — pode ser executado a qualquer momento do cronograma.
 
| Dimensão | Métrica | Papel |
| :---- | :---- | :---- |
| Comportamento | Casos de uso que continuam funcionando após a troca | **Primária** |
| Alteração no código | Arquivos, linhas e módulos alterados | Primária |
| Impacto estrutural | Componentes ou interfaces afetados | Primária |
| Dependência | Referências diretas ao SDK do provedor | Primária |
| Testes | Testes alterados ou quebrados | Primária |
| Esforço | Tempo de implementação da substituição | Secundária |
 
**Protocolo:** implementar o mesmo caso de uso em H e D; trocar o provedor em ambas; medir. Escolher dois provedores com **APIs razoavelmente distintas**, para tornar o teste exigente — a escolha deve ser declarada e justificada.
 
**Mitigação de viés do experimentador** (o autor implementa as duas versões conhecendo a hipótese): (a) métricas estruturais e comportamentais objetivas como primárias; (b) tempo apenas como secundária e, se possível, cronometrado por um colega; (c) ordem de implementação e cronometragem registradas e declaradas em §6.4.
 
**Ancoragem:** **Mo et al. (2023, R14)** é o precedente empírico mais próximo — compara funções serverless com biblioteca de abstração vs. APIs nativas usando métricas estruturais de código como variável dependente primária; justifica os proxies adotados e expõe a mesma limitação de construto. **Kaur et al. (2017, R13)** e **Issarny et al. (2007, R12)** legitimam "mitigar lock-in por camada intermediária" como problema arquitetural consolidado fora de IA.
 
**Controle de custo:** a troca de provedor pode usar um **provedor mock determinístico** como segunda condição, se o orçamento de API real for limitante — desde que declarado. As métricas estruturais primárias não dependem de chamadas reais.
 
### 6.3 Benchmark 2 — Eficiência energética
 
**Mede:** custo energético introduzido pela camada, e se ele é justificado pela funcionalidade entregue.
**Variável independente:** presença/ausência da camada, sobre **um** modelo aberto hospedado localmente.
 
#### Matriz experimental reduzida — 4 células
 
| | Versão D (direta) | Versão H (harness) |
| :---- | :---- | :---- |
| **Nível 1 — requisição simples** (single-shot, sem ferramenta) | célula 1 | célula 2 |
| **Nível 2 — requisição agêntica** (loop com 2 chamadas de ferramenta) | célula 3 | célula 4 |
 
Os dois níveis não são arbitrários: **o nível 1 isola o overhead do invólucro** (o que a camada custa só por existir no caminho) e **o nível 2 mede o overhead do loop agêntico** (o que ela custa ao orquestrar ferramentas). A diferença entre os dois níveis é, por si só, um achado — e é exatamente o padrão que **Ifath & Haque (2026, R6)** caracteriza como workflow agêntico multi-requisição. *(R6 é resumo estendido em volume de abstracts do SIGMETRICS: citável, não sustenta sozinho afirmação central.)*
 
**Unidade de medida:** a **requisição completa, incluindo o loop de ferramentas** — não a chamada isolada ao modelo.
 
#### Métricas
 
| Dimensão | Métrica | Papel |
| :---- | :---- | :---- |
| Energia por requisição | Joules/req, por integração de potência instantânea (NVML) | Primária |
| Energia por token de saída | J/token | Primária |
| Potência média/pico da GPU | Watts — diagnóstico extensional vs. intensivo | Primária |
| Latência | p50/p95/p99 | Primária |
| Utilização de GPU | % | Secundária (diagnóstica) |
| Carbono estimado | gCO2e, pelo fator da matriz energética local | Secundária |
 
**Medição real, não estimada:** **Fernandez et al. (2025, R3 — ACL)** mostra que estimativas baseadas em FLOPs subestimam significativamente o consumo real — argumento direto para telemetria NVML. **Luccioni et al. (2024, R2 — FAccT)** ancora as métricas primárias e a distinção potência instantânea vs. energia total. **Wilkins et al. (2024, R4)** complementa com modelos de energia por carga.
 
**Critério de aceitação (gating de qualidade):** a comparação só é válida se o harness não degradar a taxa de sucesso funcional:
 
> H<sub>energia</sub>: Aceita ⟺ (A<sub>harness</sub> ≥ A<sub>direto</sub>) ∧ (Ē<sub>harness</sub> < Ē<sub>direto</sub>, ou comparável) ∧ (p < 0,05) ∧ (\|δ Cliff's\| acima do limiar adotado)
 
Se A<sub>harness</sub> < A<sub>direto</sub>, a análise energética daquela condição é descartada — economia por perda de funcionalidade não é eficiência.
 
**Protocolo estatístico:** Shapiro-Wilk; em caso de rejeição (esperado, dado o perfil de cauda longa), Mann-Whitney U (α = 0,05) com Cliff's delta e Holm-Bonferroni. Com 4 células, são **2 comparações pareadas** (H vs. D em cada nível) × 4 métricas primárias = 8 testes sob correção — matriz pequena o bastante para que a correção não destrua o poder estatístico. ⚠️ **Pendência (§12):** decidir a adequação de Mann-Whitney U para percentis de cauda antes de congelar o protocolo.
 
**Protocolo de telemetria:** NVML/nvidia-smi a 100 ms; energia por integração da potência instantânea; baseline de ociosidade subtraído; estabilização térmica entre baterias.
 
**Decomposição do overhead:** reportar potência média separada de duração, para diagnosticar se o custo é **extensional** (mesmo regime de potência por mais tempo) ou **intensivo** (maior demanda instantânea). Lastro externo: **Vellaisamy et al. (2026, R5 — IEEE ISPASS)**.
 
**Infraestrutura:** requer GPU **sem compartilhamento simultâneo** — leituras NVML refletem a GPU física inteira, e contenção invalida a comparação. Há acesso confirmado a janelas exclusivas do servidor institucional, de poucas horas, com recorrência semanal/mensal.
 
**Orçamento de janelas — calcular no piloto, não estimar agora.** No mês 6 o piloto deve produzir: (a) tempo médio por requisição em cada nível; (b) tempo de estabilização térmica; (c) n necessário por célula para o tamanho de efeito esperado. Desses três números sai o total de horas de GPU exigido, que é a entrada do gate de decisão do mês 8 (§9.2). Sem esse cálculo, o risco do B2 permanece não quantificado.
 
**Setup por sessão:** intercalar as condições H e D dentro da mesma janela (controla temperatura e estado de cache KV); baseline de ociosidade e estabilização térmica no início de cada sessão; registrar metadados (data, driver, temperatura ambiente aproximada) para análise de variância entre sessões.
 
### 6.4 Ameaças à validade
 
*Taxonomia de Wohlin et al. (2024, R1). Riscos operacionais estão em §9.3.*
 
**Validade interna**
 
- *Viés do experimentador (B1):* o autor implementa H e D conhecendo a hipótese. → Métricas primárias estruturais e comportamentais; tempo como secundária, idealmente por terceiro; ordem e cronometragem declaradas.
- *Falta de paridade funcional entre H e D:* se as versões não fizerem exatamente a mesma coisa, tanto o B1 quanto o B2 comparam objetos diferentes. → Suíte de testes comum executada em ambas antes de cada coleta, com resultado registrado.
- *Contaminação da leitura de potência por GPU compartilhada (B2):* NVML reflete a GPU física inteira. → Usar apenas janelas exclusivas; registrar processos concorrentes (`nvidia-smi --query-compute-apps`) e descartar ou declarar como amostra degradada a sessão que não puder ser garantida.
- *Variabilidade entre sessões (B2):* coleta fragmentada em meses expõe a variação de driver, temperatura e versão de modelo. → Congelar driver e modelo; baseline e estabilização no início de **cada** sessão; intercalar condições dentro da sessão; reportar variância **entre** sessões separadamente da variância **dentro** de sessão.
**Validade externa**
 
- *Uma aplicação, um domínio:* declarar como estudo de caso único; escolher domínio representativo de integrações típicas de LLM; publicar harness e protocolo para replicação.
- *Um único modelo local (B2):* **limitação introduzida por esta versão.** Não se pode afirmar se o overhead da camada escala com o tamanho do modelo. → Declarar explicitamente; registrar como trabalho futuro imediato; se sobrarem janelas de GPU após completar a matriz mínima, um segundo modelo entra como extensão oportunista, não como compromisso.
- *Dois provedores (B1):* escolher APIs razoavelmente distintas e declarar a escolha.
**Validade de construto**
 
- *"Substituibilidade" por proxies estruturais* pode não capturar esforço cognitivo de manutenção. → Combinar com a métrica comportamental e com o tempo; declarar o proxy (mesma limitação reconhecida em R14).
- *"Eficiência energética" por consumo agregado* mascara o trade-off potência × duração. → Reportar potência média separada de energia total e duração (R5).
**Validade de conclusão**
 
- *n grande detecta diferenças triviais (B2).* → Reportar Cliff's delta além do p-valor, com Holm-Bonferroni.
- *Qualidade desigual da evidência do ecossistema.* → Zhu et al. (R11) marca explicitamente achados reportados por fornecedores; adotar o mesmo critério ao citar frameworks.
### 6.5 Base metodológica reaproveitada de trabalho prévio do autor
 
O B2 reaproveita elementos validados em **Barros et al. (2026, R7)** — *"Single Prompt vs. Debate Multiagente: Uma Análise de Telemetria de Hardware em Tarefas de Contexto Longo com Llama 3.2 2B"*, LIII SEMISH / CSBC 2026, SBC (DOI 10.5753/semish.2026.23941):
 
1. **Critério de gating de qualidade** — a comparação energética só vale se a corretude funcional não degradar.
2. **Pacote estatístico** — Shapiro-Wilk → Mann-Whitney U → Cliff's delta → Holm-Bonferroni.
3. **Protocolo de telemetria NVML** — 100 ms, integração de potência, baseline de ociosidade, estabilização térmica.
4. **Decomposição extensional vs. intensivo** — com lastro externo adicional em R5.
**Diferença a declarar:** no trabalho anterior a coleta ocorreu em GPU H100 dedicada, em infraestrutura contínua. Aqui, o acesso exclusivo é em **janelas recorrentes de poucas horas** — o que obriga a fragmentar a coleta.
 
**Ganho desta versão:** o reaproveitamento metodológico reduz substancialmente o risco do B2. O protocolo não é novo para o autor; o que é novo é o objeto medido e o regime de acesso ao hardware.
 
⚠️ **Pendência de autoria (§12):** a lista registrada no CrossRef é *Barros; **da Silva, V. M. A.**; dos Santos; Viana; Gomes de B. Filho*. Confirmar o registro de autor a usar e padronizar a citação.
 
---
 
## 7. Base bibliográfica
 
Fonte: `consolidated_references.md` (21 referências validadas, metadados reverificados contra CrossRef/editora em 09–10/09/2026). **Critério:** publicação revisada por pares ou livro de editora acadêmica — arXiv isolado não conta como validado.
 
**No v5-Minimal: 14 referências ativas, 7 em reserva.** O corte de escopo não reduz a qualidade da base — reduz a superfície que ela precisa cobrir.
 
### 7.1 Ativas
 
| Bloco | Referências |
| :---- | :---- |
| Metodologia experimental | R1 (Wohlin) |
| Fundamentação: middleware, terminologia, padrões | R12 (Issarny), R8 (Sapkota), R21 (Liu) |
| Estado da arte / tabela comparativa | R21, R11 (Zhu), R10 (Kandogan) |
| B1 — Substituibilidade | R14 (Mo), R13 (Kaur), R12 |
| B2 — Eficiência energética | R2 (Luccioni), R3 (Fernandez), R4 (Wilkins), R5 (Vellaisamy), R6 (Ifath) |
| Base metodológica do autor | R7 (Barros) |
 
### 7.2 Em reserva
 
| Referências | Quando entram |
| :---- | :---- |
| R15 (Mendonça), R16 (Sedghpour), R17 (Aderaldo), R9 (Chang & Geng) | Se o gate do mês 8 acionar o B3 (§9.2) — a base do benchmark de falhas já está pronta |
| R18 (Pivot Tracing), R19 (OmegaLog), R20 (Phiri) | ADR de logging estruturado (§6.1) e seção de trabalhos futuros |
 
### 7.3 Achado citável sobre a própria busca
 
Cinco iterações de busca sistemática mostraram que terminologia madura de engenharia de software (middleware, vendor lock-in, medição de potência em GPU, distributed tracing) rende **45–70%** de literatura revisada por pares, enquanto "harness/scaffolding" rende **~35%**, por ser recente e dominada por preprint. É argumento direto a favor da decisão de §2.1 — fundamentar o trabalho em conceitos consolidados e tratar "harness" como objeto de estudo aplicado.
 
---
 
## 8. Estrutura de capítulos
 
| Capítulo | Conteúdo | Peso |
| :---- | :---- | :---- |
| 1. Introdução | Motivação, problema, objetivos (§4), justificativa do recorte de duas dimensões, estrutura | Leve |
| 2. Fundamentação Teórica | Arquitetura de software (estilos, ADRs, C4, atributos de qualidade) + harness como middleware (R12, R21) + terminologia agêntica e tool calling (R8) + Green AI: potência vs. energia, extensional vs. intensivo (R2, R3, R5) | Médio |
| 3. Trabalhos Relacionados | Integração ad hoc de LLM + frameworks (R11) + arquiteturas propostas (R21, R10) + lock-in fora de IA (R13, R14) + medição energética (R2–R6) + preprints rotulados + **tabela comparativa** com coluna "avaliação empírica controlada" | Médio |
| 4. Metodologia | Fase de solução + B1 + B2 + ameaças à validade + base reaproveitada | **Pesado** |
| 5. Resultados e Análise | Resultado do B1; resultado do B2 por nível; **síntese do trade-off** (objetivo 3); dados brutos em apêndice | **Pesado** |
| 6. Conclusão | Contribuições, limitações (incluindo o que B3/B4 não respondem), trabalhos futuros | Leve |
| Apêndices | Guia do harness + ADRs + dados brutos + **protocolo do B3 em reserva** | — |
 
---
 
## 9. Cronograma replanejado (12 meses)
 
### 9.1 Linha do tempo
 
| Mês | Entrega principal | Depende de GPU? |
| :---- | :---- | :---- |
| **1–2** | Revisão bibliográfica (base já consolidada em §7) e definição do caso de uso | Não |
| **3** | C4, ADRs e contrato da interface do harness | Não |
| **4** | MVP do harness (5 componentes) — **versão H** | Não |
| **5** | **Versão D** (controle) + suíte de paridade funcional verde em ambas | Não |
| **6** | **TCC I** + piloto instrumentado: valida NVML, mede tempo/requisição por nível, calcula o **orçamento de horas de GPU** (§6.3) | 1 janela curta |
| **7** | **B1 executado e analisado** — resultado completo no bolso antes de qualquer risco de hardware | Não |
| **8** | Coleta B2 — lote 1 · **GATE DE DECISÃO** (§9.2) | Sim |
| **9** | Coleta B2 — lote 2 | Sim |
| **10** | Coleta B2 — lote 3 e fechamento da matriz | Sim |
| **11** | Análise integrada e redação | Não |
| **12** | Revisão e defesa | Não |
 
### 9.2 Gate de decisão — fim do mês 8
 
**Regra:** ao fim do mês 8, comparar as horas de GPU exclusiva efetivamente obtidas (meses 6–8) contra o orçamento calculado no piloto do mês 6.
 
| Condição | Ação |
| :---- | :---- |
| Horas obtidas ≥ 50% do orçamento | **Seguir com o B2.** Meses 9–10 completam a matriz. |
| Horas obtidas < 50% do orçamento | **Acionar o B3 no lugar do B2.** O TCC passa a ser B1 + B3, ambos sem dependência de hardware. |
 
**Viabilidade do plano B:** o protocolo do B3 já está redigido (apêndice) e suas referências já estão validadas (R15, R16, R17, R9); a política de retry já está implementada desde o mês 4. O que falta construir é o injetor de falhas configurável e executar n ≈ 20–30 por tipo de falha — **estimativa de 3 a 4 semanas**, o que cabe nos meses 9–10 com folga. O custo de manter essa rede de segurança é redigir o protocolo do B3 uma vez, no mês 3, e não tocá-lo mais.
 
**Por que o mês 8, e não depois:** a decisão precisa de quatro meses de folga até a defesa. Um gate no mês 10 não deixaria tempo para executar o plano B.
 
### 9.3 Riscos operacionais
 
| Risco | Mitigação |
| :---- | :---- |
| **Janelas de GPU exclusiva insuficientes (B2)** | Matriz reduzida a 4 células; coleta em lotes desde o mês 8; gate formal no mês 8 com plano B pronto (§9.2) |
| **Versão D e H divergirem funcionalmente** | Suíte de paridade comum, verde obrigatória antes de cada coleta (§6.1); qualquer divergência invalida a comparação |
| Custo de API real (B1) | Orçamento máximo definido; provedor mock determinístico como condição principal; métricas estruturais não dependem de chamadas reais |
| Ecossistema muda no meio do projeto | Congelamento de versões obrigatório desde o mês 4 |
| Bibliografia parcialmente em preprint | Rotular explicitamente; as 14 referências ativas sustentam as afirmações centrais |
| Tool calling aumenta o esforço de implementação | 2–3 ferramentas determinísticas, definidas no mês 3 |
| Banca questionar o recorte de duas dimensões | Justificativa na Introdução e nas Limitações: B1 e B2 são benefício e preço da mesma decisão arquitetural (§5.2) |
 
### 9.4 O que mudou em relação ao cronograma da v5
 
- **B1 antecipado do mês 10 para o mês 7.** É o benchmark sem dependência de hardware; executá-lo cedo garante que o TCC tenha ao menos um resultado completo desde o mês 7.
- **Coleta do B2 distribuída em três meses (8–10)** em vez de concentrada, compatível com janelas curtas e recorrentes.
- **Piloto do mês 6 ganhou função nova:** calcular o orçamento de horas de GPU. Antes era só validação de protocolo.
- **Meses 11–12 livres de coleta.** Na v5, atrasos de coleta comiam o tempo de redação.
- **Implementação encurtada:** os meses 7–8, antes dedicados à "versão principal", ficaram livres porque o MVP de cinco componentes é menor e cabe nos meses 4–5.
---
 
## 10. Contribuições esperadas
 
1. **Arquitetural:** definição operacional, limites e responsabilidades de uma camada de integração de IA, mapeada contra padrões já publicados (R21).
2. **Experimental:** medição controlada do trade-off entre desacoplamento e custo energético — **a quantificação que a literatura existente discute apenas qualitativamente**, e que nenhum dos trabalhos relacionados (R10, R11, R21) realiza.
3. **Prática:** implementação de referência com ADRs, testes de paridade, dados brutos e protocolo reproduzível.
---
 
## 11. Pitch para o orientador
 
> "Professor(a), proponho um TCC em arquitetura de software aplicada a sistemas com IA: medir experimentalmente o trade-off central de uma camada desacoplada (harness) entre uma aplicação web e um provedor de IA — de um lado, quanto ela reduz o custo de trocar de provedor; do outro, quanto ela cobra em energia para fazer isso. A literatura já propõe arquiteturas desse tipo e discute seus trade-offs qualitativamente (Liu et al., JSS 2025); o que não existe é medição controlada com e sem a camada. Escolhi deliberadamente medir duas dimensões em vez de quatro, para caber em um ano com profundidade. Já domino a metodologia de telemetria de hardware do benchmark energético — validada em artigo aceito no SEMISH/CSBC 2026 — e a base bibliográfica está consolidada em referências revisadas por pares."
 
**Venues realistas (CBSoft 2027):** CTIC-ES (concurso de iniciação científica, desenhado para graduação); SBES — Trilha de Ferramentas, se o harness for entregue como ferramenta demonstrável; SBCARS, que já listou "design e arquitetura de software assistido por IA" como tópico. **Não almejar** SBES Research Track ou ICSE Research Track nesta primeira submissão. O tema do CSBC 2026 — "Transformação Digital para um Mundo em Emergência Climática" — dá alinhamento temático à dimensão Green AI.
 
---
 
## 12. Próximos passos e pendências
 
**Próximos passos**
 
1. Confirmar orientador (preferir quem já orientou no formato "construir + avaliar empiricamente").
2. Escolher o caso de uso e os dois provedores do B1 (mês 1).
3. Redigir o protocolo do B3 em reserva (mês 3) — custo pequeno, habilita o plano B do gate.
4. Definir as 2–3 ferramentas determinísticas e o orçamento máximo de API (mês 3).
5. Especificar a suíte de paridade funcional H/D antes de escrever a versão D (mês 4).
**Pendências abertas** (nenhuma bloqueia o pitch)
 
1. **Teste estatístico do B2** — adequação de Mann-Whitney U para comparar percentis de cauda. Decidir antes de congelar o protocolo (mês 3).
2. **Autoria de R7 (SEMISH)** — confirmar se "Vitor Manoel A. da Silva" é o registro de autor e padronizar a citação.
3. **Escolha do modelo local do B2** — depende do que estiver hospedado e estável no servidor institucional; decidir junto com o piloto do mês 6.
4. **AGENT 2026** — escolher um artigo específico do volume (DOI 10.1145/3786167) se o texto for citá-lo nominalmente; verificar a precisão de qualquer alegação sobre o escopo temático do workshop.
5. **Busca bibliográfica opcional** — base acadêmica formal para ADRs, C4 e ISO/IEC 25010, hoje ancorados apenas na prática.
---
 
## 13. Registro de versões
 
**Histórico condensado:** v1 → v2 incorporou tool calling ao MVP; v2 → v3 fundiu a apresentação dos benchmarks; v3 → v4 substituiu "Overhead de desempenho" por "Eficiência energética" e adicionou a base metodológica reaproveitada; v4 → v5 reescreveu os objetivos conforme a Aula 3, integrou a base bibliográfica consolidada e reformulou a alegação de lacuna.
 
**v5 → v5-Minimal:**
 
- Escopo reduzido a **dois benchmarks** (B1, B2). B3 e B4 saem dos objetivos e dos resultados; retry e logging **permanecem implementados** como pré-requisito técnico e decisão arquitetural em ADR (§5.1).
- Objetivos específicos reduzidos de 5 para **3**, com o terceiro reformulado de "comparar quatro dimensões" para "confrontar benefício e custo".
- Problema de pesquisa e título reescritos em torno do trade-off **desacoplamento × energia**.
- **B2 com matriz reduzida a 4 células** (1 modelo × 2 níveis de carga × 2 condições), com os níveis desenhados para separar overhead de invólucro de overhead de loop agêntico.
- **Cronograma replanejado:** B1 antecipado para o mês 7; coleta do B2 distribuída nos meses 8–10; meses 11–12 livres de coleta.
- **Gate de decisão formal no mês 8** com plano B (B3) documentado e viável (§9.2).
- Nova ameaça de validade externa declarada: **um único modelo local**.
- Base bibliográfica segmentada em 14 ativas e 7 em reserva (§7).