# Avaliação do projeto de TCC I — revisão do texto completo (v1)

**Avaliador:** — | **Projeto avaliado:** *Projeto e avaliação experimental de uma camada arquitetural (harness) para integração de modelos de IA em aplicações web: custo de substituição do provedor e custo energético* (Vitor Manoel Alves da Silva; orientador: Prof. Dr. Sidarta Carvalho)
**Data:** 16/11/2026 | **Versão avaliada:** commit `44e58f2` (branch `correcoes-validacao-cruzada-v1`)
**Arquivos avaliados:** `2-textuais/1-introducao.tex`, `2-textuais/trabalhos-relacionados.tex`, `2-textuais/2-fundamentacao-teorica.tex`, `2-textuais/3-metodologia.tex`, `3-pos-textuais/apendices/apendice-busca.tex`, `3-pos-textuais/apendices/apendice-delimitacao.tex`, `3-pos-textuais/referencias.bib` e `documento.tex`. O Resumo existe, mas não entra na entrega parcial.
**Tipo de pesquisa:** implementação (experimento com artefato de software, sem participantes).
**Apoio:** rubrica do `revisor-tcc1` (Pinheiro e Bezerra, 2014), os 19 critérios.

**Nota estimada: 8,45 / 10**

**Parecer:** apto à defesa (coerência interna). **Maiores perdas:** critérios de análise de dados (−0,25), formatação (−0,25), cobertura do objetivo energético pela metodologia (−0,20) e pilha de implementação indefinida (−0,20).

**Limite desta revisão:** a formatação foi conferida no `documento.pdf` de 15/11/2026 (23h34), anterior aos commits `bf7713d` e `44e58f2`. O texto atual não foi recompilado na revisão. A justificativa dada então ("não há LaTeX nesta máquina") estava errada: só se procurou `pdflatex` e `latexmk`, e o `tectonic` está instalado (`/opt/homebrew/bin/tectonic`). Ver a correção no backlog, "Situação em 18/11/2026".

---

## 1. Título/Introdução (1,30 / 1,5)

| Critério | Observações do avaliador |
|---|---|
| 1.1 Título (0,375) | **Atende.** Traz ação ("projeto e avaliação experimental"), objeto (camada de *harness*), domínio (aplicações *web*) e as duas dimensões avaliadas. |
| 1.2 Problema (0,375) | **Parcial** (−0,10, leve). A questão de pesquisa e a lacuna estão explícitas (Seção 1.2, com remissão ao Apêndice A). Mas "essa incorporação costuma ocorrer da forma mais direta possível" (1.1) e "o benefício mais alegado da camada" (1.2) não têm fonte, e o próprio texto admite que os números da Menlo "não isolam a causa". Correção: citar fonte para as duas afirmações ou reescrevê-las como premissa. |
| 1.3 Público-alvo (0,375) | **Atende.** "Desenvolvedores e arquitetos que integram LLMs a aplicações *web*" aparece nas Seções 1.2 e 1.3, ligado à decisão entre acoplar e abstrair. |
| 1.4 Justificativa (0,375) | **Parcial** (−0,10, leve). O lado da substituição está demonstrado com dados de mercado. O lado energético se apoia em números agregados da IEA, enquanto a estimativa do próprio autor prevê acréscimo "inferior a 1%" por requisição. Correção: justificar por que energia, e não latência ou custo financeiro, é o preço relevante para esse público. |

Conferido: a aritmética da estimativa da Seção 1.1 fecha (0,047 kWh por mil inferências ≈ 170 J por requisição; 10 ms a 100 W = 1 J).

## 2. Trabalhos Relacionados (1,00 / 1,0)

| Critério | Observações do avaliador |
|---|---|
| 2.1 Contextualização e relação (1,0) | **Atende.** São 12 trabalhos revisados por pares, 11 deles de 2023 a 2026 (a exceção, Feitosa et al., 2017, é justificada), cada um com semelhança e diferença declaradas, mais o Quadro 1 e o protocolo de busca do Apêndice A. Ressalvas sem perda: (i) o trabalho "mais próximo quanto ao objetivo" (Morais et al., 2026) foi julgado só pelo resumo, como o próprio texto declara; (ii) o Apêndice A registra que "o número de trabalhos triados e excluídos em cada etapa não foi registrado"; (iii) a coluna "Manutenibilidade medida: Sim" da proposta conta de novo a medição do custo de substituição (ver item 5 da coerência interna). |

Recência medida por 5 anos (2021 a 2026).

## 3. Objetivos (0,85 / 1,0)

| Critério | Observações do avaliador |
|---|---|
| 3.1 Geral (0,5) | **Atende.** Verbo, objeto e campo presentes ("Projetar e avaliar experimentalmente uma camada… entre aplicações *web* e provedores de modelos de IA"), com o termo de comparação (integração direta). |
| 3.2 Específicos (0,5) | **Parcial** (−0,15, leve). Os cinco levam ao geral e têm atividade correspondente. Porém (d) promete "mensurar o custo energético que a camada acrescenta", e a metodologia só estima o trabalho próprio da camada por limite superior; (a) diz delimitar "com base em padrões arquiteturais publicados", mas a Seção 3.4.1 afirma que "a lista não vem da literatura" e o Apêndice B já declara o objetivo atendido. Correção: reescrever (d) como medição do efeito sobre a inferência e estimativa do custo direto, e ajustar (a). |

## 4. Fundamentação Teórica (1,70 / 2,0)

| Critério | Observações do avaliador |
|---|---|
| 4.1 Conceitos-chave (0,5) | **Parcial** (−0,15, leve). Cobertos: LLM, agente, chamada de ferramentas, modificabilidade, acoplamento, substituibilidade, *middleware*, *harness*, energia e potência, NVML, RAPL, experimentação controlada, equivalência por testes, Mann-Whitney e tamanho de efeito, ATAM. Ausentes, embora usados na Metodologia: margem de não inferioridade (atividade 4), delta de Cliff, correção de Holm-Bonferroni e teste de Shapiro-Wilk (atividade 12) e estimativa de carbono por fator de emissão (Quadro 5). Correção: um parágrafo na Seção 3.6.2 e fonte para o fator de emissão. |
| 4.2 Fontes (0,5) | **Parcial** (−0,15, leve). Contagem real das 52 referências citadas: 38 revisadas por pares (15 em periódicos, 23 em anais), 2 livros, 1 norma, 1 relatório técnico e 10 documentos, sites e relatórios de mercado; 31 são de 2021 em diante, 6 são documentos sem data e 15 são anteriores a 2021. Fonte dominante: Liu et al. (2025), 21 citações. A abertura do capítulo diz que fonte não revisada por pares serve "nunca para sustentar afirmação empírica", mas "aplicações em produção costumam depender de recursos desse tipo" (atividade 1) se apoia em um único relato da Thoughtworks e motiva um fator inteiro do *Benchmark* 1. Correção: buscar fonte revisada ou declarar o cenário como exploratório. |
| 4.3 Texto (0,5) | **Atende.** Há transições entre seções ("Dessa descrição decorre a distinção que o experimento usa") e voz autoral constante; não há indício de composição por fragmentos. |
| 4.4 Escopo e uso (0,5) | **Atende.** Todas as seções fecham com a ligação ao trabalho ("Adota-se aqui o primeiro uso"; "Neste trabalho, o diagrama de contêineres…"), e o Quadro 3 liga cada conceito a um objetivo específico. |

## 5. Procedimentos Metodológicos (1,85 / 2,5)

Critérios aplicáveis: 5.1, 5.2, 5.3 e 5.5 (0,625 cada). O cronograma está presente, sem desconto.

| Critério | Observações do avaliador |
|---|---|
| 5.1 Responde aos objetivos (0,625) | **Parcial** (−0,20, leve). A abertura do capítulo mapeia cada objetivo às atividades. Mas a atividade 6 faz as duas versões enviarem "as mesmas chamadas, com o mesmo contexto" e a atividade 12 desconta a potência ociosa, de modo que a diferença medida na GPU tende a zero por construção (inferência do avaliador a partir do desenho). Além disso, o plano alternativo da atividade 10 troca o *Benchmark* 2 por recuperação de falhas, atributo que a Justificativa exclui. Correção: medir a CPU da máquina da aplicação ou rebaixar o objetivo (d); rever o plano alternativo. |
| 5.2 Etapas detalhadas (0,625) | **Atende.** As 13 atividades trazem entrada, ação, critério e saída (por exemplo, os cinco critérios de escolha da aplicação e o roteiro de sessão da atividade 11). |
| 5.3 Implementação (0,625) | **Parcial** (−0,20, leve). Modelos, GPU, NVML, C4, ADRs, métricas e linha de base estão definidos. Linguagem, *framework*, servidor de inferência, máquina da aplicação e o conjunto de requisições ficam para as atividades 1 e 2. Há ainda um risco não listado nas ameaças: se o servidor local for compatível com a OpenAI (atividade 2), o adaptador do modelo local, escrito na atividade 5, antecipa o código da troca medida na atividade 7. |
| 5.4 Pesquisa de campo | **Não se aplica.** Não há participantes nem coleta com pessoas; o custo de substituição é medido "por métricas de código, sem participantes". |
| 5.5 Critérios de análise (0,625) | **Parcial** (−0,25, moderada). A atividade 12 prevê Mann-Whitney "em caso de rejeição" da normalidade, mas não diz o que usar se ela não for rejeitada. A atividade 4 fala em "margem de não inferioridade", e a atividade 12 só lista teste de diferença. O critério de decisão não traz valores de exemplo nem diz sobre qual das cinco métricas primárias do *Benchmark* 1 incide a "redução mínima". Correção: definir os três pontos e dar ao menos faixas ilustrativas. |

Cronograma (sem efeito na nota): os nomes das 13 atividades batem com o texto e com a Figura 2. Março concentra a versão D, o piloto e a verificação do orçamento de GPU, sem folga.

## 6. Coerência interna

**Apto à defesa.** Os desvios são pontuais e corrigíveis:

1. **Objetivo (d) × *Benchmark* 2.** O objetivo promete mensurar o custo da camada; a Seção 3.5 diz que essa parcela "não é medida: é estimada por um limite superior". É o ponto que a banca mais deve explorar.
2. **Atividade 4 × atividade 12.** A margem de não inferioridade é planejada, mas a análise não inclui teste de não inferioridade.
3. **Atividade 10 × Justificativa.** O plano alternativo avalia recuperação de falhas, que a Seção 1.3 declara fora da avaliação.
4. **Hipótese × análise.** A Seção 1.2 chama de "a ser testada" uma hipótese cuja metade (custo de substituição) terá só comparação descritiva, com uma troca por célula.
5. **Quadro 1 × Seção 1.3.** A proposta marca "Manutenibilidade medida: Sim", e a Justificativa restringe o trabalho a duas dimensões; a coluna conta de novo a medição do custo de substituição.

## 7. Formatação e Texto (0,75 / 1,0)

| Critério | Observações do avaliador |
|---|---|
| 7.1 Formatação e linguagem (1,0) | **Parcial** (−0,25, leve). A linguagem é clara e correta, e figuras e quadros têm legenda e fonte no padrão abnTeX2/UFC. No PDF de 15/11, a Lista de Abreviaturas e Siglas sai em branco (p. 4) e o sumário lista parágrafos como "4.5.0.0.1 Validade interna" e "B.0.0.0.1 Responsabilidade 1". Há ainda "multiagentes" (Seção 1.1) contra "multiagente" (Seção 3.1), "GOMES DE B. FILHO, B." e "Jafari Kaleibar" fora do padrão na lista de referências, e palavras quebradas nas células do Quadro 1 ("substitui-ção", "fra-meworks", "topo-logias"). |

## 8. Defesa (1,00 / 1,0)

Atribuída por instrução da rubrica, não avaliada.

## Resumo de pontos

| Parte | Máx. | Obtido | Perdido | Critérios com perda |
|---|---|---|---|---|
| Título/Introdução | 1,5 | 1,30 | 0,20 | 1.2, 1.4 |
| Trabalhos Relacionados | 1,0 | 1,00 | 0,00 | — |
| Objetivos | 1,0 | 0,85 | 0,15 | 3.2 |
| Fundamentação Teórica | 2,0 | 1,70 | 0,30 | 4.1, 4.2 |
| Procedimentos Metodológicos | 2,5 | 1,85 | 0,65 | 5.1, 5.3, 5.5 |
| Formatação e Texto | 1,0 | 0,75 | 0,25 | 7.1 |
| Defesa | 1,0 | 1,00 | 0,00 | atribuída |
| **Total** | **10,0** | **8,45** | **1,55** | |

## Justificativa e comentários sobre a nota final

O projeto tem problema delimitado, lacuna sustentada por busca registrada e metodologia detalhada; as perdas se concentram na ligação entre o que se promete medir em energia e o que o desenho de fato mede. A maior perda (5.5) vem de três lacunas de análise: o ramo sem rejeição da normalidade, o teste de não inferioridade ausente e um critério de decisão sem valores nem métrica-alvo. A segunda (5.1 e 3.2) vem de a medição na GPU tender a diferença nula por construção, restando ao custo direto da camada apenas uma estimativa. A formatação perde pelo PDF: lista de siglas em branco e sumário com parágrafos numerados.

Correções prioritárias:

1. Decidir entre medir a CPU da máquina da aplicação (máquina com RAPL ou medidor externo) e reescrever o objetivo (d) e o título do *Benchmark* 2 como efeito sobre a inferência e limite do custo direto.
2. Fechar a análise estatística: teste para o caso normal, teste de não inferioridade e métrica-alvo do critério de decisão, com faixas de exemplo.
3. Recompilar com `makeglossaries`, tirar os `\paragraph` do sumário e fixar a ordem de construção dos adaptadores para não contaminar o *Benchmark* 1.

## Fora da nota

Os comentários do próprio fonte registram afirmações "A CONFERIR" atribuídas a Bass et al. (2021), Wohlin et al. (2024), Parnas (1972), Sculley et al. (2015), Schwartz et al. (2020) e Fernández et al. (2025), e a norma ISO/IEC 25010 como não lida (cabeçalho de `2-textuais/2-fundamentacao-teorica.tex` e `referencias.bib`). Vale conferi-las antes da defesa.

## Premissas

- Divisão igual dos pontos entre os critérios de cada parte; Defesa atribuída.
- Referências: 18 das 52 verificadas no Crossref pelo DOI (título, autores, ano e páginas conferem): Liu et al. (2025), Mo et al. (2023), Xiao et al. (2025), Barros et al. (2026), Vellaisamy et al. (2026), Rafique e Bindschaedler (2026), Feitosa et al. (2017), Wohlin et al. (2024), Luccioni et al. (2024), Morais et al. (2026), Matinpour et al. (2026), Tripathy et al. (2026), Bucaioni et al. (2025), Kandogan et al. (2025), Zhu et al. (2026), Fernández et al. (2025), Arcuri e Briand (2011) e Sapkota et al. (2026). As outras 34 e o conteúdo atribuído às fontes não foram verificados.
- Todas as 52 chaves citadas têm entrada no `.bib`; 7 entradas do `.bib` não são citadas (retiradas do capítulo de Trabalhos Relacionados em 03/11/2026).
