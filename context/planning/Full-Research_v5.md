# Planejamento de TCC — Avaliação experimental dos trade-offs de uma camada arquitetural desacoplada agêntica (harness)
 
> **Versão 5 — enxugamento + incorporação dos objetivos revisados e da base bibliográfica consolidada.**
> Documento de trabalho para a conversa com o orientador e referência ao longo do TCC I e II. Curso: Engenharia de Software. Prazo: 12 meses.
>
> Mudanças em relação à v4: Seção 4 (Objetivos) reescrita conforme `objetivos_tcc_diagnostico_proposta_v1.md`; nova Seção 7 integrando `consolidated_references.md`; preprints rebaixados a citação rotulada; alegação de lacuna reformulada; changelog reduzido a registro curto (§15).
 
---
 
## 1. Título provisório
 
**"Projeto e avaliação experimental de uma camada arquitetural desacoplada agêntica (harness) para integração de modelos de IA em aplicações web"**
 
---
 
## 2. Contexto e definição operacional
 
A integração de LLMs em aplicações web costuma ser feita de forma pouco estruturada — chamadas diretas à API do provedor espalhadas pelo código de negócio, sem separação entre o que o modelo decide e o que o sistema garante. A literatura recente chama de **harness** a camada de software ao redor do modelo responsável por execução de ferramentas, gerenciamento de memória, persistência de estado e recuperação de erros.
 
**Definição operacional adotada:** harness é a **camada arquitetural intermediária entre a aplicação web e o provedor de IA**, que abstrai e centraliza as interações da aplicação com modelos e agentes. A aplicação não acessa SDKs de provedores diretamente; comunica-se com o harness por interface própria e padronizada.
 
**Aplicação Web → Harness → Provedor/Modelo de IA**
 
Responsabilidades atribuídas ao harness neste trabalho:
 
- abstração e padronização da comunicação com diferentes provedores;
- gerenciamento de contexto e estado da interação;
- orquestração de chamadas ao modelo e **execução autônoma de ferramentas** (tool calling);
- tratamento e recuperação de falhas;
- registro estruturado de eventos, métricas e informações de auditoria.
O harness **não** implementa lógica de negócio, não substitui a interface com o usuário e não treina modelos.
 
**Ancoragem teórica (evita definição *ad hoc*):** as responsabilidades acima são mapeadas contra o catálogo de padrões arquiteturais para agentes baseados em foundation models de **Liu et al. (2025, R21 — J. Systems and Software, Q1)**; a camada é tratada conceitualmente como *middleware* no sentido de **Issarny et al. (2007, R12)**; a terminologia "agêntico" segue a taxonomia de **Sapkota et al. (2026, R8)**, que permite posicionar este harness no lado "AI Agents" (execução controlada de ferramentas) e não "Agentic AI" (multiagente), coerente com o que está fora do escopo (§5).
 
**Hipótese, não pressuposto:** não se assume que o harness torna o sistema melhor. Os efeitos sobre substituibilidade, energia, recuperação de falhas e auditabilidade são o objeto da avaliação experimental. A implementação em uma tecnologia específica é **meio de demonstração de uma arquitetura de referência**, não a contribuição central.
 
### 2.1. Posicionamento da lacuna (reformulado)
 
O termo "harness" carece de definição canônica e sua literatura ainda é dominada por *gray literature* e preprints. A partir de 2026 há proceedings revisados por pares (AGENT 2026, co-localizado com o ICSE 2026 — volume ACM, DOI 10.1145/3786167) e surveys, mas a base validada deste trabalho não depende deles.
 
**Formulação defensável da lacuna:** Liu et al. (R21) já discutem trade-offs dos padrões agênticos — **qualitativamente, a partir de literatura**; Kandogan et al. (R10) e Zhu et al. (R11) propõem e comparam arquiteturas/frameworks **sem avaliação empírica controlada**. Este trabalho **mede quantitativamente**, em estudo controlado com e sem a camada, os trade-offs que a literatura documenta apenas em prosa. Afirmar que "a literatura não discute trade-offs da camada" é falso e derrubável em banca.
 
**Consequências metodológicas:**
 
- A fundamentação se apoia em conceitos consolidados de arquitetura (estilos, ADRs, C4, atributos de qualidade), tratando "harness" como objeto de estudo aplicado.
- Preprints arXiv citados no texto (2606.20683, 2603.25723, 2605.18747, 2605.23950, 2607.08028) devem aparecer **rotulados como preprint** e **não podem sustentar nenhuma afirmação central** — R21, R11 e R10 assumem esse papel.
- A metodologia declara abertamente o histórico de *gray literature* do termo. Há precedente Q1 para essa postura: o próprio catálogo de R21 foi construído incorporando literatura cinzenta de forma declarada.
---
 
## 3. Problema de pesquisa
 
> Quais são os efeitos da introdução de uma camada arquitetural intermediária entre uma aplicação web e um provedor de IA sobre a substituibilidade do provedor, a eficiência energética, o tratamento de falhas e a auditabilidade da aplicação?
 
---
 
## 4. Objetivos
 
*Reescritos conforme os critérios da Aula 3 (Prof. Emanuel Coutinho) e o critério de Wazlawick (2009): verbo único no objetivo geral, objetivos específicos verificáveis ao final do trabalho, separação entre objetivo técnico (construir o artefato) e objetivo de pesquisa (o que se descobre com ele).*
 
### Objetivo geral
 
> **Avaliar** experimentalmente os trade-offs arquiteturais introduzidos por uma camada de harness desacoplada entre aplicações web e provedores de modelos de IA, quantificando seus efeitos sobre substituibilidade de provedor, eficiência energética, recuperação de falhas e auditabilidade, em comparação com uma integração direta sem essa camada.
 
Projetar e implementar a camada continuam necessários, mas como **metodologia** (§6.1), não como verbos do objetivo geral.
 
### Objetivos específicos
 
1. **Quantificar** o custo de substituição de provedor de IA com e sem a camada, por métricas estruturais objetivas — arquivos/linhas alterados, dependências diretas ao SDK, testes quebrados (Benchmark 1).
2. **Mensurar** o impacto da camada sobre a eficiência energética da aplicação, comparando energia por requisição, energia por token e potência de GPU com e sem harness, sob critério de gating de corretude funcional (Benchmark 2).
3. **Determinar** a taxa de recuperação automática de falhas provida pela camada sob diferentes tipos de falha injetada — timeout, erro de conexão, rate limit, resposta inválida (Benchmark 3).
4. **Verificar** a completude dos registros de auditoria e a capacidade de reconstrução causal de erros a partir deles, por checklist estrutural e cenários com causa raiz conhecida (Benchmark 4).
5. **Comparar** os resultados das quatro dimensões para caracterizar em que condições a introdução da camada se justifica.
**Realocados (saíram de "objetivos", continuam no TCC):** definição operacional do harness → §2; documentação arquitetural e implementação da camada → §6.1 (Metodologia); disponibilização de código, artefatos e contrato arquitetural → §11 (Contribuições).
 
---
 
## 5. Escopo
 
**Dentro do escopo:**
 
- **Uma aplicação web de domínio único** que: tenha ao menos um fluxo usando LLM **com chamadas de ferramenta**; permita repetir requisições; permita simular falhas; não exija dados sensíveis; tenha lógica de negócio simples o bastante para separar a integração de IA.
- **MVP científico com cinco componentes:**
  1. Interface abstrata para dois provedores/adaptadores.
  2. Normalização de requisições e respostas.
  3. Registro estruturado de eventos e erros.
  4. Política de retry e tratamento de falhas transitórias.
  5. **Execução autônoma de ferramentas (tool calling) orquestrada pelo harness** — escopo principal, não extensão. Conjunto pequeno e controlado (2–3 ferramentas determinísticas).
- **Versão de controle ("sem harness")** implementando o mesmo caso de uso por chamadas diretas ao SDK — é condição experimental obrigatória, não opcional, e está no cronograma (§9).
- Avaliação por benchmarks técnicos automatizados, sem estudo com usuários.
**Extensões condicionais** (somente com os 4 benchmarks completos, nesta ordem): MCP como mecanismo de exposição de ferramentas; múltiplos modelos com capacidades distintas; persistência complexa de estado; guardrails avançados.
 
**Fora do escopo:** sistemas multiagente; fine-tuning ou treinamento; segurança geral de IA (além do necessário ao B4); estudo de usabilidade — **troca deliberada, a declarar explicitamente nas limitações**: valida-se a arquitetura, não a experiência de uso.
 
---
 
## 6. Metodologia
 
### 6.1 Fase de solução
 
- **Documentação arquitetural antes da implementação:** diagramas C4 (contexto, containers, componentes) e ADRs para cada decisão relevante. O diagrama de containers explicita a posição do harness entre aplicação e provedores.
- **Implementação** da camada como middleware/biblioteca separada da aplicação, com interface estável e encapsulamento dos detalhes de provedor.
- **Congelamento de versões** de dependências a partir do início da implementação, sem atualização até o fim da coleta (o ecossistema MCP/orquestração muda rápido o suficiente para quebrar o experimento no meio).
- **Para o Benchmark 2:** congelar também driver/firmware de GPU e versões dos modelos locais a partir do início da coleta energética — a coleta se estende por múltiplas sessões ao longo de meses (§6.2), e qualquer atualização intermediária vira variável de confusão entre sessões.
- Desenho experimental e taxonomia de validade conforme **Wohlin et al. (2024, R1)**.
### 6.2 Fase de validação — quatro benchmarks
 
#### Benchmark 1 — Substituibilidade
 
**Mede:** custo de trocar o provedor/modelo de IA.
**Variável independente:** presença/ausência da camada.
 
| Dimensão | Métrica | Papel |
| :---- | :---- | :---- |
| Comportamento | Casos de uso que continuam funcionando após a troca | **Primária** |
| Alteração no código | Arquivos, linhas e módulos alterados | Primária |
| Impacto estrutural | Componentes ou interfaces afetados | Primária |
| Dependência | Referências diretas ao SDK do provedor | Primária |
| Testes | Testes alterados ou quebrados | Primária |
| Esforço | Tempo de implementação da substituição | Secundária |
 
**Protocolo:** estudo de caso controlado — mesmo caso de uso com e sem a camada, troca de modelo em ambas as versões.
 
**Mitigação de viés do experimentador** (o autor implementa as duas versões conhecendo a hipótese): (a) métricas estruturais objetivas como primárias; (b) tempo apenas como secundária e, se possível, cronometrado por um colega; (c) ordem de implementação e cronometragem registradas e declaradas em §6.3.
 
**Ancoragem:** **Mo et al. (2023, R14)** é o precedente empírico mais próximo — compara funções serverless com biblioteca de abstração vs. APIs nativas usando métricas estruturais de código como variável dependente primária; justifica o uso de "arquivos/linhas/referências ao SDK" como proxies aceitos e expõe a mesma limitação de construto. **Kaur et al. (2017, R13)** e **Issarny et al. (2007, R12)** legitimam "mitigar lock-in por camada intermediária" como problema arquitetural consolidado fora de IA.
 
#### Benchmark 2 — Eficiência energética
 
**Mede:** custo energético (e seus correlatos de latência/tokens) introduzido pela camada, e se ele é justificado pela funcionalidade adicional entregue.
**Variável independente:** presença/ausência da camada, sobre modelos abertos hospedados localmente (conforme disponibilidade no servidor institucional).
 
| Dimensão | Métrica | Papel |
| :---- | :---- | :---- |
| Energia por requisição | Joules/req, por integração de potência instantânea (NVML) | Primária |
| Energia por token de saída | J/token | Primária |
| Potência média/pico da GPU | Watts — diagnóstico extensional vs. intensivo | Primária |
| Latência | p50/p95/p99 | Primária |
| Utilização de GPU | % | Secundária (diagnóstica) |
| Carbono estimado | gCO2e, pelo fator da matriz energética local | Secundária |
 
**Unidade de medida:** a **requisição completa, incluindo o loop de ferramentas**, não a chamada isolada ao modelo — justificada por **Ifath & Haque (2026, R6)**, que caracteriza trade-offs performance-energia especificamente em workflows agênticos multi-requisição. *(R6 é resumo estendido em volume de abstracts do SIGMETRICS: citável, mas não sustenta sozinho afirmação central.)*
 
**Medição real, não estimada:** **Fernandez et al. (2025, R3 — ACL)** mostra que estimativas baseadas em FLOPs subestimam significativamente o consumo real — argumento direto para telemetria NVML. **Luccioni et al. (2024, R2 — FAccT)** ancora as métricas primárias (J/req, J/token) e a distinção potência instantânea vs. energia total. **Wilkins et al. (2024, R4)** complementa com modelos de energia por carga.
 
**Critério de aceitação (gating de qualidade):** a comparação energética só é válida se o harness não degradar a taxa de sucesso funcional (ex.: chamadas de ferramenta corretamente executadas):
 
> H<sub>energia</sub>: Aceita ⟺ (A<sub>harness</sub> ≥ A<sub>direto</sub>) ∧ (Ē<sub>harness</sub> < Ē<sub>direto</sub>, ou comparável) ∧ (p < 0,05) ∧ (\|δ Cliff's\| acima do limiar adotado)
 
Se A<sub>harness</sub> < A<sub>direto</sub>, a análise energética daquela condição é descartada — economia por perda de funcionalidade não é eficiência.
 
**Protocolo estatístico:** Shapiro-Wilk sobre os dados de energia; em caso de rejeição (esperado, dado o perfil de cauda longa), Mann-Whitney U (α = 0,05) com Cliff's delta e correção de Holm-Bonferroni para as métricas comparadas simultaneamente. ⚠️ **Pendência aberta (§15):** a adequação de Mann-Whitney U para comparar percentis de cauda precisa ser decidida antes do congelamento do protocolo.
 
**Protocolo de telemetria:** NVML/nvidia-smi com amostragem de 100 ms; energia por integração da potência instantânea; baseline de ociosidade subtraído; estabilização térmica entre baterias.
 
**Decomposição do overhead:** reportar potência média separada de duração, para diagnosticar se o custo é **extensional** (mesmo regime de potência por mais tempo) ou **intensivo** (maior demanda instantânea). Lastro externo direto: **Vellaisamy et al. (2026, R5 — IEEE ISPASS)**, que decompõe overhead de orquestração visível no host (tradução de framework, tradução CUDA, lançamento de kernel) separando-o do trabalho no device, validado em H100/H200.
 
**Infraestrutura:** o experimento requer GPU **sem compartilhamento simultâneo** — leituras NVML refletem a GPU física inteira, não a fração de um processo, e contenção invalida a comparação. Há acesso confirmado a janelas exclusivas do servidor institucional, tipicamente poucas horas por sessão, com recorrência semanal/mensal — o que implica coleta fragmentada ao longo de meses (§6.3 e §10).
 
**Setup:** dentro de cada janela, intercalar as condições com/sem harness (controla temperatura e estado de cache KV); registrar metadados de sessão (data, driver, temperatura ambiente aproximada) para análise de variância entre sessões.
 
#### Benchmark 3 — Recuperação de falha
 
**Mede:** capacidade de tratamento automatizado de falhas.
**Variável independente:** tipo de falha injetada.
**Variável dependente:** taxa de recuperação automática (%) e tempo até recuperação.
 
**Protocolo:** harness de injeção de falhas configurável; n ≈ 20–30 tentativas por tipo. Considera-se recuperada a operação que, após a falha, conclui o caso de uso dentro de um limite de tempo e sem duplicar efeitos colaterais.
 
| Falha | Recuperação esperada |
| :---- | :---- |
| Timeout transitório | Retry com limite |
| Erro de conexão | Retry com backoff |
| Rate limit | Espera respeitando política |
| Resposta inválida | Validação e nova tentativa |
| Indisponibilidade persistente | Falha controlada e observável |
| Erro de ferramenta | Encerramento seguro ou fallback |
 
**Ancoragem:** a escolha de Retry e Circuit Breaker como objeto não é *ad hoc* — **Mendonça et al. (2020, R15 — ICSA)** os modela formalmente como CTMC e quantifica seu impacto sobre atributos de qualidade. **Sedghpour et al. (2022, R16 — ICPE)** fornece base empírica para os **parâmetros concretos** de retry/backoff/circuit breaker do MVP (hoje sem ancoragem). **Aderaldo et al. (2024, R17 — SPE)** é o precedente metodológico mais direto (injeção controlada + medição de padrões de resiliência) e a base para justificar — ou aumentar — o n por tipo de falha.
 
**Delimitação honesta:** **Chang & Geng (2025, R9 — PVLDB)** mostra que "recuperação" em sistemas com LLM exige compensação semântica (padrão Saga), não apenas retry de transporte. O B3 mede falhas de transporte/protocolo; isso deve estar escrito como limite do benchmark.
 
#### Benchmark 4 — Auditabilidade
 
**Mede:** (a) % de elementos esperados presentes no log; (b) **taxa de reconstrução causal** — em k cenários com causa raiz conhecida, fração em que os logs permitem reconstruir por script a cadeia completa (requisição → tentativa → chamada de ferramenta → erro → política aplicada → encerramento).
**Protocolo:** checklist estrutural verificado por script + cenários de reconstrução causal, sem avaliação humana.
 
**Dimensões avaliadas:** completude, consistência, rastreabilidade, privacidade, utilidade diagnóstica.
 
**Elementos esperados no log:** identificador da requisição; identificador da execução; timestamp; provedor; modelo; versão da aplicação; tentativa; ferramenta chamada; resultado ou classe do resultado; erro; política aplicada; causa de encerramento; correlação entre eventos.
 
**Ancoragem externa do checklist** (contra a circularidade de "checklist definido pelo autor e verificado pelo autor"): **Phiri (2025, R20)** oferece definição operacional de auditabilidade para IA agêntica em 8 axiomas — ⚠️ venue de prestígio não verificável, serve para ancorar conceito, não para sustentar alegação empírica; reforçar com a especificação aberta do **OpenTelemetry** (rotulada como documento técnico) e com os padrões transversais de guardrail e registro de execução de **R21** (mapeamento pendente, §15). O mecanismo de correlação causal cross-tier tem referência canônica em **Mace et al. (2018, R18 — ACM TOCS, *Pivot Tracing*)**; **Hassan et al. (2020, R19 — NDSS, *OmegaLog*)** é a mais próxima do enunciado exato do B4 e fornece dois usos: justificar que reconstrução causal exige correlacionar camadas (não uma única trace) e oferecer o overhead de ~4% como **ponto de comparação externo** para o custo de observabilidade do harness — ligando B4 a B2.
 
**Nota de privacidade:** não registrar indiscriminadamente prompts e respostas completas (privacidade, custo, exposição). Usar conteúdo redigido, hashes, identificadores ou ambientes sintéticos.
 
### 6.3 Ameaças à validade
 
*Taxonomia de Wohlin et al. (2024, R1). Riscos operacionais e de execução do projeto estão em §10.*
 
**Validade interna**
 
- *Viés do experimentador (B1):* o autor implementa as duas versões conhecendo a hipótese. → Métricas primárias estruturais e comportamentais; tempo como secundária, idealmente por terceiro; ordem e cronometragem declaradas.
- *Contaminação de leitura de potência por GPU compartilhada (B2):* NVML reflete a GPU física inteira. → Usar apenas janelas exclusivas; se uma janela não puder ser garantida, registrar processos concorrentes (`nvidia-smi --query-compute-apps`) e declarar a sessão como amostra degradada ou descartá-la.
- *Variabilidade entre sessões de coleta (B2):* coleta fragmentada em meses expõe a variação de driver/firmware, temperatura e versão de modelo. → Congelar driver e modelos (§6.1); baseline de ociosidade e estabilização térmica **no início de cada sessão**; intercalar condições dentro da sessão; reportar variância **entre** sessões separadamente da variância **dentro** de sessão.
- *Falhas sintéticas (B3):* podem não representar falhas reais. → Declarar como amostra de conveniência; se possível, complementar com falhas observadas em logs reais no piloto.
**Validade externa**
 
- *Uma aplicação, um domínio:* declarar como estudo de caso único; escolher domínio representativo de integrações típicas de LLM; publicar harness e protocolo para replicação.
- *Dois provedores/adaptadores:* escolher provedores com APIs razoavelmente distintas, para tornar o teste mais exigente, e declarar a escolha.
**Validade de construto**
 
- *"Substituibilidade" por proxies estruturais* pode não capturar esforço cognitivo de manutenção. → Combinar com a medida comportamental (casos de uso que continuam funcionando) e com o tempo; declarar o proxy (mesma limitação reconhecida em R14).
- *"Auditabilidade" por checklist* captura formato, não utilidade diagnóstica. → Taxa de reconstrução causal (B4b) + ancoragem externa do checklist (R20 / OpenTelemetry / R21).
- *"Eficiência energética" por consumo agregado* mascara o trade-off potência × duração. → Reportar potência média separada de energia total e duração (R5).
**Validade de conclusão**
 
- *n grande detecta diferenças triviais (B2).* → Reportar Cliff's delta além do p-valor, com Holm-Bonferroni.
- *n ≈ 20–30 por tipo de falha (B3) limita a precisão.* → Reportar intervalos de confiança das proporções, não apenas porcentagens pontuais.
- *Qualidade desigual da evidência do ecossistema.* → Zhu et al. (R11) marca explicitamente achados reportados por fornecedores para distingui-los de evidência revisada por pares; adotar o mesmo critério ao citar frameworks.
### 6.4 Base metodológica reaproveitada de trabalho prévio do autor
 
O Benchmark 2 reaproveita elementos validados em **Barros et al. (2026, R7)** — *"Single Prompt vs. Debate Multiagente: Uma Análise de Telemetria de Hardware em Tarefas de Contexto Longo com Llama 3.2 2B"*, LIII SEMISH / CSBC 2026, Gramado/RS, SBC (DOI 10.5753/semish.2026.23941):
 
1. **Critério de gating de qualidade** — a comparação energética só vale se a corretude funcional não degradar.
2. **Pacote estatístico** — Shapiro-Wilk → Mann-Whitney U → Cliff's delta → Holm-Bonferroni, validado sobre dados de energia com cauda longa.
3. **Protocolo de telemetria NVML** — 100 ms, integração de potência, baseline de ociosidade, estabilização térmica.
4. **Decomposição extensional vs. intensivo** — agora com lastro externo adicional em R5.
**Diferença a declarar:** no trabalho anterior a coleta ocorreu em GPU H100 dedicada, em infraestrutura contínua. Aqui, o acesso exclusivo é em **janelas recorrentes de poucas horas**, o que obriga a fragmentar a coleta — ameaça ausente no trabalho anterior (§6.3).
 
⚠️ **Pendência de autoria (§15):** a lista oficial de autores registrada no CrossRef é *Barros; **da Silva, V. M. A.**; dos Santos; Viana; Gomes de B. Filho*. Confirmar se "Vitor Manoel A. da Silva" é o registro de autor a usar, e manter a citação consistente com o nome publicado — afeta §6.4, §12 e §13.
 
---
 
## 7. Base bibliográfica
 
Documento-fonte: `consolidated_references.md` (21 referências validadas, metadados reverificados contra CrossRef/editora em 09–10/09/2026). **Critério de inclusão:** publicação revisada por pares confirmada ou livro de editora acadêmica — arXiv isolado não conta como validado.
 
### 7.1 Núcleo por dimensão
 
| Bloco | Referências | Situação |
| :---- | :---- | :---- |
| Metodologia experimental | R1 (Wohlin, Springer) | Suficiente |
| Fundamentação: middleware, terminologia, padrões | R12, R8, R21 | Boa |
| Estado da arte de harness / arquiteturas agênticas | R21, R11, R10, R9 | Boa — deixou de depender de preprint |
| B1 — Substituibilidade | R14, R13, R12 | Boa (3) |
| B2 — Eficiência energética | R2, R3, R4, R5, R6 | Muito boa (5) |
| B3 — Recuperação de falhas | R15, R16, R17 (+ R9) | Boa (3+1) |
| B4 — Auditabilidade | R18, R19, R20 (+ R21 a verificar) | Fechada (3), com R20 de venue frágil |
| Trabalho prévio do autor | R7 | Validado, com pendência de autoria |
 
### 7.2 Mapa de uso por capítulo
 
| Capítulo / seção | Referências |
| :---- | :---- |
| Cap. 1 — Introdução e lacuna | R21, R8, R10, R11 |
| Cap. 2 — Definição operacional de harness | R21, R12, R8, R9 |
| Cap. 2 — Green AI (potência vs. energia; extensional vs. intensivo) | R2, R3, R5 |
| Cap. 2 — Auditabilidade e reconstrução causal | R20 (definição), R18, R19 (mecanismo) |
| Cap. 2 — Resiliência (Retry, Circuit Breaker) | R15 |
| Cap. 3 — Tabela comparativa | R11 (base), R21, R10, R9 |
| Cap. 3 — Lock-in / abstração fora de IA | R13, R12, R14 |
| Cap. 3 — Medição energética de LLM | R2, R3, R4, R5, R6 |
| Cap. 4 / §6.1 — Desenho geral | R1 |
| §6.2 B1 / B2 / B3 / B4 | R14, R13, R12 / R2, R3, R4, R5, R6 / R16, R17, R15, R9 / R19, R18, R20, R21 |
| §6.3 — Ameaças à validade | R1, R5, R14, R11 |
| §6.4 — Base reaproveitada | R7, R3, R5 |
 
### 7.3 Achado citável sobre a própria busca
 
Cinco iterações de busca sistemática mostraram um padrão consistente: terminologia madura de engenharia de software (middleware, vendor lock-in, medição de potência em GPU, retry/circuit breaker, distributed tracing) rende **45–70%** de literatura revisada por pares; a terminologia "harness/scaffolding" rende **~35%**, por ser recente e dominada por preprint. Isso é argumento direto a favor da decisão metodológica de §2.1 — fundamentar o trabalho em conceitos consolidados e tratar "harness" como objeto de estudo aplicado.
 
Segundo achado aproveitável na motivação do Cap. 1 e em §6.3: os veículos rejeitados por falta de indexação concentram alegações de melhoria muito específicas e não auditáveis ("redução de 84,2% no MTTR"). É literalmente o tipo de afirmação que o Benchmark 4 deveria permitir auditar.
 
---
 
## 8. Estrutura de capítulos
 
| Capítulo | Conteúdo |
| :---- | :---- |
| 1. Introdução | Motivação, problema, objetivos (§4), estrutura |
| 2. Fundamentação Teórica | Arquitetura de software (estilos, ADRs, C4, atributos de qualidade) + harness como middleware (R12, R21) + tool calling e terminologia agêntica (R8) + MCP + Green AI: potência vs. energia, extensional vs. intensivo (R2, R3, R5) + auditabilidade (R20, R18, R19) + resiliência (R15) |
| 3. Trabalhos Relacionados | Integração ad hoc de LLM + frameworks de orquestração (R11) + arquiteturas/padrões propostos (R21, R10, R9) + lock-in fora de IA (R13, R14) + medição energética (R2–R6) + preprints rotulados + **tabela comparativa** posicionando a lacuna |
| 4. Metodologia | Fase de solução + quatro benchmarks + ameaças à validade (§6.3) + base reaproveitada (§6.4) |
| 5. Resultados e Análise | Um resultado por benchmark + síntese dos trade-offs (objetivo específico 5); dados brutos em apêndice |
| 6. Conclusão | Contribuições, limitações, trabalhos futuros |
| Apêndices | Guia de uso do harness + dados brutos |
 
**Atributos da tabela comparativa (Cap. 3):** nível de abstração; suporte a múltiplos provedores; mecanismo de recuperação de falha; observabilidade/auditoria nativa; acoplamento à infraestrutura; **presença de avaliação empírica controlada** (coluna que evidencia a lacuna).
 
---
 
## 9. Cronograma (12 meses)
 
| Período | Entrega principal |
| :---- | :---- |
| Meses 1–2 | Revisão bibliográfica e definição do problema |
| Meses 3–4 | Projeto (C4/ADRs), contratos e protocolo experimental |
| Mês 5 | Protótipo mínimo **+ versão de controle ("sem harness")** |
| Mês 6 | TCC I e validação do protocolo (piloto reduzido) |
| Meses 7–8 | Implementação da versão principal **+ início da coleta energética em lotes** |
| Mês 9 | Piloto completo dos benchmarks; B1 e B3 executáveis |
| Mês 10 | Coleta definitiva (B1, B3, B4) e continuação do B2 |
| Mês 11 | Análise e redação |
| Mês 12 | Revisão e defesa |
 
**Notas de risco de cronograma:**
 
- A construção da versão de controle entra explicitamente no Mês 5 — sem ela não há B1 nem B2.
- A coleta do B2 **não** pode se concentrar no Mês 10: as janelas de GPU exclusiva são curtas e recorrentes, então a coleta começa em lotes incrementais no Mês 7, aproveitando cada janela conforme surgir.
- Os meses 7–10 concentram risco. Mitigação parcial: antecipar B1 (não depende de GPU) para o Mês 9.
**Ponto de corte se atrasar** — prioridade: (1) substituibilidade; (2) recuperação de falhas; (3) auditabilidade; (4) eficiência energética. **Não cortar a documentação arquitetural (C4/ADRs)** — é a parte mais barata de manter e a mais valorizada numa banca de arquitetura.
 
---
 
## 10. Riscos operacionais
 
*Riscos de execução do projeto. Distinto de §6.3, que trata do rigor do desenho experimental.*
 
| Risco | Mitigação |
| :---- | :---- |
| Ecossistema (MCP, frameworks) muda rápido | Congelar versões é obrigatório, não opcional (§6.1) |
| "Harness" sem definição canônica | A contribuição não é inventar o conceito, e sim aplicar princípios consolidados de arquitetura e medir os trade-offs; ancoragem em R21/R12 (§2) |
| Bibliografia de apoio parcialmente em preprint | Rotular explicitamente; base validada de 21 referências (§7) assume o peso das afirmações centrais |
| Validação sem usuários → pergunta previsível da banca | Antecipar na seção de limitações |
| **Custo de provedores reais (B1, B3, B4)** | Orçamento máximo definido; créditos gratuitos e modelos menores; provedor mock determinístico como condição principal quando aplicável. O B2 não tem esse risco (modelos locais) |
| **Disponibilidade de janelas de GPU exclusiva (B2)** | Coleta em lotes incrementais a partir do Mês 7; se o tempo total de janelas não cobrir todas as células, priorizar as comparações com/sem harness nos níveis mais representativos do uso real |
| Tool calling no escopo aumenta o esforço | Conjunto pequeno e determinístico (2–3 ferramentas); ponto de corte (§9) preserva os 4 benchmarks sobre extensões |
 
---
 
## 11. Contribuições esperadas
 
1. **Arquitetural:** definição operacional, limites e responsabilidades de uma camada de integração de IA, mapeada contra padrões já publicados (R21).
2. **Experimental:** comparação controlada entre integração direta e integração por camada intermediária, em quatro dimensões — **a medição quantitativa que a literatura existente discute apenas qualitativamente**.
3. **Prática:** implementação de referência com ADRs, testes, dados brutos e protocolo reproduzível, publicados quando possível.
---
 
## 12. Pitch para o orientador
 
> "Professor(a), proponho um TCC em arquitetura de software aplicada a sistemas com IA: avaliar experimentalmente os trade-offs de uma camada arquitetural desacoplada (harness) entre uma aplicação web e um provedor de IA, via quatro benchmarks técnicos — substituibilidade, eficiência energética, recuperação de falha e auditabilidade. A literatura já propõe arquiteturas desse tipo e discute seus trade-offs qualitativamente (Liu et al., JSS 2025); o que não existe é medição controlada com e sem a camada. Já domino a metodologia de telemetria de hardware do benchmark energético — validada em artigo aceito no SEMISH/CSBC 2026 — e tenho a base bibliográfica consolidada em 21 referências revisadas por pares."
 
---
 
## 13. Relevância e possíveis venues
 
- **AGENT 2026** (workshop do ICSE 2026, Rio de Janeiro) publicou proceedings revisados por pares e convidou trabalhos para edição especial da IEEE Software — sinal de que a comunidade trata o tema como relevante, não hype.
- **Meta realista (CBSoft 2027):** CTIC-ES (concurso de iniciação científica, desenhado para graduação); SBES — Trilha de Ferramentas, se o harness for entregue como ferramenta demonstrável; SBCARS, que já listou "design e arquitetura de software assistido por IA" como tópico.
- **Não almejar** SBES Research Track ou ICSE Research Track nesta primeira submissão.
- **Timing:** os resultados do TCC II (meados de 2027) precisam estar prontos para a chamada do CBSoft 2027 — a coleta não pode escorregar para o último mês.
- **Alinhamento temático:** o CSBC 2026 adotou o tema "Transformação Digital para um Mundo em Emergência Climática"; a dimensão Green AI alinha o TCC ao momento da comunidade nacional.
- **Trajetória demonstrada:** artigo aceito no LIII SEMISH aplicando exatamente a metodologia NVML e o protocolo estatístico do B2 (§6.4).
---
 
## 14. Próximos passos
 
1. Confirmar orientador (preferir quem já orientou trabalhos no formato "construir + avaliar empiricamente").
2. Resolver as quatro pendências bibliográficas de §15 antes de fechar o Cap. 2.
3. Detalhar o protocolo de cada benchmark até o nível de script executável (meses 2–3), incluindo as mitigações de viés (B1), o desenho estatístico definitivo (B2) e os cenários de reconstrução causal (B4).
4. Rascunhar os primeiros ADRs junto com o desenho C4.
5. Definir o conjunto de 2–3 ferramentas determinísticas e o orçamento máximo do experimento com provedor real.
---
 
## 15. Registro de versões e pendências abertas
 
**Histórico condensado:** v1 → v2 incorporou tool calling ao escopo do MVP; v2 → v3 fundiu a apresentação dos benchmarks e separou riscos de ameaças à validade; v3 → v4 substituiu "Overhead de desempenho" por "Eficiência energética" e adicionou a base metodológica reaproveitada (§6.4). *(O arquivo da v4 circulou com o nome de arquivo `..._v3.md`; esta versão corrige a numeração.)*
 
**v4 → v5 (esta versão):**
 
- §4 (Objetivos) reescrita conforme `objetivos_tcc_diagnostico_proposta_v1.md`: objetivo geral com verbo único (*avaliar*), cinco objetivos específicos verificáveis, e realocação dos objetivos técnicos e de disseminação para §6.1 e §11.
- Nova §7 integrando `consolidated_references.md`; cada benchmark de §6.2 passou a citar suas âncoras bibliográficas.
- §2.1: alegação de lacuna reformulada (medição quantitativa, não ausência de discussão); preprints rebaixados a citação rotulada, com R21/R11/R10 assumindo o estado da arte.
- B1: dimensão comportamental promovida a métrica primária.
- B4: ancoragem externa do checklist (R20 + OpenTelemetry + R21) contra a circularidade.
- §9: versão de controle explicitada no Mês 5; risco dos meses 7–10 parcialmente redistribuído.
- §10 convertida em tabela; changelog reduzido a este registro.
**Pendências abertas** (decisão do autor, nenhuma bloqueia o pitch):
 
1. **Teste estatístico do B2** — adequação de Mann-Whitney U para comparar percentis de cauda. Decidir antes de congelar o protocolo.
2. **Autoria de R7 (SEMISH)** — confirmar se "Vitor Manoel A. da Silva" é o registro de autor e padronizar a citação (§6.4).
3. **AGENT 2026** — escolher um artigo específico do volume (DOI 10.1145/3786167), já que §2.1 e §14 prometem citá-lo nominalmente.
4. **Mapear R21 contra §2 e contra os elementos esperados no log do B4** — tarefa concreta identificada e ainda não feita; se os padrões de guardrail/registro servirem, resolvem a circularidade do B4 sem depender de R20 (venue frágil).
5. **Busca bibliográfica opcional** — base acadêmica formal para ADRs, C4 e ISO/IEC 25010, hoje ancorados apenas na prática (§6.1 e Cap. 2 dependem deles).
6. **Precisão da alegação sobre o escopo temático do AGENT 2026** — verificar antes de afirmar em texto.