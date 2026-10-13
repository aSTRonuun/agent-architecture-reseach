# Tasks de correção — Projeto e avaliação experimental de uma camada arquitetural desacoplada agêntica (harness): custo de substituição de provedor e custo energético
Origem: `revision/revisao-introducao-v1.md` (1ª revisão, somente Introdução), nota estimada 2,90/3,5 no escopo entregue | Parecer: coerência interna não determinável nesta etapa
Total: 26 tasks (1 crítica, 9 altas, 8 médias, 8 baixas) | Pontos recuperáveis: 0,60 (escopo entregue). As tasks T20–T26 cobrem seções não entregues (5,5 pontos pendentes, não pontuados) e por isso valem 0 aqui.

## Visão geral

| ID | Título | Tipo | Severidade | Pontos | Esforço | Depende de |
|---|---|---|---|---|---|---|
| T01 | Definir operacionalmente "custo de substituição" na Introdução | Clareza/precisão | Média | −0,10 | M | — |
| T02 | Reescrever objetivo específico (d) com critério explícito de "compensa" | Clareza/precisão | Média | −0,15 | M | T01 |
| T03 | Acrescentar objetivo específico de implementação e equivalência funcional | Conteúdo ausente | Média | 0 | P | — |
| T04 | Unificar terminologia e verbos entre título, geral, pergunta e específicos | Coerência interna | Baixa | 0 | P | T03 |
| T05 | Reformular a pergunta de pesquisa de forma neutra | Coerência interna | Baixa | 0 | P | — |
| T06 | Explicar como troca de provedor e energia em modelo local se encaixam | Coerência interna | Baixa | 0 | M | T04 |
| T07 | Alinhar "agêntica" no título com a taxonomia adotada | Clareza/precisão | Baixa | 0 | P | T04 |
| T08 | Citar a origem do termo "harness" | Referência | Média | 0 | M | — |
| T09 | Indicar base e estratégia de busca de "não foram encontrados estudos" | Conteúdo insuficiente | Média | 0 | M | — |
| T10 | Reposicionar relevância energética como hipótese e dimensionar o overhead | Coesão/argumentação | Média | −0,10 | G | — |
| T11 | Moderar "o custo de trocar de provedor deixa de ser hipotético" | Coesão/argumentação | Média | 0 | P | — |
| T12 | Corrigir "ordens de grandeza" para a razão real (≈ 23×) | Clareza/precisão | Baixa | 0 | P | — |
| T13 | Nomear o público-alvo já em 1.2 | Clareza/precisão | Baixa | 0 | P | — |
| T14 | Conferir números e fontes não verificadas pela revisão | Referência | Baixa | 0 | M | — |
| T15 | Localizar e confirmar a referência Zhu et al. (2026) | Referência | Média | 0 | P | — |
| T16 | Confirmar versão publicada e venue dos preprints citados | Referência | Baixa | 0 | P | — |
| T17 | Verificar no PDF e corrigir siglas, sumário, ordem de frases e ref. Barros | Formatação | Alta | −0,15 | M | — |
| T18 | Corrigir URL do Stack Overflow e completar páginas das referências | Referência | Alta | −0,05 | P | T16 |
| T19 | Aplicar itálico nos termos estrangeiros | Formatação | Alta | −0,05 | P | — |
| T20 | Incluir bibliotecas e gateways de provedor como comparadores diretos | Conteúdo ausente | Alta | 0 | G | T09 |
| T21 | Contextualizar os trabalhos relacionados e o que o projeto aproveita | Conteúdo ausente | Alta | 0 | G | T15, T20 |
| T22 | Escrever a Fundamentação Teórica cobrindo os conceitos-chave | Conteúdo ausente | Alta | 0 | G | T01, T02, T08 |
| T23 | Escrever etapa metodológica para cada objetivo específico | Conteúdo ausente | Alta | 0 | M | T02, T03 |
| T24 | Detalhar a implementação e a validade externa na metodologia | Conteúdo ausente | Alta | 0 | G | T06, T23 |
| T25 | Definir métricas, teste estatístico e critério de "compensa" | Conteúdo ausente | Alta | 0 | G | T01, T02, T24 |
| T26 | Elaborar o cronograma | Conteúdo ausente | Crítica | 0 | M | T23, T24, T25 |

Soma dos pontos: T01 (0,10) + T02 (0,15) + T10 (0,10) + T17 (0,15) + T18 (0,05) + T19 (0,05) = **0,60**, igual ao total perdido na revisão.

## Detalhamento

### T01 — Definir operacionalmente "custo de substituição" na Introdução
**Tipo:** Clareza/precisão | **Severidade:** Média | **Critério:** 1.2 Problema | **Pontos:** −0,10 | **Esforço:** M
**Localização:** Introdução 1.2 (o Resumo cita apenas "métricas comportamentais e estruturais do código")
**Evidência:** a revisão diz que "custo de substituição" nunca é definido operacionalmente na Introdução.
**Problema:** o termo está no título, na pergunta e no objetivo (b). Sem definição, não se sabe o que será medido. A perda de −0,10 do critério 1.2 está atribuída a esta task; T08 e T09 contribuem para o mesmo critério.
**Como resolver:**
1. Escolher as dimensões que compõem o custo (a revisão sugere, para a metodologia, arquivos/linhas alteradas, acoplamento e testes comportamentais que passam).
2. Escrever uma frase de definição em 1.2, na primeira ocorrência do termo.
3. Alinhar a redação do Resumo com a definição.
**Critério de aceite:** 1.2 contém uma frase que diz o que é medido e em que unidade ou indicador; o Resumo usa a mesma definição.
**Depende de:** —

### T02 — Reescrever objetivo específico (d) com critério explícito de "compensa"
**Tipo:** Clareza/precisão | **Severidade:** Média | **Critério:** 3.2 Específicos | **Pontos:** −0,15 | **Esforço:** M
**Localização:** Seção Objetivos, específico (d) "identificar condições de compensação"
**Evidência:** a revisão diz que (d) "não é verificável como escrito, pois não há critério para 'compensar' (limiar, ponto de equilíbrio, regra de decisão)".
**Problema:** sem critério, não há como dizer ao final se o objetivo foi atingido, e a análise de dados (T25) fica sem regra de decisão. A perda de −0,15 do critério 3.2 está atribuída a esta task; T03 contribui para o mesmo critério.
**Como resolver:**
1. Escolher a forma do critério: limiar, ponto de equilíbrio ou regra de decisão.
2. Reescrever (d) com verbo mensurável e esse critério.
3. Reaproveitar o mesmo critério em T25.
**Critério de aceite:** (d) traz critério explícito que outra pessoa consegue aplicar aos dados para responder sim ou não.
**Depende de:** T01

### T03 — Acrescentar objetivo específico de implementação e equivalência funcional
**Tipo:** Conteúdo ausente | **Severidade:** Média | **Critério:** 3.2 Específicos | **Pontos:** 0 (perda do critério atribuída a T02) | **Esforço:** P
**Localização:** Seção Objetivos, lista de específicos (a)–(d)
**Evidência:** a revisão diz que "nenhum específico cobre implementar as duas versões e demonstrar a equivalência funcional, que é a base do experimento (1.3)".
**Problema:** a comparação só vale se as duas versões da aplicação forem funcionalmente equivalentes. Hoje isso não aparece entre os objetivos e não terá etapa própria na metodologia.
**Como resolver:**
1. Verificar se o específico (a) "projetar" já cobre parte disso; se sim, ampliá-lo ou fundi-lo.
2. Redigir um específico com verbo mensurável para implementar as duas versões e verificar a equivalência funcional.
**Critério de aceite:** a lista de específicos tem um objetivo que cobre a implementação das duas versões e a verificação de equivalência funcional.
**Depende de:** —

### T04 — Unificar terminologia e verbos entre título, geral, pergunta e específicos
**Tipo:** Coerência interna | **Severidade:** Baixa | **Critério:** 3.1 Geral (ressalva sem perda) e Coerência interna, item 4 | **Pontos:** 0 | **Esforço:** P
**Localização:** Título; objetivo geral; pergunta de pesquisa em 1.2; específicos
**Evidência:** o título promete "projeto" e o geral só "avaliar". O geral diz "eficiência energética", enquanto a pergunta e os específicos dizem "custo energético".
**Problema:** variações de termo e de verbo dão a impressão de objetos de pesquisa diferentes.
**Como resolver:**
1. Escolher um termo único para a dimensão energética e aplicá-lo em todo o texto.
2. Fazer título e geral prometerem o mesmo: incluir "projetar/implementar" no geral (ver T03) ou retirar "projeto" do título.
**Critério de aceite:** o texto usa um único termo para a dimensão energética; os verbos do título e do objetivo geral correspondem.
**Depende de:** T03

### T05 — Reformular a pergunta de pesquisa de forma neutra
**Tipo:** Coerência interna | **Severidade:** Baixa | **Critério:** Coerência interna, item 2 (pergunta × hipótese) | **Pontos:** 0 | **Esforço:** P
**Localização:** Introdução 1.2, pergunta de pesquisa e parágrafo seguinte
**Evidência:** a pergunta pergunta "qual é o custo energético *dessa redução*", enquanto o parágrafo seguinte trata a redução como hipótese a testar.
**Problema:** a pergunta pressupõe um resultado que o texto diz querer testar.
**Como resolver:**
1. Reescrever a pergunta sem pressupor que haja redução (por exemplo, perguntando qual é o custo energético associado à camada).
**Critério de aceite:** a pergunta não contém pressuposição de redução e é compatível com a hipótese do parágrafo seguinte.
**Depende de:** —

### T06 — Explicar como troca de provedor e energia em modelo local se encaixam
**Tipo:** Coerência interna | **Severidade:** Baixa | **Critério:** Coerência interna, item 3 (provedor × modelo local) | **Pontos:** 0 | **Esforço:** M
**Localização:** Introdução 1.1/1.3 e Resumo ("modelo aberto executado localmente")
**Evidência:** a motivação trata de provedores comerciais (OpenAI, Anthropic, Google), mas a energia será medida em modelo aberto local. O texto não diz como as duas coisas se encaixam, nem o que o overhead da camada significa quando a inferência roda em nuvem.
**Problema:** um leitor pode concluir que a medição de energia não responde à motivação. A revisão pede tratamento completo como validade externa na metodologia (T24); aqui fica só o esclarecimento na Introdução.
**Como resolver:**
1. Acrescentar um parágrafo curto em 1.3 dizendo por que o modelo local serve para medir o overhead da camada.
2. Declarar o limite de generalização para provedores em nuvem.
**Critério de aceite:** a Introdução diz explicitamente a relação entre substituição de provedor e medição em modelo local e o limite de generalização; T24 recebe esse ponto.
**Depende de:** T04

### T07 — Alinhar "agêntica" no título com a taxonomia adotada
**Tipo:** Clareza/precisão | **Severidade:** Baixa | **Critério:** 1.1 Título (ressalva sem perda) | **Pontos:** 0 | **Esforço:** P
**Localização:** Título; Introdução 1.1 (taxonomia de Sapkota et al., 2026)
**Evidência:** a revisão diz que "agêntica" conflita com a taxonomia do próprio texto, que reserva "IA agêntica" a sistemas multiagentes, e que o título tem cerca de 30 palavras. Sugestão da revisão: "…camada de integração (harness) para modelos de IA em aplicações web: custo de substituição de provedor e custo energético".
**Problema:** o título usa um termo que o corpo do texto restringe a outro sentido.
**Como resolver:**
1. Decidir entre trocar "agêntica" (por exemplo, pela sugestão da revisão) ou defini-la no texto.
2. Aplicar a decisão em todas as ocorrências.
3. Aproveitar para encurtar o título.
**Critério de aceite:** o uso de "agêntica" no título é compatível com a taxonomia adotada em 1.1, ou está definido no texto.
**Depende de:** T04

### T08 — Citar a origem do termo "harness"
**Tipo:** Referência | **Severidade:** Média | **Critério:** 1.2 Problema | **Pontos:** 0 (perda do critério atribuída a T01) | **Esforço:** M
**Localização:** Introdução 1.1, frase "Na prática recente, o termo harness passou a designar…"
**Evidência:** a revisão aponta que a definição do termo central abre "sem citação".
**Problema:** o conceito central do trabalho se apoia só na voz do autor.
**Como resolver:**
1. Localizar a fonte em que o termo é usado ou definido nesse sentido.
2. Inserir a citação no texto e a entrada correspondente na lista de referências.
**Critério de aceite:** a frase tem citação, e a fonte consta na lista de referências no formato ABNT.
**Depende de:** —

### T09 — Indicar base e estratégia de busca de "não foram encontrados estudos"
**Tipo:** Conteúdo insuficiente | **Severidade:** Média | **Critério:** 1.2 Problema | **Pontos:** 0 (perda do critério atribuída a T01) | **Esforço:** M
**Localização:** Introdução 1.2, afirmação "não foram encontrados estudos"
**Evidência:** a revisão diz que a afirmação "não indica onde nem como se buscou".
**Problema:** a lacuna é a base do problema de pesquisa e hoje não é verificável. Revisar depois de T20, que pode obrigar a restringir a afirmação.
**Como resolver:**
1. Registrar as bases consultadas, os termos de busca e o período.
2. Reescrever a frase informando essas escolhas.
**Critério de aceite:** a frase informa bases, termos e período, de modo que outra pessoa possa repetir a busca.
**Depende de:** —

### T10 — Reposicionar relevância energética como hipótese e dimensionar o overhead
**Tipo:** Coesão/argumentação | **Severidade:** Média | **Critério:** 1.4 Justificativa/impacto | **Pontos:** −0,10 | **Esforço:** G
**Localização:** Introdução 1.1 e 1.3 (IEA, 945 TWh; Vellaisamy et al., 2026)
**Evidência:** a revisão diz que a relevância energética se apoia em dado global e em Vellaisamy et al. (2026), que decompõem o overhead de host dentro da pilha de inferência, não de uma camada de aplicação. O salto até "a camada pode ter custo mensurável" é analogia, não demonstração.
**Problema:** a justificativa afirma mais do que a evidência sustenta. A perda de −0,10 do critério 1.4 está atribuída a esta task; T11 contribui para o mesmo critério.
**Como resolver:**
1. Reescrever a relevância energética como hipótese.
2. Deixar claro que Vellaisamy trata da pilha de inferência e que a extensão à camada de aplicação é analogia.
3. Dimensionar a ordem de grandeza esperada do overhead frente à inferência, com fonte ou com estimativa declarada.
**Critério de aceite:** o texto marca a relevância energética como hipótese, separa o que a evidência mostra do que é analogia e traz a ordem de grandeza esperada, com fonte ou premissa explícita.
**Depende de:** —

### T11 — Moderar "o custo de trocar de provedor deixa de ser hipotético"
**Tipo:** Coesão/argumentação | **Severidade:** Média | **Critério:** 1.4 Justificativa/impacto | **Pontos:** 0 (perda do critério atribuída a T10) | **Esforço:** P
**Localização:** Introdução 1.3 (afirmação) e 1.1 (taxa de troca de 11%)
**Evidência:** a revisão diz que a frase é mais forte do que a evidência, pois o próprio texto admite em 1.1 que a taxa de troca de 11% "não isola a causa".
**Problema:** duas passagens do texto se contradizem em força de afirmação.
**Como resolver:**
1. Reescrever a frase de 1.3 para refletir o que 1.1 sustenta, ou acrescentar evidência que a sustente.
**Critério de aceite:** 1.3 não afirma mais do que 1.1 admite.
**Depende de:** —

### T12 — Corrigir "ordens de grandeza" para a razão real (≈ 23×)
**Tipo:** Clareza/precisão | **Severidade:** Baixa | **Critério:** 1.1 (verificação de consistência numérica) | **Pontos:** 0 | **Esforço:** P
**Localização:** Introdução 1.1, comparação de Luccioni et al. (0,047 vs. 0,002 kWh por mil inferências)
**Evidência:** a revisão calcula ≈ 23×, "pouco mais de uma ordem de grandeza", e diz que "ordens de grandeza" exagera.
**Problema:** a expressão superestima a diferença que os próprios números mostram.
**Como resolver:**
1. Reescrever com a razão calculada (por exemplo, "cerca de 23 vezes") ou "uma ordem de grandeza".
**Critério de aceite:** a expressão é compatível com a razão entre 0,047 e 0,002.
**Depende de:** —

### T13 — Nomear o público-alvo já em 1.2
**Tipo:** Clareza/precisão | **Severidade:** Baixa | **Critério:** 1.3 Público-alvo (ressalva sem perda) | **Pontos:** 0 | **Esforço:** P
**Localização:** Introdução 1.2 (o público só aparece em 1.3)
**Evidência:** a revisão diz que o público ("desenvolvedores e arquitetos que integram LLMs a aplicações web") aparece só em 1.3 e que "vale nomeá-lo já em 1.2".
**Problema:** o problema é apresentado antes de dizer a quem ele pertence.
**Como resolver:**
1. Citar o público em 1.2, na formulação do problema.
**Critério de aceite:** 1.2 nomeia o público-alvo, de forma coerente com 1.3.
**Depende de:** —

### T14 — Conferir números e fontes não verificadas pela revisão
**Tipo:** Referência | **Severidade:** Baixa | **Critério:** Verificação de referências; 4.2 Fontes (atenção) | **Pontos:** 0 | **Esforço:** M
**Localização:** Introdução 1.1 e lista de referências (Stack Overflow, Menlo, IEA, Luccioni, Fernandez, Sculley, Parnas, Bass, Wohlin, Schwartz, Strubell, Sapkota, Kaur, Issarny, Barros)
**Evidência:** a revisão diz que essas referências ficaram "não verificadas" e que os números de Stack Overflow, Menlo, IEA e Luccioni não foram conferidos. Também alerta que dois itens-chave são relatório de mercado (Menlo) e survey de fornecedor de plataforma (Stack Overflow).
**Problema:** números centrais da motivação podem estar errados, e duas fontes-chave têm natureza não acadêmica.
**Como resolver:**
1. Abrir cada fonte e conferir cada número atribuído a ela (incluindo o 11% de troca de provedor e os dados de TWh e kWh).
2. Confirmar a existência e os dados bibliográficos das demais referências não verificadas.
3. Para Menlo e Stack Overflow, buscar fonte acadêmica complementar ou declarar no texto a natureza da fonte.
**Critério de aceite:** existe um registro (lista ou tabela) com cada número, a fonte e a página ou seção onde foi conferido. Não há discrepância pendente, e a natureza das fontes de mercado está explícita no texto.
**Depende de:** —

### T15 — Localizar e confirmar a referência Zhu et al. (2026)
**Tipo:** Referência | **Severidade:** Média | **Critério:** Verificação de referências | **Pontos:** 0 | **Esforço:** P
**Localização:** Introdução 1.2 (limitação de Zhu et al.) e lista de referências
**Evidência:** a revisão diz que a referência ficou "não localizada" na busca (título + *Future Internet*), e que isso "não significa inexistente; confira o DOI".
**Problema:** se a referência estiver incorreta, a limitação atribuída a ela na lacuna não se sustenta.
**Como resolver:**
1. Conferir o DOI e abrir o artigo.
2. Comparar autores, título, venue, ano e a limitação atribuída com o texto.
3. Se não existir, substituir a fonte e rever a afirmação que depende dela.
**Critério de aceite:** o DOI resolve para o artigo, e os dados bibliográficos e a afirmação conferem com o texto. Caso contrário, a citação foi substituída.
**Depende de:** —

### T16 — Confirmar versão publicada e venue dos preprints citados
**Tipo:** Referência | **Severidade:** Baixa | **Critério:** Verificação de referências | **Pontos:** 0 | **Esforço:** P
**Localização:** Lista de referências: Liu et al. (2025), Vellaisamy et al. (2026), Ifath e Haque (2026), Mo et al. (2023)
**Evidência:** a revisão verificou os quatro como preprint (ou sem venue confirmado): versão do *J. Systems and Software* de Liu não confirmada; ISPASS de Vellaisamy e SIGMETRICS de Ifath não confirmados; CloudCom de Mo não confirmado diretamente.
**Problema:** a referência pode indicar um venue que o autor não conferiu.
**Como resolver:**
1. Para cada item, confirmar se há versão publicada e qual é o venue.
2. Ajustar a referência para a versão correta ou marcá-la como preprint (arXiv).
**Critério de aceite:** cada uma das quatro referências indica a versão correta com venue confirmado, ou está marcada como preprint.
**Depende de:** —

### T17 — Verificar no PDF e corrigir siglas, sumário, ordem de frases e ref. Barros
**Tipo:** Formatação | **Severidade:** Alta | **Critério:** 7 Formatação e texto | **Pontos:** −0,15 (estimado, ver premissas) | **Esforço:** M
**Localização:** Lista de siglas; Sumário; parágrafo de 1.1 ("de dependência já foi descrito…" antes de "IA agêntica —, a quantidade de código…"); referência Barros et al. ("Anais do LIII Seminário Integrado de…")
**Evidência:** a revisão lista os itens (i)–(iv) e diz que "podem ser artefato da conversão PDF→Markdown". Se o PDF estiver correto, a perda do critério cai para ≈ −0,10.
**Problema:** a revisão avaliou o `.md` e não conseguiu renderizar o PDF; não se sabe quais defeitos existem no arquivo entregue.
**Como resolver:**
1. Abrir o PDF e conferir cada um dos itens (i)–(iv); registrar quais são artefato de conversão e quais são defeitos reais.
2. Corrigir os defeitos reais no arquivo-fonte: siglas em ordem alfabética, cada uma pareada com sua expansão (incluindo "IA"); sumário preenchido; frases de 1.1 em ordem lógica; título do evento no lugar certo na referência Barros.
3. Se tudo for artefato, registrar isso e fechar a task sem alteração.
**Critério de aceite:** no PDF final, a lista de siglas está em ordem alfabética com sigla e expansão pareadas, o sumário está preenchido, o parágrafo de 1.1 está em ordem lógica e a referência Barros tem o nome do evento na posição correta.
**Depende de:** —

### T18 — Corrigir URL do Stack Overflow e completar páginas das referências
**Tipo:** Referência | **Severidade:** Alta | **Critério:** 7 Formatação e texto | **Pontos:** −0,05 (estimado, ver premissas) | **Esforço:** P
**Localização:** Referência Stack Overflow (URL "<https: //survey…"); referências Kandogan, Ifath, Vellaisamy e Mo
**Evidência:** a revisão aponta (v) a URL quebrada e que as quatro referências citadas estão "sem páginas" e devem ser completadas conforme a ABNT.
**Problema:** a URL não abre e as referências ficam incompletas segundo a norma.
**Como resolver:**
1. Corrigir a URL e testá-la.
2. Completar páginas ou número do artigo das quatro referências, usando a versão confirmada em T16.
**Critério de aceite:** a URL abre a pesquisa citada; as quatro referências têm páginas ou número de artigo conforme a ABNT (ou a indicação equivalente para preprint).
**Depende de:** T16

### T19 — Aplicar itálico nos termos estrangeiros
**Tipo:** Formatação | **Severidade:** Alta | **Critério:** 7 Formatação e texto | **Pontos:** −0,05 (estimado, ver premissas) | **Esforço:** P
**Localização:** Todo o texto (*trade-off*, *glue code*, *vendor lock-in*, *serverless* e outros)
**Evidência:** a revisão diz que esses termos devem estar em itálico e que "não é possível confirmar no arquivo".
**Problema:** o requisito de formatação não pôde ser confirmado.
**Como resolver:**
1. Verificar no PDF quais termos estrangeiros estão sem itálico.
2. Aplicar itálico em todas as ocorrências.
**Critério de aceite:** todas as ocorrências de termos estrangeiros estão em itálico (exceto siglas e nomes próprios).
**Depende de:** —

### T20 — Incluir bibliotecas e gateways de provedor como comparadores diretos
**Tipo:** Conteúdo ausente | **Severidade:** Alta | **Critério:** 2.1 Contextualização e relação com o projeto | **Pontos:** 0 (seção não entregue, não pontuada) | **Esforço:** G
**Localização:** Seção Trabalhos Relacionados (a criar); embrião em 1.2
**Evidência:** a revisão diz que falta "enfrentar os comparadores óbvios de uma camada de harness: bibliotecas e gateways de abstração de provedor (ex.: LangChain, LiteLLM, Vercel AI SDK) e estudos empíricos sobre eles. Sem isso, 'não foram encontrados estudos' fica frágil".
**Problema:** esses comparadores são a alternativa direta ao que o trabalho propõe, e sua ausência enfraquece a lacuna.
**Como resolver:**
1. Levantar as bibliotecas e gateways relevantes, incluindo os três citados pela revisão, e estudos empíricos sobre eles.
2. Descrever, para cada um, o que oferece e como se diferencia do harness proposto.
3. Ajustar a afirmação de 1.2 (T09) conforme o que for encontrado.
**Critério de aceite:** a seção trata os comparadores (ou justifica o recorte) com a diferença de cada um para o projeto, e 1.2 é coerente com o que a seção mostra.
**Depende de:** T09

### T21 — Contextualizar os trabalhos relacionados e o que o projeto aproveita
**Tipo:** Conteúdo ausente | **Severidade:** Alta | **Critério:** 2.1 Contextualização e relação com o projeto | **Pontos:** 0 (seção não entregue, não pontuada) | **Esforço:** G
**Localização:** Seção Trabalhos Relacionados (a criar); Liu et al. (2025), Kandogan et al. (2025), Zhu et al. (2026), Mo et al. (2023)
**Evidência:** a revisão diz que o embrião em 1.2 aponta as limitações, mas "falta, para cada um, o que o projeto aproveita". Mo et al. (2023) é "o trabalho mais próximo do desenho (abstração × API nativa, métricas de código) e merece destaque".
**Problema:** a seção descreve limitações, mas não diz como cada trabalho se relaciona com o projeto.
**Como resolver:**
1. Para cada trabalho, escrever o que faz, sua limitação e o que o projeto aproveita ou como se diferencia.
2. Dar destaque a Mo et al. (2023).
**Critério de aceite:** cada trabalho tem o que faz, a limitação e o que o projeto aproveita; Mo et al. tem tratamento destacado.
**Depende de:** T15, T20

### T22 — Escrever a Fundamentação Teórica cobrindo os conceitos-chave
**Tipo:** Conteúdo ausente | **Severidade:** Alta | **Critério:** 4.1 Conceitos-chave (e 4.3 e 4.4, não avaliáveis) | **Pontos:** 0 (seção não entregue, não pontuada) | **Esforço:** G
**Localização:** Seção Fundamentação Teórica (a criar)
**Evidência:** a revisão lista o que a seção terá de cobrir: LLM e agentes (ciclo de ferramentas, distinção agente × multiagente); padrões de agentes e harness; acoplamento, modificabilidade e *vendor lock-in*; camadas de abstração/middleware; métricas de código para substituibilidade; energia em inferência (Green AI), telemetria de hardware; experimentação controlada.
**Problema:** a seção vale 2,0 pontos e não existe. O padrão de escopo operacional dado a "harness" na Introdução deve ser repetido em cada conceito (4.4).
**Como resolver:**
1. Escrever uma subseção para cada grupo de conceitos da lista da revisão.
2. Em cada uma, delimitar o escopo ("definido operacionalmente como…") e usar fontes acadêmicas (4.2).
3. Encadear as subseções até a lacuna do trabalho (4.3).
**Critério de aceite:** cada grupo de conceitos da lista tem subseção com escopo definido e fonte acadêmica; os conceitos usados em T01 e T02 estão definidos.
**Depende de:** T01, T02, T08

### T23 — Escrever etapa metodológica para cada objetivo específico
**Tipo:** Conteúdo ausente | **Severidade:** Alta | **Critério:** 5.1 Coerência com os objetivos | **Pontos:** 0 (seção não entregue, não pontuada) | **Esforço:** M
**Localização:** Seção Procedimentos Metodológicos (a criar)
**Evidência:** a revisão diz "cada específico (a–d) precisa de etapa própria".
**Problema:** sem etapa por objetivo, não há como verificar se a metodologia o atende.
**Como resolver:**
1. Montar uma tabela objetivo específico → etapa, incluindo o específico acrescentado em T03.
2. Escrever a etapa de cada um.
**Critério de aceite:** todo específico tem etapa correspondente, e toda etapa corresponde a um específico.
**Depende de:** T02, T03

### T24 — Detalhar a implementação e a validade externa na metodologia
**Tipo:** Conteúdo ausente | **Severidade:** Alta | **Critério:** 5.2 Detalhamento das etapas; 5.3 Implementação | **Pontos:** 0 (seção não entregue, não pontuada) | **Esforço:** G
**Localização:** Seção Procedimentos Metodológicos (a criar); Introdução já menciona "modelos abertos executados localmente", GPU institucional e protocolo de telemetria de Barros et al. (2026)
**Evidência:** a revisão diz que "faltam modelo e versões, aplicação-base, provedores, carga de requisições, repetições, baseline e métricas", e pede que a relação provedor × modelo local seja tratada como validade externa.
**Problema:** sem esses itens o experimento não é replicável, e a validade externa fica sem tratamento.
**Como resolver:**
1. Especificar modelo e versões, aplicação-base, provedores, carga de requisições, repetições e baseline.
2. Descrever o hardware e o protocolo de telemetria de Barros et al.
3. Escrever a subseção de validade externa com o ponto levantado em T06.
**Critério de aceite:** outra pessoa consegue reproduzir o experimento a partir do texto; todos os itens da lista estão presentes; existe subseção de validade externa.
**Depende de:** T06, T23

### T25 — Definir métricas, teste estatístico e critério de "compensa"
**Tipo:** Conteúdo ausente | **Severidade:** Alta | **Critério:** 5.5 Critérios de análise de dados | **Pontos:** 0 (seção não entregue, não pontuada) | **Esforço:** G
**Localização:** Seção Procedimentos Metodológicos (a criar)
**Evidência:** a revisão diz "defina métricas de substituição (ex.: arquivos/linhas alterados, acoplamento, testes comportamentais que passam) e energéticas (ex.: Wh por requisição, potência média), além do teste estatístico e do critério de 'compensa'".
**Problema:** sem esses critérios, os dados coletados não levam a uma conclusão.
**Como resolver:**
1. Definir as métricas de substituição, coerentes com a definição de T01.
2. Definir as métricas energéticas.
3. Escolher o teste estatístico e justificar.
4. Aplicar o critério de "compensa" definido em T02.
**Critério de aceite:** a seção lista cada métrica com unidade e forma de coleta, o teste estatístico escolhido e o critério de "compensa" idêntico ao do objetivo (d).
**Depende de:** T01, T02, T24

### T26 — Elaborar o cronograma
**Tipo:** Conteúdo ausente | **Severidade:** Crítica | **Critério:** Cronograma (Procedimentos Metodológicos) | **Pontos:** 0 hoje (a revisão prevê −1,0 sobre a seção se for entregue sem cronograma) | **Esforço:** M
**Localização:** Seção Procedimentos Metodológicos (a criar)
**Evidência:** a revisão diz "Não encontrado no texto. Perda de −1,0 sobre a seção só se aplicará quando a seção for entregue sem cronograma."
**Problema:** a falta de cronograma é a única perda de −1,0 prevista na rubrica e só pode ser evitada com a metodologia pronta.
**Como resolver:**
1. Listar as atividades correspondentes às etapas de T23 a T25.
2. Atribuir períodos e marcos a cada uma.
3. Conferir se o total cabe no prazo do TCC II.
**Critério de aceite:** o cronograma cobre todas as etapas da metodologia, com períodos e marcos, e cabe no prazo do TCC II.
**Depende de:** T23, T24, T25

## Fora da revisão (não convertido)
Nenhum item.

Premissas: severidade derivada das regras da skill. A severidade das tasks de um mesmo critério segue a perda do critério na revisão (Média para 1.2, 1.4 e 3.2; Alta para o critério 7), mesmo quando os pontos são atribuídos a uma única task. Itens "Não encontrado no texto" em seções não entregues (T20–T26) foram tratados como "Não atende" (Alta), e a falta de cronograma como Crítica; ambos valem 0 ponto porque a revisão não os pontuou. Esforço estimado. Pontos conforme a revisão; quando um critério gerou várias tasks, a perda foi atribuída a uma só (T01, T02, T10), e a divisão do critério 7 entre T17 (−0,15), T18 (−0,05) e T19 (−0,05) é estimativa a partir da revisão, que diz que a perda cai para ≈ −0,10 se os itens (i)–(iv) forem artefato de conversão. A nova nota depende de nova avaliação.
