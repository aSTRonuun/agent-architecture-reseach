# Mapeamento: responsabilidades do harness × padrões de Liu et al. (2025)

**Item do action log:** A28 · **Status:** rascunho para decisão do autor (nada aplicado em outros arquivos)
**Fonte lida:** texto completo, seções 1 a 6 (`context/full-papers/1-s2.0-S0164121224003224-main.txt`). Liu et al., *Journal of Systems and Software*, v. 220, art. 112278, 2025 (recebido 30/07/2024, aceito 06/11/2024, online 15/11/2024).
**Responsabilidades mapeadas:** as cinco do plano §2 (`context/planning/TCC_minimal_v5.md`).

---

## 1. O que o artigo é

- Catálogo de **18 padrões** (seções 4.1 a 4.18), cada um no formato Summary, Context, Problem, Forces, Solution, Consequences (Benefits/Drawbacks), Known uses, Related patterns.
- **Escopo:** agentes baseados em modelos de fundação que fazem *goal-seeking* e geração de plano. "Agent" é a IA que assume papel ativo para atingir objetivos do usuário (seção 1). O foco é o projeto interno do agente, não a camada de integração entre uma aplicação e o provedor do modelo.
- **Método (seção 3):** revisão sistemática de 57 estudos (Lu et al., 2023b), mais uma revisão adicional com literatura cinzenta e páginas oficiais, usada **para os usos conhecidos** de cada padrão.
- **Não é avaliação empírica.** Os trade-offs são listados de forma qualitativa.

Padrões: 4.1 Passive goal creator · 4.2 Proactive goal creator · 4.3 Prompt/response optimiser · 4.4 RAG · 4.5 One-shot model querying · 4.6 Incremental model querying · 4.7 Single-path plan generator · 4.8 Multi-path plan generator · 4.9 Self-reflection · 4.10 Cross-reflection · 4.11 Human reflection · 4.12 Voting-based cooperation · 4.13 Role-based cooperation · 4.14 Debate-based cooperation · 4.15 Multimodal guardrails · 4.16 Tool/agent registry · 4.17 Agent adapter · 4.18 Agent evaluator.

Termos que **não aparecem** no artigo: *harness*, *middleware*, *energy*, *carbon*, portabilidade. *Vendor lock-in* aparece uma vez (4.16, como risco do próprio registro).

---

## 2. Tabela de mapeamento

Grau: **Parcial** (o padrão cobre parte da função) · **Analogia** (função parecida, objeto diferente) · **Nenhum**. O grau é julgamento meu, para você aprovar ou mudar.

| # | Responsabilidade (plano §2) | Padrões do catálogo | Grau | O que o artigo diz | Ressalva |
|---|---|---|---|---|---|
| 1 | Abstração e padronização da comunicação com provedores (medida no B1) | Agent adapter (4.17); Prompt/response optimiser (4.3); Multimodal guardrails (4.15), só pela posição | **Analogia** | O adapter converte "agent messages into required format or content, and vice versa" para ferramentas externas. O optimiser padroniza prompts e respostas (forças: *Standardisation*, *Interoperability*). Os guardrails ficam como "intermediate layer between the foundation model and all other components". | **Nenhum padrão trata de trocar o provedor do modelo.** Adapter e registry tratam de ferramentas; o optimiser, de *templates* de prompt. Esta é a responsabilidade que o B1 mede. |
| 2 | Orquestração de chamadas e execução de ferramentas (nível 2 do B2) | Agent adapter (4.17); Tool/agent registry (4.16); One-shot (4.5) e Incremental model querying (4.6) | **Parcial** (adapter); **analogia** (querying) | O adapter "invokes and manages" as interfaces das ferramentas e devolve os resultados ao modelo. One-shot consulta o modelo uma vez; incremental, várias vezes. | One-shot e incremental descrevem a **geração de plano**, não o ciclo de ferramentas; ligá-los aos níveis 1 e 2 do B2 é analogia do autor. O MVP tem 2 a 3 ferramentas fixas, então o registry (seleção entre muitas) pouco se aplica. O registry lista como desvantagem: "may become a vendor lock-in solution and cause single point of failure". |
| 3 | Gerenciamento de contexto e estado da interação | Passive goal creator (4.1); Incremental model querying (4.6); RAG (4.4) | **Parcial / analogia** | O goal creator recupera da memória (histórico de conversa, artefatos, ferramentas recentes) e anexa ao prompt. O incremental divide o contexto em vários prompts por causa da janela. O RAG enriquece com base externa. | **Não há padrão de gestão de estado da interação.** "Memory" aparece como componente na Fig. 2, não como padrão. RAG é enriquecimento de conhecimento, não estado. |
| 4 | Tratamento e recuperação de falhas | — | **Nenhum** | "Fault tolerance" aparece só como benefício de Role-based cooperation (substituir agentes inativos). A seção 5.3 cita como trabalho em andamento "real-time exception identification and handling". | Retry e *circuit breaker* não estão no catálogo. A base disponível é R15 a R17 (reserva), fora de IA. |
| 5 | Registro estruturado de eventos e auditoria | — | **Nenhum** (nos 18) | Registro e auditoria aparecem como forças ou benefícios de padrões multiagente (4.10, 4.11, 4.12, 4.14), não como padrão. A seção 5.3 cita os padrões *black box* e *bill of materials registry* de Lu et al. (2023a), que o artigo referencia mas que ficam **fora dos 18**. | Candidato a verificar: Lu et al. (2023a), livro da Addison-Wesley. **Não li.** |

**Resumo:** das cinco responsabilidades, uma tem correspondência parcial direta (2), duas têm correspondência parcial ou por analogia (1 e 3) e duas não têm correspondência no catálogo (4 e 5).

---

## 3. Padrões do catálogo que não são responsabilidade do harness

| Padrões | Motivo |
|---|---|
| 4.2 Proactive goal creator | Captura contexto multimodal do ambiente do usuário. |
| 4.7 e 4.8 Plan generators | Quem planeja é o modelo; o harness não gera plano. |
| 4.9 a 4.11 Reflection | Revisão de plano por modelo, outro agente ou humano. |
| 4.12 a 4.14 Cooperation | Multiagente, fora do escopo (plano §5.2). |
| 4.15 Multimodal guardrails | Fora do escopo (plano §5.2). Só a posição estrutural se parece com a do harness. |
| 4.18 Agent evaluator | Avaliação do agente. Tem semelhança com a suíte de paridade e o *gating* de corretude, mas não é responsabilidade da camada. |

---

## 4. O que o artigo sustenta sobre a lacuna

- Cada padrão traz benefícios e desvantagens **sem medição**. **14 dos 18** padrões listam "Overhead" ou "Maintenance overhead" entre as desvantagens (4.2, 4.3, 4.4, 4.6, 4.8 a 4.14, 4.16, 4.17); nenhum o quantifica. O overhead descrito é de custo, tempo, comunicação, complexidade e manutenção.
- **Energia:** as palavras *energy* e *carbon* não aparecem no artigo.
- **Apoio textual direto (seção 5.3):** "The majority of pattern benefits and drawbacks are software quality attributes, which still require quantification for fine-grained metrics and rubrics." E: "Proper quantification can promote the evaluation of agents and validate the effectiveness of applied patterns."
- Cuidado: a seção 5.3 pede quantificação dos atributos de qualidade em geral. Não aponta energia nem substituibilidade de provedor como lacuna.

---

## 5. Divergências entre o artigo e as notas do projeto

1. **`consolidated_references.md` (entrada R21)** diz que o catálogo é "organizado por categoria de responsabilidade — … e mecanismos transversais como guardrails e registro de execução", e sugere verificar se algum padrão ancora o checklist do B4. O texto não traz essa organização por categoria e **não tem padrão de registro de execução**. Guardrails existem (4.15). A ancoragem do B4 ou do ADR de logging em R21 não se sustenta nos 18 padrões.
2. **Literatura cinzenta:** o artigo a usa para identificar os *known uses* (seção 3), não para derivar os padrões. O "precedente" citado no plano §2.1 e no §6.1 vale, mas com esse alcance.
3. **Plano §2 e §10:** "as responsabilidades acima são mapeadas contra o catálogo" e a contribuição 1 não se sustentam para as responsabilidades 1, 4 e 5, e só em parte para a 3.
4. **Introdução ([1-introducao.tex](../../2-textuais/1-introducao.tex)):** o parágrafo "Essas responsabilidades dialogam com o catálogo… que serve de referência para o projeto da camada" e o objetivo específico (a) ("com base em padrões arquiteturais publicados") foram escritos antes deste mapeamento.
5. **Known uses (T20):** os usos conhecidos são ferramentas e *frameworks* citados por documentação oficial (LangChain, Semantic Kernel, AutoGen, Amazon Bedrock). Servem como "Liu et al. listam X como uso conhecido", nunca como evidência de que o *framework* entrega o padrão.

---

## 6. Limites desta leitura

- O arquivo é texto extraído de PDF. **Não vi as figuras** (Fig. 1 metodologia, Fig. 2 ecossistema anotado, Fig. 19 modelo de decisão). O que digo sobre elas vem do texto das seções 4 e 5.1.
- A Tabela 1 saiu embaralhada na extração; conferi cada padrão contra o texto das seções 4.1 a 4.18.
- Lu et al. (2023a), Lu et al. (2023b) e Xia et al. (2023) são citados pelo artigo e **não foram lidos**.

---

## 7. Decisões que dependem do autor

**D5a. Como tratar o resultado do mapeamento.**
(i) Manter Liu como referência **parcial** e declarar as lacunas, completando cada uma com outra fonte e a ressalva dela: responsabilidade 1 com Issarny (*middleware*), 4 com R15 a R17 (reserva), 5 com Lu et al. (2023a) ou OpenTelemetry (documento técnico).
(ii) Reformular a contribuição 1 do plano para "mapeada parcialmente contra padrões publicados, com lacunas identificadas".
(iii) Outra abordagem.

**D5b. Texto da Introdução.** O parágrafo do liu2025 e o objetivo (a) precisam de ajuste conforme a D5a? Proposta de redação só depois da sua decisão.

**D5c. Notas do projeto a corrigir:** entrada R21 de `consolidated_references.md`, plano §2, §2.1, §6.1 e §10, e o item A28 do action log (o que fecha o item).

**D5d. Apresentação na Fundamentação.** O mapeamento entra no Cap. 2 como Quadro "responsabilidade × padrão" (com a coluna "Grau")? Ou só como texto?
