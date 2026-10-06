# Registro de ações — TCC Harness

> **Backlog vivo do projeto — ponto de entrada de toda sessão de trabalho.**
> Semeado a partir da análise crítica de `TCC_minimal_v5.md` (`planning/TCC_minimal_v5_critical_review.md`, 26/09/2026) e das pendências declaradas no próprio plano (§12).
> Itens fechados **não são apagados**: o campo *Decisão* de cada item forma o histórico de decisões do projeto.

## Como usar

- **Status:** `aberto` → `em análise` → `decidido` → `fechado` (decisão registrada no item **e** aplicada no documento-alvo).
- **Prioridade:** **P1** = afeta a validade do experimento ou trava o congelamento do protocolo (mês 3); **P2** = robustez, rastreabilidade ou plano B; **P3** = higiene, redação ou risco menor.
- **Prazo:** mês do cronograma (§9.1 do plano) até o qual a decisão precisa estar tomada; `imediato` = próxima sessão.
- **Ao fechar um item:** preencher o campo **Decisão** (o quê foi decidido, uma linha de porquê, onde foi aplicado). Decisões metodológicas substanciais do harness viram ADR no futuro repositório do artefato.
- **Documentos-alvo:** `planning/TCC_minimal_v5.md` (patch pontual ou nova versão), protocolos do B1/B2 (a redigir no mês 3), `planning/5w2h.md`, capítulos do TCC.
- **Escopo:** tarefas ordinárias do cronograma (§9.1) continuam no plano; este registro cobre **pendências e decisões**.
- **Git (se adotado):** um commit por item fechado — ex.: `fecha A07: política da versão D`.
- **Foco atual:** fechar o gate de abertura da introdução (A02 — falta só reconciliar caminho e commitar; A03) + ancorar o calendário (A27) + decisões do mês 1 (A04, A06 — evidência já reunida). *(atualizar esta linha ao fim de cada sessão)*

## 1. Painel

| ID | Ação | P | Prazo | Bloqueia | Status |
| :--- | :--- | :---: | :--- | :--- | :--- |
| A01 | Corrigir nome do arquivo-fonte no cabeçalho do plano | P3 | imediato | Introdução | **fechado** |
| A02 | Trazer `consolidated_references.md` para o repositório | P1 | imediato | Introdução | em análise |
| A03 | Confirmar orientador e endossar o recorte B1+B2 | P1 | mês 1 | Introdução | aberto |
| A04 | Escolher os dois provedores do B1; mock só como fallback declarado | P2 | mês 1 | — | aberto |
| A05 | Reinstalar "permite simular falhas" nos critérios de escolha da aplicação | P2 | mês 1 | Plano B | **fechado** |
| A06 | Confirmar autoria de R7 (SEMISH) e padronizar a citação | P3 | mês 1–2 | — | em análise |
| A07 | Definir política de implementação da versão D | P1 | mês 3 | Protocolo B1 | aberto |
| A08 | Pré-registrar o checklist da troca de provedor | P2 | mês 3 | Protocolo B1 | aberto |
| A09 | Decompor a métrica de alteração de código (modificados vs. adaptador) | P2 | mês 3 | Protocolo B1 | aberto |
| A10 | Definir fallback para a métrica de tempo (sem cronometrista) | P3 | mês 3 | — | aberto |
| A11 | Decidir medição de energia de CPU (RAPL) ou limitação declarada | P1 | mês 3 | Protocolo B2 | aberto |
| A12 | Definir escopo da interface: modelo local é 2º ou 3º adaptador? | P2 | mês 3 | MVP (mês 4) | aberto |
| A13 | Definir determinismo operacional + gate de contagem de tool calls | P1 | mês 3 | Protocolo B2 | aberto |
| A14 | Pré-especificar unidade amostral por lote (M requisições) | P2 | mês 3 | Piloto (mês 6) | aberto |
| A15 | Fechar o pacote estatístico definitivo (pendência §12.1 do plano) | P1 | mês 3 | Protocolo B2 | aberto |
| A16 | Definir família de testes vs. métricas descritivas (contagem de testes) | P1 | mês 3 | Protocolo B2 | aberto |
| A17 | Formalizar "comparável" como margem de não-inferioridade | P1 | mês 3 | Protocolo B2 | aberto |
| A18 | Fixar o limiar de Cliff's delta antes da coleta | P1 | mês 3 | Protocolo B2 | aberto |
| A19 | Definir critério operacional de paridade funcional H/D | P1 | mês 3–4 | Versão D (mês 5) | aberto |
| A20 | Redigir memo de pivô (moldura B1+B3) junto ao protocolo do B3 | P2 | mês 3 | Plano B | aberto |
| A21 | Definir efeito mínimo de interesse prático; n por simulação no piloto | P2 | mês 3 → 6 | Piloto (mês 6) | aberto |
| A22 | Incluir teste de sensibilidade (efeito piso) no piloto | P2 | mês 6 | Piloto (mês 6) | aberto |
| A23 | Reformular o gate do mês 8 para taxa projetada de acesso | P2 | mês 6 | Gate (mês 8) | aberto |
| A24 | Buscar base acadêmica formal para ADRs, C4 e ISO/IEC 25010 | P3 | antes do Cap. 2 | — | aberto |
| A25 | Escolher artigo específico do AGENT 2026, se citado nominalmente | P3 | antes do Cap. 3 | — | aberto |
| A26 | Nota de redação: capítulos sem herdar o meta-comentário do plano | P3 | redação (11–12) | — | aberto |
| A27 | Ancorar o "mês 1" do cronograma a uma data de calendário | P2 | imediato | Todos os prazos | aberto |
| A28 | Fazer o mapeamento responsabilidades do harness × padrões de R21 | P2 | mês 1–2 | Cap. 2; contribuição 1 | aberto |
| A29 | Escolher o modelo local e a stack de serving do B2 (pendência §12.3) | P2 | mês 3 (stack) / mês 6 (modelo) | MVP (mês 4); Piloto | aberto |

## 2. Gate de abertura da redação da introdução

A introdução **não depende dos detalhes de protocolo** (A07–A23): a moldura — problema (§3), objetivos (§4), posicionamento da lacuna (§2.1) e justificativa do recorte (§5.2) — já está definida e foi avaliada como o ponto mais forte do plano. Os itens de protocolo correm em paralelo e, ao fechar, apenas acrescentam precisão à metodologia; não mudam o que a introdução afirma.

Para abrir a redação, feche antes:

- [x] **A01** — higiene do cabeçalho do plano
- [ ] **A02** — base bibliográfica consolidada dentro do repositório (fonte única de verdade das citações)
- [ ] **A03** — orientador confirmado e recorte endossado (não se redige introdução de um recorte que ainda pode mudar)

**Ressalva (não bloqueia):** enquanto A28 estiver aberto, a introdução não deve afirmar que as responsabilidades do harness *já foram* mapeadas contra R21 — redigir como procedimento da fundamentação, não como fato consumado.

**Matéria-prima da introdução** (tudo já existe no plano): título e subtítulo (§1), contexto e definição operacional (§2), lacuna (§2.1), problema (§3), objetivos (§4), justificativa das duas dimensões (§5.2), estrutura do Cap. 1 (§8) e o pitch do §11 como narrativa-base.

---

## 3. Itens — detalhe e registro de decisão

### Gate (imediato)

#### A01 — Corrigir nome do arquivo-fonte no cabeçalho do plano
**Origem:** análise crítica §2.6 · **P3** · **imediato** · **Afeta:** cabeçalho de `TCC_minimal_v5.md`
O cabeçalho citava `planejamento_tcc_harness_arquitetura_v5.md`, mas o arquivo real da versão v5 no repositório é `Full-Research_v5.md`.
**Decisão:** ✔ **Fechado em 26/09/2026** — cabeçalho do plano corrigido para `Full-Research_v5.md`.

#### A02 — Trazer `consolidated_references.md` para o repositório
**Origem:** análise crítica §2.6 · **P1** · **imediato** · **Afeta:** rastreabilidade de todo o §7 do plano
O plano afirma que as 21 referências foram verificadas contra CrossRef (09–10/09/2026), mas o arquivo-fonte não está no repositório: a verificação não é reproduzível a partir dele, e a introdução citará R21, R10, R11, R2 e R3.
**Ação:** copiar o arquivo para `context/planing/` (ou registrar nele onde vive e por quê).
**Definition of done:** o caminho citado no §7 do plano resolve dentro do repositório.
**Revisão 01/10/2026 — quase concluído:** o arquivo já está no repositório como `references/references-consolidadas.md` (*untracked*, ainda não commitado; o frontmatter mantém `name: referencias_tcc_consolidado`). Falta: (a) reconciliar nome/local — o §7 do plano cita `consolidated_references.md`, este item e o README apontam para `context/planing/`; ou renomear/mover o arquivo, ou atualizar §7 + README para o caminho real; (b) commitar; (c) remover a linha "Pendente" do README. Ao fechar, registrar duas ressalvas do próprio arquivo: as seções citadas em "Onde usar" não correspondem às do v5-Minimal (o arquivo aponta ameaças à validade para §6.3 e base reaproveitada para §6.4, que no plano são §6.4 e §6.5; e trata B3/B4 como §6.2, embora o plano os tenha tirado do escopo em §5.2); e as pendências internas dele estão absorvidas aqui (1 → A06, 2 → A25, 6 → A24, 8 → A28) ou dizem respeito a referências em reserva (3: venue de R20; 5: data de R18 — resolver só se R18/R20 entrarem no ADR de logging).
**Revisão 01/10/2026 — reorganização de pastas:** `context/` virou `planning/` e o arquivo foi movido para `planning/consolidated_references.md` — nome agora igual ao citado no §7 do plano e ao frontmatter; README atualizado e linha "Pendente" removida. Itens (a) e (c) resolvidos; falta só (b) commitar e registrar as duas ressalvas acima ao fechar. Os metadados passam a alimentar `thesis/references.bib` (R1 já transcrita).
**Decisão:** —

#### A03 — Confirmar orientador e endossar o recorte B1+B2
**Origem:** análise crítica §2.6 + §12 do plano · **P1** · **mês 1** · **Afeta:** o projeto inteiro (é o gate real)
O `5w2h.md` já nomeia Sidarta Carvalho como orientador, mas o plano (§12) ainda lista "confirmar orientador" como passo aberto — os documentos divergem sobre o estado real. Além de formalizar, é a sessão em que o recorte de duas dimensões (§5.2) precisa ser endossado: a introdução não deve ser redigida sobre um recorte que ainda pode mudar.
**Definition of done:** orientador confirmado; posição sobre o recorte registrada abaixo.
**Decisão:** —

### Mês 1 — decisões de escopo

#### A04 — Escolher os dois provedores do B1
**Origem:** §12 do plano (passo 2) + análise crítica §2.1 · **P2** · **mês 1** · **Afeta:** §6.2; orçamento de API
Escolha já prevista no plano; regra adicional da análise: APIs razoavelmente distintas (teste exigente) e o mock determinístico apenas como fallback **declarado** — se virar condição principal, registrar na validade de construto que a métrica comportamental perde força (mock é determinístico e "fácil demais").
**Revisão 01/10/2026:** (1) o plano se contradiz — §6.2 trata o mock como recurso "se o orçamento for limitante", mas §9.3 (riscos) diz "provedor mock determinístico como **condição principal**"; ao fechar, corrigir o §9.3 para ficar coerente com a regra deste item. (2) Sequência: a escolha (mês 1) depende do orçamento máximo de API, que o plano só fixa no mês 3 (§12, passo 4) — fazer ao menos uma estimativa de custo agora. (3) Considerar A12/A29 na escolha: se um dos dois provedores for o próprio modelo local do B2, A12 se resolve sozinho (dois adaptadores em vez de três).
**Decisão:** —

#### A05 — Reinstalar "permite simular falhas" nos critérios de escolha da aplicação
**Origem:** análise crítica §2.4 · **P2** · **mês 1** · **Afeta:** §5.1 do plano
A v5 completa exigia que a aplicação "permitisse simular falhas"; o v5-Minimal derrubou o critério ao cortar o B3 — mas o plano B do gate (mês 8) depende de injeção de falhas. Sem o critério, a aplicação escolhida no mês 1 pode inviabilizar o plano B silenciosamente.
**Definition of done:** critério de volta ao §5.1 **antes** da escolha da aplicação.
**Decisão:** ✔ **Fechado em 26/09/2026** — critério reinstalado no §5.1 do plano como "permita simular/injetar falhas (ex.: timeout, erro de conexão, rate limit, resposta inválida)", com a justificativa explícita de condição de viabilidade do plano B (§9.2) no próprio texto do plano.

#### A06 — Confirmar autoria de R7 (SEMISH) e padronizar a citação
**Origem:** §12.2 do plano · **P3** · **mês 1–2** · **Afeta:** §6.5; toda citação de R7
Registro CrossRef: *Barros; da Silva, V. M. A.; dos Santos; Viana; Gomes de B. Filho*. Confirmar que "da Silva, V. M. A." é o registro correto do autor e padronizar antes da primeira citação em texto corrido.
**Revisão 01/10/2026 — evidência reunida:** o `5w2h.md` identifica o aluno como "Vitor Manoel **Alves** da Silva", o que bate com "Vitor Manoel A. da Silva" (2º autor no CrossRef). Falta só a confirmação do próprio autor e a escolha da forma na lista de referências: o arquivo consolidado sugere "DA SILVA, V. M. A.", mas na regra usual da ABNT (NBR 6023) partículas como "da" não entram no sobrenome de entrada ("SILVA, V. M. A. da") — confirmar qual norma o curso adota. A citação em texto ("Barros et al., 2026") não muda.
**Decisão:** —

### Mês 3 — congelamento do protocolo (B1)

#### A07 — Definir política de implementação da versão D
**Origem:** análise crítica §2.1 · **P1** · **mês 3** · **Afeta:** §6.2 e §6.4; futuro ADR
O resultado do B1 é parcialmente verdade por construção (o harness existe para facilitar a troca). Sem política declarada, a comparação vira *strawman* (D dispersa chamadas de SDK) ou se dilui (D centraliza o acesso ao SDK por conta própria). Política sugerida: **D segue a documentação oficial/quickstart do provedor — sem dispersão artificial e sem camada de abstração própria** — declarada no protocolo e repetida nas ameaças à validade.
**Definition of done:** política redigida no protocolo do B1 e citada em §6.4.
**Revisão 01/10/2026:** a política também precisa fixar e declarar o **número de pontos de integração** (call sites de LLM no código de negócio) que a aplicação tem. Com um único caso de uso e um único call site, D segue o quickstart e a troca toca um arquivo, tanto quanto o adaptador de H: o B1 sai pouco informativo. O tamanho da diferença H × D cresce com o número de pontos de integração, então esse número é parâmetro do experimento e entra nas ameaças à validade (externa).
**Decisão:** —

#### A08 — Pré-registrar o checklist da troca de provedor
**Origem:** análise crítica §2.1 · **P2** · **mês 3** (procedimento; execução no mês 7) · **Afeta:** §6.2
O autor implementa H e D conhecendo a hipótese; definir o que conta como "troca completa" depois de executá-la abre espaço para racionalização pós-hoc. Registrar no repositório, **antes** da execução, o checklist objetivo da troca (o que deve continuar funcionando; o que é permitido tocar).
**Definition of done:** checklist commitado antes da execução da troca, com o hash do commit anotado aqui. O histórico do git é a prova datada do pré-registro.
**Decisão:** —

#### A09 — Decompor a métrica de alteração de código
**Origem:** análise crítica §2.1 · **P2** · **mês 3** · **Afeta:** §6.2 (tabela de métricas)
"Arquivos/linhas alterados" mistura naturezas: em H a troca gera **código novo** (adaptador); em D, **modificação** de código existente. Sugerido: primária = LOC modificados/removidos de código existente; secundária = LOC adicionados (adaptador).
**Decisão:** —

#### A10 — Definir fallback para a métrica de tempo
**Origem:** análise crítica §2.1 · **P3** · **mês 3** · **Afeta:** §6.2 (métrica secundária)
O plano diz "cronometrado por um colega, **se possível**" — sem fallback. Definir protocolo de auto-cronometragem (sessão dedicada, registro de início/fim, sem interrupções) caso o terceiro não se confirme.
**Decisão:** —

### Mês 3 — congelamento do protocolo (B2)

#### A11 — Decidir medição de energia de CPU (RAPL) ou limitação declarada
**Origem:** análise crítica §2.2 · **P1** · **mês 3** · **Afeta:** §6.3 (protocolo de telemetria)
NVML mede GPU; o custo **direto** do harness é trabalho de CPU (normalização, serialização, orquestração). Parte aparece indiretamente como duração maior, mas a energia da CPU do host não é medida — e o sinal de interesse (overhead H−D) vive na ordem de grandeza do termo não medido. Opções: (a) RAPL/`powercap` como métrica secundária/diagnóstica; (b) limitação declarada, com o argumento de dominância do termo de GPU.
**Revisão 01/10/2026 — verificar viabilidade antes de decidir:** a opção (a) depende do servidor institucional. Em kernels Linux atuais, `/sys/class/powercap/intel-rapl*/energy_uj` costuma ser legível só por root (restrição adotada após a vulnerabilidade PLATYPUS, 2020), e em CPUs AMD o suporte depende do kernel. Perguntar ao administrador do servidor se há acesso, ou se ele pode liberar a leitura, antes do mês 3. Sem acesso, resta a opção (b).
**Decisão:** —

#### A12 — Definir escopo da interface: modelo local é 2º ou 3º adaptador?
**Origem:** análise crítica §2.2 · **P2** · **mês 3** · **Afeta:** §5.1 (MVP); cronograma do mês 4
O MVP prevê "interface abstrata para dois provedores/adaptadores" (B1), mas o B2 exige que H converse com o **modelo local** — um terceiro ponto de integração, salvo se um dos provedores do B1 for o próprio modelo local. Decidir antes do contrato da interface para dimensionar o mês 4. A escolha do modelo em si permanece no piloto (§12.3 do plano).
**Revisão 01/10/2026:** depende de A04 (se um provedor do B1 for o modelo local, o problema some) e da **stack de serving** do modelo local (A29). Se o servidor expuser API compatível com OpenAI (ex.: vLLM, Ollama), o adaptador local pode reaproveitar o de um provedor do B1, e muda o que "D direta" significa no B2 (D falaria com o servidor de inferência pelo mesmo SDK). Fechar junto com A29.
**Decisão:** —

#### A13 — Definir determinismo operacional + gate de contagem de tool calls
**Origem:** análise crítica §2.2 · **P1** · **mês 3** · **Afeta:** §5.1 e §6.3
O §5.1 exige "repetições determinísticas" sem definir como. Sugerido: temperature 0, seed fixa, prompts e tool schemas idênticos entre H e D. No nível 2, o **número** de chamadas de ferramenta depende do modelo: registrar a contagem por requisição e usá-la como gate/diagnóstico — loops de comprimentos diferentes fazem J/req misturar overhead por passo com comprimento do loop.
**Revisão 01/10/2026:** temperature 0 + seed **não garantem** saídas idênticas em GPU (*batching* e kernels não determinísticos fazem a saída variar entre execuções). Definir "determinismo operacional" como *parâmetros fixados e idênticos entre H e D + variação residual medida no piloto*, não como saída bit a bit igual. A consequência vai direto para A19: a paridade não pode exigir texto de saída idêntico.
**Decisão:** —

#### A14 — Pré-especificar unidade amostral por lote (M requisições)
**Origem:** análise crítica §2.2 · **P2** · **mês 3** (design); M calibrado no **mês 6** · **Afeta:** §6.3
Se o overhead do nível 1 for menor que a banda de ruído do NVML (efeito piso), a requisição isolada não resolve o sinal. Pré-especificar no protocolo a alternativa: unidade amostral = **lote de M requisições sequenciais**, com M calibrado no piloto (junto com A22).
**Decisão:** —

### Mês 3 — congelamento do protocolo (estatística)

#### A15 — Fechar o pacote estatístico definitivo
**Origem:** §12.1 do plano + análise crítica §2.3 · **P1** · **mês 3** · **Afeta:** §6.3 (protocolo estatístico)
Fecha a pendência §12.1: Mann-Whitney U compara distribuições (superioridade estocástica), não percentis. Sugerido: testes formais sobre as **amostras brutas** (J/req, J/token, potência média); p50/p95/p99 como **descritivos** com IC bootstrap; regressão quantílica apenas se um teste formal de cauda for indispensável.
**Decisão:** —

#### A16 — Definir família de testes vs. métricas descritivas
**Origem:** análise crítica §2.3 · **P1** · **mês 3** · **Afeta:** §6.3 (correção de multiplicidade)
"2 comparações × 4 métricas = 8 testes" é ambíguo: p50/p95/p99 são uma família ou três testes? "potência média/pico" é uma métrica ou duas? A carga do Holm-Bonferroni muda conforme a resposta (8 vs. 14 testes). Pré-especificar quais quantidades recebem teste de hipótese e quais ficam descritivas.
**Decisão:** —

#### A17 — Formalizar "comparável" como margem de não-inferioridade
**Origem:** análise crítica §2.3 · **P1** · **mês 3** · **Afeta:** §6.3 (critério de aceitação)
O critério de aceitação contém "Ē_harness < Ē_direto, **ou comparável**" — "comparável" sem definição operacional não sobrevive a um protocolo congelado. Definir a margem (ex.: ±5% de J/req) e tratar formalmente como teste de não-inferioridade.
**Revisão 01/10/2026 — problema maior que o termo vago, eleva a prioridade interna do item:** a fórmula atual é **logicamente inconsistente** no ramo "comparável". Ela exige, na mesma conjunção, "comparável" **e** p < 0,05 **e** |δ| acima do limiar. Se H for de fato comparável a D, o δ será pequeno e o critério falha por construção. Além disso, a hipótese do próprio plano (§2) é que a camada *cobra* custo energético, então "Ē_H < Ē_D" é o ramo improvável. O critério herdado de R7 (comparação entre duas estratégias rivais) não se encaixa bem aqui. Reescrever em dois ramos: **(i) não-inferioridade** — o limite superior do IC (bootstrap ou Hodges-Lehmann) da diferença relativa H−D fica abaixo de Δ; **(ii) superioridade/custo relevante** — p < 0,05 ∧ |δ| ≥ limiar (A18). Reportar sempre a estimativa do overhead com IC, porque o problema de pesquisa pergunta "*qual* é o custo", e isso se responde com uma estimativa, não com um aceita/rejeita. Fechar junto com A18 e A21.
**Decisão:** —

#### A18 — Fixar o limiar de Cliff's delta
**Origem:** análise crítica §2.3 · **P1** · **mês 3** · **Afeta:** §6.3
O critério exige "|δ| acima do **limiar adotado**" sem adotar limiar algum. A análise crítica sugeriu "|δ| ≥ 0,33 (efeito pequeno; Romano et al.)", rótulo corrigido abaixo. Fixar **antes** da coleta para não abrir espaço a escolha conveniente pós-hoc.
**Revisão 01/10/2026:** na escala de Romano et al. (2006), |δ| < 0,147 é "desprezível", 0,147–0,33 é "pequeno", 0,33–0,474 é "médio" e ≥ 0,474 é "grande". Então |δ| ≥ 0,33 corresponde a efeito **médio**, não pequeno: escolher o corte sabendo disso (0,147 se a ideia for "não desprezível"). Pela reescrita de A17, o limiar vale só no ramo de superioridade/custo relevante, não no de não-inferioridade.
**Decisão:** —

### Mês 3–4 — validade e plano B

#### A19 — Definir critério operacional de paridade funcional H/D
**Origem:** análise crítica §2.5 · **P1** · **mês 3–4** · **Afeta:** §6.1; especificação da suíte (próximo passo 5 do plano)
A suíte de paridade é o pino de validade dos dois benchmarks, mas "verde" não está definido: mesmas entradas → mesmas saídas? Sequência de tool calls idêntica? Tolerância para campos normalizados? Definir **antes** de escrever a suíte e antes da versão D (mês 5).
**Revisão 01/10/2026:** por A13, "mesmas saídas" não é exigível literalmente: a saída do LLM varia entre execuções mesmo com parâmetros fixos. Candidato: asserções funcionais (resultado de negócio correto, *schema* de resposta válido, mesmas ferramentas chamadas com argumentos equivalentes), aplicadas igualmente a H e D, com a taxa de sucesso A como métrica, a mesma do gating do B2.
**Decisão:** —

#### A20 — Redigir memo de pivô (moldura B1+B3)
**Origem:** análise crítica §2.4 · **P2** · **mês 3** · **Afeta:** §9.2; §1/§3/§4 em contingência
O gate do mês 8 pode ativar B3 no lugar de B2 — e aí título, problema e objetivos (construídos sobre desacoplamento × energia) exigem reescrita, com o TCC I já entregue. Custo baixo se feito cedo: **uma página** com a reformulação de título/problema/objetivos do cenário B1+B3, redigida junto ao protocolo do B3 (próximo passo 3 do plano).
**Decisão:** —

### Mês 6 — piloto e gate

#### A21 — Definir efeito mínimo de interesse prático; n por simulação
**Origem:** análise crítica §2.3 · **P2** · definição no **mês 3**, cálculo no **mês 6** · **Afeta:** §6.3 (orçamento de janelas)
O piloto deve produzir "n necessário por célula para o **tamanho de efeito esperado**" — mas o efeito esperado não tem fonte declarada. Mais robusto: definir o **efeito mínimo de interesse prático** (ex.: ≥3% em J/req) e calcular n por simulação/bootstrap sobre a variância do piloto.
**Revisão 01/10/2026:** os exemplos deste item e de A17 se contradizem: com margem de não-inferioridade de 5% (A17) e efeito mínimo de interesse de 3% (aqui), um overhead de 4% seria ao mesmo tempo "comparável" e "de interesse prático". Usar **um único Δ** para as duas funções, definido no mês 3 junto com A17.
**Decisão:** —

#### A22 — Incluir teste de sensibilidade (efeito piso) no piloto
**Origem:** análise crítica §2.2 · **P2** · **mês 6** · **Afeta:** §6.3; protocolo do piloto
Além de tempo/requisição e estabilização térmica, o piloto deve medir se o NVML a 100 ms consegue **resolver** a diferença H vs. D no nível 1 (banda de ruído vs. overhead esperado). O resultado alimenta A14 (lote M) e o orçamento de horas de GPU do gate.
**Decisão:** —

#### A23 — Reformular o gate do mês 8 para taxa projetada
**Origem:** análise crítica §2.4 · **P2** · **mês 6** (antes do gate) · **Afeta:** §9.2
"Horas obtidas ≥ 50% do orçamento" compara um **acumulado** com uma necessidade que se estende ao mês 10 — 50% obtidos até o mês 8 não garantem os 50% restantes. Gate mais robusto: **taxa de acesso** (horas/semana obtidas nos meses 6–8) projetada até o fim do mês 10 contra a necessidade remanescente da matriz.
**Decisão:** —

### Redação e fundamentação

#### A24 — Buscar base acadêmica formal para ADRs, C4 e ISO/IEC 25010
**Origem:** §12.5 do plano · **P3** · **antes do Cap. 2** · **Afeta:** Cap. 2; §6.1
Hoje ancorados apenas na prática. Não bloqueia protocolo nem introdução; fechar antes da fundamentação teórica. O arquivo de referências (§6, pendência 6) já traz um *prompt* de busca pronto para isso.
**Decisão:** —

#### A25 — Escolher artigo específico do AGENT 2026, se citado nominalmente
**Origem:** §12.4 do plano · **P3** · **antes do Cap. 3** · **Afeta:** trabalhos relacionados
Só relevante se o texto citar o volume (DOI 10.1145/3786167) nominalmente; verificar a precisão de qualquer alegação sobre o escopo temático do workshop.
**Revisão 01/10/2026 — candidato a fechar como "não aplicável":** o plano **não** cita AGENT 2026 em nenhuma seção do corpo (§2.1, §7 e §8 não o mencionam); a única ocorrência é a própria pendência do §12.4. Sugestão: fechar com o gatilho "reabrir se o Cap. 3 citar o AGENT 2026".
**Decisão:** —

#### A26 — Nota de redação: capítulos sem meta-comentário
**Origem:** análise crítica §4 · **P3** · **aplica-se a cada capítulo** (meses 11–12 em particular)
Os documentos de planejamento são densos e autorreferentes (pendências, avisos, § cruzados) — adequado para um plano, errado para texto acadêmico. Ao redigir cada capítulo, traduzir para prosa e **resolver** as pendências em vez de carregá-las.
**Decisão:** —

### Itens adicionados na revisão de 01/10/2026

#### A27 — Ancorar o "mês 1" do cronograma a uma data de calendário
**Origem:** revisão do registro (01/10/2026) · **P2** · **imediato** · **Afeta:** §9.1 do plano; todos os prazos deste registro
O cronograma (§9.1) e todos os prazos daqui são relativos ("mês 3", "mês 8"), mas o plano não diz qual mês do calendário é o mês 1. Sem essa âncora não dá para saber se A03, A04 e A06 (prazo: mês 1) estão em dia ou atrasados. O próprio plano já depende de datas absolutas: os venues-alvo do §11 são do CBSoft 2027, com prazos de submissão fixos, e só dá para saber se os resultados ficam prontos a tempo com o cronograma ancorado. Fixar a data de início e conferir que o **TCC I (mês 6)** e a defesa (mês 12) batem com o calendário acadêmico do curso.
**Definition of done:** data do mês 1 registrada no §9.1 do plano e no cabeçalho deste registro; prazos do mês 1 reavaliados.
**Decisão:** —

#### A28 — Mapear as responsabilidades do harness contra os padrões de R21
**Origem:** §2 e §10 do plano (revisão de 01/10/2026) · **P2** · **mês 1–2** (revisão bibliográfica) · **Afeta:** §2 e §10 do plano; Cap. 2
O plano afirma no presente que "as responsabilidades acima **são mapeadas** contra o catálogo de padrões de Liu et al. (R21)" (§2), e a contribuição 1 (§10) depende disso. Mas o mapeamento não aparece em nenhuma seção do plano: a tabela do §2 lista as responsabilidades sem indicar padrão algum. A fonte bibliográfica declarada no §7 confirma que ele **não foi feito** (pendência 8 do arquivo). É a principal defesa contra a crítica de que a definição de harness é *ad hoc*. Ação: abrir R21 e montar a tabela "responsabilidade do §2 → padrão(ões) do catálogo", incluindo os padrões de registro de execução que sustentam o ADR de logging.
**Definition of done:** tabela de mapeamento no repositório, citada no §2 do plano.
**Decisão:** —

#### A29 — Escolher o modelo local e a stack de serving do B2
**Origem:** §12.3 do plano (pendência sem item próprio até esta revisão) · **P2** · **stack no mês 3; modelo no mês 6** · **Afeta:** §6.1 (congelamento), §6.3; A12
O registro foi semeado a partir das pendências do §12, mas a pendência 3 (modelo local) não tinha item, só uma menção dentro do A12. O plano adia a escolha do **modelo** para o piloto, e isso se mantém. A **stack de serving** (vLLM, Ollama, TGI…; API própria ou compatível com OpenAI) precisa ser conhecida antes, porque define o adaptador local (A12), o que "D direta" significa no B2 e o que entra no congelamento de versões (§6.1). Levantar com a administração do servidor o que já está hospedado e estável.
**Definition of done:** stack registrada antes do contrato da interface (mês 3); modelo e versão congelados ao fim do piloto (mês 6).
**Decisão:** —

---

*Criado em 26/09/2026 a partir da análise crítica de `TCC_minimal_v5.md`. **Revisado em 01/10/2026:** todos os itens (A01–A26) conferidos contra o `TCC_minimal_v5.md`, base da análise; o `5w2h.md` e o arquivo de referências do §7 entram só como evidência auxiliar (A02, A06, A28). Notas "Revisão 01/10/2026" acrescentadas em A02, A04, A06, A07, A08, A11, A12, A13, A17, A18, A19, A21, A24 e A25; A02 e A06 passaram a `em análise`; prazo de A06 corrigido no painel para mês 1–2; itens novos A27–A29. Próxima revisão do painel: ao fechar o gate (A02, A03).*