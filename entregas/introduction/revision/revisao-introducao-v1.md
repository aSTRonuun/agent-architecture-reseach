# Avaliação do projeto de TCC I — 1ª revisão (somente Introdução)

**Avaliador:** — | **Projeto avaliado:** *Projeto e avaliação experimental de uma camada arquitetural desacoplada agêntica (harness) para integração de modelos de IA em aplicações web: custo de substituição de provedor e custo energético* (Vitor Manoel Alves da Silva; orientador: Prof. Dr. Sidarta Carvalho)
**Arquivo avaliado:** `entregas/TCC1-Introducao-Vitor-Manoel-Alves-da-Silva.md` (conversão do PDF homônimo; o PDF não pôde ser renderizado nesta sessão)
**Tipo de pesquisa:** implementação com experimento controlado (duas versões de uma aplicação web, medição de código e de energia). Não há pesquisa de campo com pessoas; o critério 5.4 não se aplica.

## Nota estimada

| Escopo | Pontos |
|---|---|
| Partes entregues (Título/Introdução, Objetivos, Formatação) | **2,90 / 3,5** |
| Defesa (atribuída por instrução da rubrica, não avaliada) | 1,0 |
| Não entregues nesta etapa (Trabalhos Relacionados 1,0 + Fundamentação 2,0 + Metodologia 2,5) | 0,0 / 5,5 — **não avaliados** |
| Leitura literal da rubrica completa (2,90 + 1,0 + 0) | 3,90 / 10 — *não representativo* |

A nota que vale como retrato desta entrega é **2,90 / 3,5 (≈ 83%)**. A leitura literal em 10 pontos só mostra que 55% da rubrica ainda não existe no texto.

**Parecer (coerência interna):** não determinável nesta etapa, porque faltam referencial e metodologia. No recorte entregue, problema e objetivo geral são coerentes; há quatro pontos de atenção (seção "Coerência interna").
**Maiores perdas:** formatação (−0,25), Objetivo específico (−0,15), problema (−0,10) e justificativa (−0,10).

---

## 1. Título/Introdução (1,30 / 1,5)

| Critério | Observações do avaliador |
|---|---|
| 1.1 Título (0,375) | **Atende** (0). Evidência: "Projeto e avaliação experimental" (ação) + "camada arquitetural… (harness)" (objeto) + "aplicações web", "custo de substituição de provedor e custo energético" (campo e variáveis). Ressalvas sem perda: são ~30 palavras; e "agêntica" entra em conflito com a taxonomia que o próprio texto adota, pois Sapkota et al. (2026) reservam "IA agêntica" a sistemas multiagentes (1.1), enquanto o trabalho trata de agentes com ciclo de ferramentas. Sugestão: "…camada de integração (harness) para modelos de IA em aplicações web: custo de substituição de provedor e custo energético". |
| 1.2 Problema (0,375) | **Parcial** (−0,10, ≈27%). Evidência: a lacuna é explícita em 1.2 ("ausência de medição controlada") e a pergunta de pesquisa está formulada; as afirmações centrais têm fonte. Motivos: (i) a definição de harness, termo central, abre com "Na prática recente, o termo harness passou a designar…" **sem citação** (1.1); (ii) "custo de substituição" nunca é definido operacionalmente na Introdução (só o Resumo cita "métricas comportamentais e estruturais do código"); (iii) "não foram encontrados estudos" não indica onde nem como se buscou. Correção: citar a origem do termo, definir "custo de substituição" em uma frase e indicar a base de busca. |
| 1.3 Público-alvo (0,375) | **Atende** (0). Evidência: 1.3 nomeia "desenvolvedores e arquitetos que integram LLMs a aplicações web", ligado à decisão arquitetural da justificativa. Ressalva: o público aparece só ali; vale nomeá-lo já em 1.2. |
| 1.4 Justificativa/impacto (0,375) | **Parcial** (−0,10, ≈27%). Evidência: as justificativas prática e científica estão estruturadas e o recorte ("não serão avaliados" recuperação de falhas e auditabilidade) está explícito. Motivos: (i) "o custo de trocar de provedor deixa de ser hipotético" (1.3) é mais forte do que a evidência — o texto mesmo admite em 1.1 que a taxa de troca de 11% "não isola a causa"; (ii) a relevância energética se apoia em dado global (IEA, 945 TWh) e em Vellaisamy et al. (2026), que decompõem o overhead de host **dentro da pilha de inferência** (confirmado na busca), não de uma camada de aplicação; o salto até "a camada pode ter custo mensurável" é analogia, não demonstração. Correção: dizer que a relevância energética é hipótese e dimensionar a ordem de grandeza esperada do overhead frente à inferência. |

*Verificações de consistência numérica feitas só com o que o texto traz:* 3,5→8,4 bilhões (×2,4) e 415→945 TWh (×2,3) conferem com "mais que dobrou/dobre". Já 0,047 vs. 0,002 kWh por mil inferências (Luccioni et al.) é ≈ 23×, ou seja, pouco mais de **uma** ordem de grandeza; "ordens de grandeza" (1.1) exagera.

## 2. Trabalhos Relacionados (0 / 1,0 — não entregue)

| Critério | Observações do avaliador |
|---|---|
| 2.1 Contextualização e relação com o projeto (1,0) | **Não encontrado no texto** como seção; não pontuado nesta etapa. Há um embrião em 1.2: Liu et al. (2025), Kandogan et al. (2025) e Zhu et al. (2026), com limitação apontada (qualitativo, sem comparação controlada, alegações de fornecedores) — recentes e acadêmicos. Falta, para cada um, o que o projeto aproveita. Falta também enfrentar os comparadores óbvios de uma camada de harness: bibliotecas e gateways de abstração de provedor (ex.: LangChain, LiteLLM, Vercel AI SDK) e estudos empíricos sobre eles. Sem isso, "não foram encontrados estudos" fica frágil. Mo et al. (2023), usado como analogia, é o trabalho mais próximo do desenho (abstração × API nativa, métricas de código) e merece destaque. |

## 3. Objetivos (0,85 / 1,0)

| Critério | Observações do avaliador |
|---|---|
| 3.1 Geral (0,5) | **Atende** (0). Evidência: "Avaliar experimentalmente o trade-off entre desacoplamento e eficiência energética introduzido por uma camada… (harness) entre aplicações web e provedores de modelos de IA, em comparação com a integração direta". Tem verbo, objeto, campo e baseline. Ressalvas: o título promete "projeto", o geral só "avaliar"; e o geral diz "eficiência energética", enquanto pergunta e específicos dizem "custo energético". Unifique. |
| 3.2 Específicos (0,5) | **Parcial** (−0,15, 30%). Evidência: (a) projetar, (b) quantificar substituição, (c) mensurar energia, (d) identificar condições de compensação. Motivos: (i) (d) não é verificável como escrito, pois não há critério para "compensar" (limiar, ponto de equilíbrio, regra de decisão); (ii) nenhum específico cobre implementar as duas versões e **demonstrar a equivalência funcional**, que é a base do experimento (1.3); (iii) a correspondência com etapas da metodologia não é verificável (não entregue). Correção: acrescentar o específico de implementação/equivalência e reescrever (d) com um critério explícito. |

## 4. Fundamentação Teórica (0 / 2,0 — não entregue)

| Critério | Observações do avaliador |
|---|---|
| 4.1 Conceitos-chave (0,5) | **Não encontrado no texto.** Conceitos que a seção terá de cobrir, extraídos do título, problema e objetivos: LLM e agentes (ciclo de ferramentas, distinção agente × multiagente); padrões de agentes e harness; acoplamento, modificabilidade e *vendor lock-in*; camadas de abstração/middleware; métricas de código para substituibilidade; energia em inferência (Green AI), telemetria de hardware; experimentação controlada. |
| 4.2 Fontes (0,5) | **Não avaliável** na fundamentação. Diagnóstico preliminar da lista de referências da Introdução (21 itens, contagem do próprio arquivo): 10 anais, 6 periódicos, 2 livros, 3 relatórios/páginas web (IEA, Menlo, Stack Overflow); 15 de 21 de 2021 em diante (5 de 2026, 6 de 2025). Todas as 21 citações do texto constam na lista e vice-versa. Atenção: dois itens-chave são relatórios de mercado (Menlo) e survey de fornecedor de plataforma (Stack Overflow). |
| 4.3 Texto (0,5) | **Não avaliável.** Na Introdução, o encadeamento é bom (dependência → princípio de projeto → lock-in → harness → energia → lacuna), com voz autoral. |
| 4.4 Escopo e uso (0,5) | **Não avaliável.** Na Introdução, o escopo do conceito de harness é dado ("definido operacionalmente como…"); repita o padrão em cada seção teórica. |

## 5. Procedimentos Metodológicos (0 / 2,5 — não entregue)

Critérios aplicáveis: 5.1, 5.2, 5.3 e 5.5 (0,625 cada). 5.4 não se aplica.

| Critério | Observações do avaliador |
|---|---|
| 5.1 Coerência com os objetivos | **Não encontrado no texto.** Cada específico (a–d) precisa de etapa própria. |
| 5.2 Detalhamento das etapas | **Não encontrado no texto.** |
| 5.3 Implementação | **Não encontrado no texto.** Já mencionado na Introdução: "modelos abertos executados localmente", GPU institucional e protocolo de telemetria de Barros et al. (2026). Faltam modelo e versões, aplicação-base, provedores, carga de requisições, repetições, baseline e métricas. |
| 5.5 Critérios de análise de dados | **Não encontrado no texto.** Defina métricas de substituição (ex.: arquivos/linhas alterados, acoplamento, testes comportamentais que passam) e energéticas (ex.: Wh por requisição, potência média), além do teste estatístico e do critério de "compensa". |
| 5.4 Pesquisa de campo | **Não se aplica.** |
| Cronograma | **Não encontrado no texto.** Perda de −1,0 sobre a seção só se aplicará quando a seção for entregue sem cronograma. |

## 6. Formatação e texto em geral (0,75 / 1,0)

| Critério | Observações do avaliador |
|---|---|
| 7 Formatação e texto (1,0) | **Parcial** (−0,25, 25%). Texto fluente e correto, sem erros ortográficos relevantes. Perdas de apresentação encontradas no arquivo avaliado: (i) **Lista de siglas** desordenada, com as siglas API/GPU/LLM/SDK separadas das expansões e sem ordem alfabética com "IA"; (ii) **Sumário** vazio; (iii) parágrafo de 1.1 com frases fora de ordem ("de dependência já foi descrito…" aparece antes de "IA agêntica —, a quantidade de código…"); (iv) em Barros et al., "Anais do LIII Seminário Integrado de…" aparece deslocado da referência; (v) URL de Stack Overflow quebrada ("<https: //survey…"); (vi) termos estrangeiros (*trade-off*, *glue code*, *vendor lock-in*, *serverless*) devem estar em itálico, e não é possível confirmar no arquivo. **Os itens (i)–(iv) podem ser artefato da conversão PDF→Markdown**; se o PDF estiver correto, a perda cai para ≈ −0,10. Referências sem páginas (Kandogan, Ifath, Vellaisamy, Mo) devem ser completadas conforme a ABNT. |

## 7. Defesa (1,0 — atribuída)

Pontuação atribuída por instrução da rubrica (~1,0); **não avaliada**.

---

## Resumo de pontos

| Parte | Máx. | Obtido | Perdido | Critérios com perda |
|---|---|---|---|---|
| Título/Introdução | 1,5 | 1,30 | 0,20 | 1.2, 1.4 |
| Trabalhos Relacionados | 1,0 | — | — | não entregue |
| Objetivos | 1,0 | 0,85 | 0,15 | 3.2 |
| Fundamentação Teórica | 2,0 | — | — | não entregue |
| Procedimentos Metodológicos | 2,5 | — | — | não entregue |
| Formatação e texto | 1,0 | 0,75 | 0,25 | 7 |
| Defesa | 1,0 | 1,0 | 0 | atribuída |
| **Escopo entregue** | **3,5** | **2,90** | **0,60** | |

Conferência: 10 − 0,60 (perdas) − 5,5 (não entregue) = 3,90 = 2,90 + 1,0 (Defesa).

## Coerência interna

**Não determinável** (faltam fundamentação e metodologia). No recorte entregue:

1. **Problema × objetivo geral:** coerentes. O problema (falta de medição controlada) leva ao objetivo de medir.
2. **Pergunta de pesquisa × hipótese (1.2):** a pergunta pergunta "qual é o custo energético *dessa redução*", pressupondo que há redução, enquanto o parágrafo seguinte a trata como hipótese a testar. Reformule a pergunta de forma neutra.
3. **"Provedor" × modelo local (1.1/1.3 × Resumo):** a motivação trata de provedores comerciais (OpenAI, Anthropic, Google), mas a energia será medida com "modelo aberto executado localmente". O texto não diz como substituir de provedor e medir energia se encaixam, nem o que o overhead da camada significa quando a inferência roda em nuvem. Trate isso como validade externa na metodologia.
4. **Título/geral/específicos:** "projeto" no título, só "avaliar" no geral, e "eficiência" × "custo" energético (ver 3.1). Falta específico para implementação e equivalência funcional (ver 3.2).

## Justificativa e comentários sobre a nota final

A Introdução é a parte forte do projeto: cadeia argumentativa clara, lacuna delimitada com honestidade (reconhece que a taxa de troca de provedor não prova a causa), escopo explícito sobre o que não será avaliado e todas as citações presentes na lista. As perdas vêm de cinco pontos: termo central (*harness*) sem fonte, "custo de substituição" indefinido, relevância energética sustentada por analogia, objetivo (d) sem critério verificável e ausência de específico de implementação, e defeitos de apresentação (siglas, sumário, ordem de frases).
Prioridades antes da próxima entrega: (1) definir operacionalmente "custo de substituição" e "compensa" e refletir isso nos específicos; (2) escrever Trabalhos Relacionados incluindo bibliotecas/gateways de abstração de provedor como comparadores diretos; (3) explicar como a energia medida em modelo local se relaciona à troca entre provedores. A nota de 5,5 pontos pendentes dependerá de fundamentação e metodologia que ainda não existem no texto.

## Verificação de referências (amostra, via busca na web)

| Referência | Resultado |
|---|---|
| Liu et al. (2025) | **Verificada** como preprint (arXiv 2405.10467, mesmos autores e título); versão no *J. Systems and Software* **não confirmada**. |
| Kandogan et al. (2025) | **Verificada** (arXiv 2504.08148; workshop DAIS do ICDE 2025). Descreve registros de agentes e de dados, como o texto afirma. |
| Zhu et al. (2026) | **Não localizada** na busca (título + *Future Internet*). Não significa inexistente; confira o DOI. |
| Vellaisamy et al. (2026) | **Verificada** como preprint (arXiv 2603.12465); venue ISPASS não confirmado. O trabalho trata de overhead de host na pilha de inferência (ver 1.4). |
| Ifath e Haque (2026) | **Verificada** como preprint (arXiv 2604.09611); venue SIGMETRICS não confirmado. Cobre cargas agênticas, como citado. |
| Mo et al. (2023) | **Verificada** (Univ. of Washington Tacoma; compara biblioteca de abstração × APIs nativas, com métricas de código). CloudCom não confirmado diretamente. |
| Demais (Stack Overflow, Menlo, IEA, Luccioni, Fernandez, Sculley, Parnas, Bass, Wohlin, Schwartz, Strubell, Sapkota, Kaur, Issarny, Barros) | **Não verificadas**. Os números citados de Stack Overflow, Menlo, IEA e Luccioni também não foram conferidos com a fonte. |

**Premissas:** pontos divididos igualmente entre os critérios de cada parte; Defesa atribuída; partes não entregues não pontuadas; "recente" = últimos ~5 anos; formatação avaliada sobre o `.md` (norma de referência: ABNT, já usada pelo documento).
