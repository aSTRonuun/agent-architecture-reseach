# Avaliação do projeto de TCC I — 1ª revisão (Fundamentação Teórica)

**Avaliador:** — | **Projeto avaliado:** *Projeto e avaliação experimental de uma camada arquitetural (harness) para integração de modelos de IA em aplicações web: custo de substituição de provedor e custo energético* (Vitor Manoel Alves da Silva; orientador: Prof. Dr. Sidarta Carvalho)
**Arquivos avaliados:** `2-textuais/2-fundamentacao-teorica.tex` (versão de 21/10/2026), lido junto com `2-textuais/1-introducao.tex` para o cruzamento de coerência. `2-textuais/3-metodologia.tex` foi consultado só para checar pendências (está majoritariamente em `\pendencia{}`).
**Tipo de pesquisa:** implementação com experimento controlado (duas versões de uma aplicação web, medição de código e de energia). Sem pesquisa de campo com pessoas.
**Apoio:** rubrica do `revisor-tcc1` (critérios 4.1–4.4) complementada pelo checklist da skill `fundamentacao-teorica-trabalhos-relacionados`.

## Nota estimada

| Escopo | Pontos |
|---|---|
| Fundamentação Teórica (4 critérios × 0,5) | **1,45 / 2,0** |
| Demais partes da rubrica | não avaliadas nesta revisão (Introdução já revisada em `entregas/introduction/revision/revisao-introducao-v1.md`; Trabalhos Relacionados e Metodologia não redigidos) |

**Parecer (coerência interna, no recorte Introdução × Fundamentação):** apto, com uma ressalva corrigível — a fronteira da medição de energia (GPU × CPU), descrita na seção "Coerência interna".
**Maiores perdas:** conceitos-chave ausentes (−0,25), escopo da medição de energia (−0,15), texto repetido da Introdução e ressalvas de processo (−0,15).

---

## 4. Fundamentação Teórica (1,45 / 2,0)

| Critério | Observações do avaliador |
|---|---|
| 4.1 Conceitos-chave (0,5) | **Parcial** (−0,25, 50%). Evidência: os conceitos do título e do problema estão cobertos — LLM, agente e chamada de ferramentas (2.1); modificabilidade, acoplamento, substituibilidade e *lock-in* (2.2.1); ADRs e C4 (2.2.2); camada de abstração e *middleware* (2.3); harness (2.4); energia, potência e NVML (2.5); experimentação controlada (2.6). Ausentes: (i) **critério de decisão do trade-off** — o objetivo (e) pede decidir "se a redução do custo de substituição … justifica o seu custo energético", e a 2.6 só menciona "critério de decisão final, definido antes da coleta", sem base para confrontar grandezas de natureza diferente (linhas alteradas × joules); (ii) **variabilidade e análise estatística das medições** — a 2.6 adia os "procedimentos estatísticos" para a Metodologia, mas o efeito esperado é menor que 1% da energia da requisição (estimativa da Seção 1.1), o que exige justificar conceitualmente como separá-lo do ruído (repetições, unidade amostral, tamanho de efeito); (iii) **equivalência funcional por testes** — o objetivo (b) prevê verificar a equivalência "por meio de testes comuns às duas" versões, e a 2.6 diz que ela "é o que permite atribuir a diferença observada à camada", sem definir como é estabelecida. Correção: subseção curta para (i) e (ii), parágrafo para (iii), e atualizar o Quadro `qua:conceitos-uso`. |
| 4.2 Fontes (0,5) | **Atende** (0). Contagem real das 34 chaves citadas no capítulo (todas presentes no `.bib`): 27 revisadas por pares (periódicos e anais), 2 livros (Wohlin et al., 2024; Bass et al., 2021), 1 norma (ISO/IEC 25010:2023) e 4 documentos técnicos rotulados no texto como não revisados por pares (Anthropic, OpenAI, NVML, OpenTelemetry). 22 das 34 são de 2021 em diante; as antigas são clássicas e usadas como origem de conceito (Parnas, 1972; Stevens et al., 1974; Tyree e Akerman, 2005; Issarny et al., 2007). Fonte dominante: Liu et al. (2025), 8 citações. Observações sem perda: (a) a primeira frase da 2.3 ("Uma camada de abstração interpõe…"), definição central da seção, não tem citação; (b) o modelo C4 é definido só por Mavrogiorgou et al. (2025), guia secundário que, segundo o comentário do próprio `.tex`, não foi lido na íntegra; falta a fonte primária (Simon Brown). Ressalva informativa: o comentário do capítulo declara 7 fontes não lidas na íntegra (Issarny, Stevens, Tyree, Buchgeher, Mavrogiorgou, Yao, Chang e Geng), às quais o texto só atribui o que consta do título/resumo — prática correta, mas a banca pode perguntar. |
| 4.3 Texto (0,5) | **Parcial** (−0,15, 30%). Evidência: o encadeamento é bom — abertura que anuncia o percurso, transições entre seções e síntese (2.7) com quadro conceito → uso → objetivo; há voz autoral. Motivos: (i) **cerca de 7 trechos repetem a Introdução quase literalmente**: Parnas/Bass (2.2.1, §1), Sculley (2.2.1, §1), Kandogan (2.3, §2), definição de Rafique e Bindschaedler (2.4.1, §1), Schwartz/Strubell (2.5, §1), Fernández et al. (2.5, §3) e "Estendê-las … é uma analogia" (2.5, §4); (ii) **ressalvas de processo repetidas** — "do autor" (5 ocorrências no corpo), "não revisado por pares" (2), além de "definição operacional", "transposição", "julgamento do autor" — e **7 remissões "na Metodologia"** a um capítulo ainda em `\pendencia{}`, o que dá ao texto tom de registro de auditoria; (iii) o par **"extensional/intensivo"** (2.5, §2) é terminologia do autor, sem fonte; "intensivo" tem outro sentido em física e "extensional" não é a forma usual em português. Correção: no Cap. 2, aprofundar (mecanismo, condições, limitações) em vez de repetir a frase da Introdução; declarar uma única vez, na abertura, a política sobre documentos técnicos e definições operacionais; trocar as remissões por `\ref{}`; usar "efeito de duração" e "efeito de potência" ou citar fonte do par. |
| 4.4 Escopo e uso (0,5) | **Parcial** (−0,15, 30%). Evidência: cada seção fecha ligando o conceito ao trabalho — 2.1 (requisição simples × agêntica), 2.2.1 (custo de substituição), 2.2.2 (ADRs/C4 como documentação, não como objeto), 2.3 (custo da indireção × benefício), 2.4.4 (o que é medido e o que só é implementado), 2.6 (variável independente e dependentes). Motivo: a 2.5 fixa o escopo da medição na GPU ("Por isso o trabalho mede a energia da GPU por telemetria do *hardware*") sem justificar essa fronteira diante do objeto estudado: o trabalho próprio da camada roda na CPU do servidor (é o que a Seção 1.1 estima), e a própria fonte citada na 2.5, Vellaisamy et al. (2026), trata justamente da sobrecarga no processador hospedeiro. Correção: definir a fronteira do sistema medido (GPU e/ou CPU) e justificá-la; se a CPU ficar de fora, declarar que o construto captura só o efeito indireto (número de chamadas, tamanho do contexto). |

## Resumo de pontos

| Parte | Máx. | Obtido | Perdido | Critérios com perda |
|---|---|---|---|---|
| Fundamentação Teórica | 2,0 | 1,45 | 0,55 | 4.1 (−0,25), 4.3 (−0,15), 4.4 (−0,15) |

## Coerência interna

**Apto, com ressalva.** Três cruzamentos:

- **(a) Objetivos × fundamentação.** O objetivo (d) — "mensurar o custo energético que a camada de harness acrescenta" — e a estimativa da Seção 1.1 ("o trabalho próprio da camada ocupe a CPU do servidor por até 10 ms a cerca de 100 W") apontam para um custo direto na CPU. A Seção 2.5 só fundamenta a telemetria de GPU (NVML), e a medição de CPU (RAPL) está pendente na Metodologia (item A11, comentário do Benchmark 2). Como está, o instrumento fundamentado não alcança o custo direto da camada. É corrigível (decidir o A11 e fundamentar o que for decidido), por isso não torna o projeto inapto.
- **(b) Objetivo (e) × fundamentação.** O objetivo que fecha a questão de pesquisa depende de um critério de decisão sem base no referencial (ver 4.1-i).
- **(c) Problema × objetivo geral.** Coerentes: o objetivo geral confronta exatamente os dois custos do problema (Seção 1.2).

Observação sem efeito na nota: o Quadro `qua:harness-liu` apresenta os graus de correspondência (Parcial, Analogia, Nenhuma), mas a justificativa de cada grau foi migrada para a Metodologia (`sec:delimitacao`). Enquanto a Metodologia não compila, o leitor do Cap. 2 vê o grau sem a justificativa.

## Verificação de referências (amostragem)

| Referência | Resultado |
|---|---|
| Rafique e Bindschaedler (2026), ClawVM | Verificada no arXiv (2604.10352). Publicação nos anais do EuroMLSys '26 não confirmada na busca. |
| Vellaisamy et al. (2026), TaxBreak | Verificada no arXiv (2603.12465) e no sumário dos anais do ISPASS 2026. |
| Ifath e Haque (2026) | Verificada no arXiv (2604.09611). Publicação nos *Abstracts* do SIGMETRICS 2026 não confirmada na busca. |
| Chang e Geng (2025), SagaLLM | Verificada (PVLDB vol. 18, p. 4874). |
| Mavrogiorgou et al. (2025), C4 | Verificada (registro no ResearchGate). |
| Demais (29) | Não verificadas nesta revisão; o projeto declara conferência via CrossRef em `context/planning/consolidated_references.md`. |

Fontes da verificação: [ClawVM, arXiv](https://arxiv.org/pdf/2604.10352) · [TaxBreak, arXiv](https://arxiv.org/abs/2603.12465) · [ISPASS 2026, sumário](https://www.proceedings.com/content/086/086249webtoc.pdf) · [Ifath e Haque, arXiv](https://arxiv.org/pdf/2604.09611) · [SagaLLM, PVLDB](https://www.vldb.org/pvldb/vol18/p4874-chang.pdf) · [Mavrogiorgou et al., ResearchGate](https://www.researchgate.net/publication/394564355_C4_Model_a_Research_Guide_for_Designing_Software_Architectures)

## Justificativa e comentários sobre a nota

A Fundamentação cobre os conceitos do título com fontes de boa qualidade, delimita o escopo de cada conceito e fecha com um quadro que liga conceito, uso e objetivo — por isso 4.2 atende e as demais perdas são parciais. O que mais pesou foi o que falta para os dois objetivos finais: não há base para o critério de decisão do objetivo (e) nem para tratar estatisticamente um efeito energético que a própria Introdução estima em menos de 1%. A segunda perda relevante é de escopo: a medição fundamentada (GPU) não alcança o custo direto da camada (CPU), o que também é a única ressalva de coerência. No texto, a repetição quase literal de cerca de 7 trechos da Introdução e o excesso de ressalvas de processo reduzem a voz própria do capítulo. Correções prioritárias: (1) decidir e fundamentar a fronteira da medição de energia; (2) fundamentar o critério de decisão do trade-off; (3) reescrever os trechos repetidos aprofundando em vez de repetir.

## Fora da revisão

- O Cap. 3 (Trabalhos Relacionados) está em `\pendencia{}`. Kandogan et al. (2025), Zhu et al. (2026) e Mo et al. (2023) já aparecem no Cap. 2; ao redigir o Cap. 3, evitar repetir a mesma descrição.
- Conferir se a GPU (H100 ou H200) e a versão do Qwen3.6 (27B ou 35B) citadas na Introdução batem com o servidor efetivamente usado.

Premissas: avaliação restrita à Parte 4 da rubrica (só Introdução e Fundamentação estão completas; a Introdução já tem revisão própria); 0,5 por critério (divisão igual da rubrica); perdas arredondadas a múltiplos de 0,05; nota apresentada como estimativa. Referências verificadas: 5 por amostragem (tabela acima).
