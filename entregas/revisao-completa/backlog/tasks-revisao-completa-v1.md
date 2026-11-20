# Tasks de correção — revisão do texto completo do TCC I

Origem: `../revision/revisao-completa-v1.md` (16/11/2026, commit `44e58f2`), nota estimada 8,45/10 | Parecer: apto à defesa
Total: 15 tasks (0 críticas, 0 altas, 12 médias, 3 baixas) | Pontos recuperáveis: 1,55

Abreviações: "VC Tnn", "Fund Tnn", "TR Tnn" e "Intro Tnn" são tasks dos backlogs em `entregas/validacao-cruzada`, `entregas/fundamentacao`, `entregas/trabalhos-relacionados` e `entregas/introduction`. "Ann" são itens do `context/action_log.md`.

Sobreposição com o que já existe: a T01 reabre a consequência da A11 (decidida em 15/11) para a redação do objetivo (d); a T06 é a parte de texto da A30; a T08 e a T09 dependem da A29; a T13 é o passo 3 da VC T02, que continua aberto; a T05 retoma a conferência da lista de siglas que a Intro T17 e a VC deixaram para o Overleaf.

## Visão geral

| ID | Título | Tipo | Severidade | Pontos | Esforço | Depende de |
|---|---|---|---|---|---|---|
| T01 | Alinhar o objetivo (d) ao que o *Benchmark* 2 de fato mede | Coerência interna | Média | −0,20 | G | A11 |
| T02 | Fechar o plano de análise estatística do *Benchmark* 2 | Método | Média | −0,15 | M | T01 |
| T03 | Fundamentar os testes estatísticos e a estimativa de carbono | Conteúdo ausente | Média | −0,15 | M | T02 |
| T04 | Sustentar a afirmação sobre recursos específicos de provedor | Referência | Média | −0,15 | M | A31 |
| T05 | Recompilar o PDF e corrigir a lista de siglas e o sumário | Formatação | Média | −0,15 | P | — |
| T06 | Dar métrica-alvo e faixas de exemplo ao critério de decisão | Conteúdo insuficiente | Média | −0,10 | M | T01, A30 |
| T07 | Rever o plano alternativo da atividade 10 | Coerência interna | Média | −0,10 | M | T01 |
| T08 | Fixar a ordem dos adaptadores para não contaminar o *Benchmark* 1 | Método | Média | −0,10 | P | A29 |
| T09 | Indicar tecnologias candidatas e o conjunto de requisições | Conteúdo insuficiente | Média | −0,10 | M | A29 |
| T10 | Dar fonte às duas afirmações sem citação da Introdução | Referência | Média | −0,10 | M | — |
| T11 | Justificar a energia como o preço relevante da camada | Coesão/argumentação | Média | −0,10 | P | T01 |
| T12 | Ajustes pontuais de forma: referências, "multiagente" e Quadro 1 | Formatação | Média | −0,10 | P | A06 |
| T13 | Fechar a redação do objetivo (a) | Clareza/precisão | Baixa | −0,05 | P | VC T02 |
| T14 | Alinhar "hipótese a ser testada" à análise descritiva do *Benchmark* 1 | Coerência interna | Baixa | 0 | P | — |
| T15 | Rever a coluna "Manutenibilidade medida" do Quadro 1 | Coerência interna | Baixa | 0 | P | — |

Ordem sugerida: T01 primeiro, porque T02, T06, T07 e T11 dependem da decisão sobre a medição de energia; T05, T08, T10, T12, T14 e T15 são independentes e podem ser feitas a qualquer momento; T13 espera o orientador.

## Detalhamento

### T01 — Alinhar o objetivo (d) ao que o *Benchmark* 2 de fato mede
**Tipo:** Coerência interna | **Severidade:** Média | **Critério:** Objetivos 3.2 (parte do objetivo d); Metodologia 5.1 (parte da medição); Coerência interna, item 1 | **Pontos:** −0,20 (−0,10 de 3.2 e −0,10 de 5.1) | **Esforço:** G
**Localização:** `1-introducao.tex:258-259` (objetivo d); `2-fundamentacao-teorica.tex`, Seção 3.5 (parágrafos da fronteira da medição); `3-metodologia.tex:320-332` (atividade 6), `:529-550` (atividade 12) e Seção do *Benchmark* 2.
**Evidência:** a revisão aponta que (d) promete "mensurar o custo energético que a camada acrescenta", que a Seção 3.5 diz que essa parcela "não é medida: é estimada por um limite superior", e que, como as duas versões enviam "as mesmas chamadas, com o mesmo contexto" e a potência ociosa é descontada, a diferença medida na GPU tende a zero por construção (inferência do avaliador).
**Problema:** o verbo do objetivo e o nome do experimento prometem uma medição que o desenho não faz; o que é medido tem resultado esperado nulo e o que interessa é só estimado. É o ponto de coerência que a banca mais deve explorar.
**Como resolver:**
1. Decidir, com o orientador, entre dois caminhos: (i) medir a energia da CPU da máquina da aplicação (máquina com RAPL ou medidor externo), o que reabre a A11; ou (ii) manter a A11 e reduzir a promessa.
2. No caminho (ii), reescrever o objetivo (d) em dois verbos: medir o efeito da camada sobre a energia de inferência e estimar, por limite superior, o seu custo direto. Ajustar o objetivo geral, a hipótese da Seção 1.2 e o Resumo no mesmo sentido.
3. Dizer na Seção do *Benchmark* 2 qual resultado é esperado na GPU e por que a medição ainda é necessária (verificar que a camada não altera chamadas, contexto nem duração).
4. Registrar a decisão na A11 do `context/action_log.md`.
**Critério de aceite:** o verbo do objetivo (d), a hipótese da Seção 1.2, a Seção 3.5 e as atividades 6 e 12 descrevem a mesma medição; o texto declara o resultado esperado na GPU; nenhuma passagem diz "mensurar" ou "medir" para a parcela que é estimada.
**Depende de:** A11 (decisão vigente; reabrir só no caminho i).

### T02 — Fechar o plano de análise estatística do *Benchmark* 2
**Tipo:** Método | **Severidade:** Média | **Critério:** Metodologia 5.5 (ramo da normalidade e não inferioridade); Coerência interna, item 2 | **Pontos:** −0,15 | **Esforço:** M
**Localização:** `3-metodologia.tex:284` (atividade 4, "margem de não inferioridade") e `:534-544` (atividade 12, pacote estatístico).
**Evidência:** a revisão cita que a atividade 12 prevê Mann-Whitney "em caso de rejeição" da normalidade sem dizer o que usar se ela não for rejeitada, e que a atividade 4 planeja uma "margem de não inferioridade" enquanto a atividade 12 só lista teste de diferença.
**Problema:** o plano tem um ramo sem teste definido, e um teste de diferença não significativo não demonstra não inferioridade. A pergunta "o consumo é comparável?" fica sem procedimento que a responda.
**Como resolver:**
1. Definir o teste do ramo em que a normalidade não é rejeitada, ou adotar o teste não paramétrico nos dois casos e retirar o Shapiro-Wilk.
2. Escolher o procedimento de não inferioridade (por exemplo, intervalo de confiança da diferença comparado à margem) e descrevê-lo na atividade 12.
3. Dizer sobre qual métrica primária a margem incide e em que unidade (joules por requisição ou percentual).
4. Conferir a consistência com a A18 (limiar do delta de Cliff).
**Critério de aceite:** a atividade 12 nomeia um teste para cada ramo da decisão e um procedimento de não inferioridade; a margem citada na atividade 4 tem métrica e unidade; nenhum teste é citado em uma atividade e ausente da outra.
**Depende de:** T01 (a métrica analisada depende do que é medido).

### T03 — Fundamentar os testes estatísticos e a estimativa de carbono
**Tipo:** Conteúdo ausente | **Severidade:** Média | **Critério:** Fundamentação 4.1 | **Pontos:** −0,15 | **Esforço:** M
**Localização:** `2-fundamentacao-teorica.tex`, Seção 3.6.2; `3-metodologia.tex:471` (linha "Carbono estimado" do Quadro 5).
**Evidência:** a revisão lista como ausentes da Fundamentação, embora usados na Metodologia: margem de não inferioridade, delta de Cliff, correção de Holm-Bonferroni, teste de Shapiro-Wilk e estimativa de carbono por fator de emissão.
**Problema:** procedimentos de análise aparecem na Metodologia sem base no referencial; o único apoio é a remissão ao trabalho anterior do autor. O fator de emissão não tem fonte.
**Como resolver:**
1. Depois da T02, acrescentar à Seção 3.6.2 um parágrafo que defina, com fonte, cada procedimento que permanecer no plano (tamanho de efeito adotado, correção para comparações múltiplas, não inferioridade).
2. Citar a fonte do fator de emissão da matriz elétrica e dizer em uma frase como o gCO₂e é obtido, ou retirar a métrica do Quadro 5.
3. Atualizar o Quadro 3 se entrar conceito novo.
**Critério de aceite:** todo teste, correção e métrica citados nas atividades 4 e 12 e no Quadro 5 tem definição com fonte na Fundamentação, ou foi retirado da Metodologia.
**Depende de:** T02.

### T04 — Sustentar a afirmação sobre recursos específicos de provedor
**Tipo:** Referência | **Severidade:** Média | **Critério:** Fundamentação 4.2 | **Pontos:** −0,15 | **Esforço:** M
**Localização:** `2-fundamentacao-teorica.tex:127-131` (convenção sobre fontes) e `:297-305` (limite da abstração); `3-metodologia.tex:160-166` (atividade 1) e Seção do *Benchmark* 1.
**Evidência:** a revisão aponta que a abertura do capítulo diz que fonte não revisada por pares serve "nunca para sustentar afirmação empírica", mas "aplicações em produção costumam depender de recursos desse tipo" se apoia em um único relato da Thoughtworks e motiva um fator inteiro do *Benchmark* 1.
**Problema:** o texto descumpre a própria convenção sobre fontes, e um fator do experimento nasce de uma única fonte de literatura cinzenta; "relatos de prática" está no plural com uma só citação.
**Como resolver:**
1. Buscar estudo revisado por pares sobre dependência de recursos específicos de provedor de LLM ou sobre limites de bibliotecas de abstração (as *strings* A2 e A7 do Apêndice A são ponto de partida).
2. Se não houver, reescrever a frase como observação do relato ("um relato de prática descreve…"), no singular, e apresentar o cenário com recurso específico como exploratório.
3. Ajustar a convenção da abertura do Capítulo 3 para incluir o relato de prática entre as exceções rotuladas, com o papel que ele tem.
**Critério de aceite:** nenhuma afirmação empírica do texto depende só de fonte não revisada por pares sem estar rotulada como tal e limitada ao que a fonte diz; a convenção da abertura do Capítulo 3 é coerente com o uso feito do relato.
**Depende de:** A31 (o cenário ainda aguarda o orientador).

### T05 — Recompilar o PDF e corrigir a lista de siglas e o sumário
**Tipo:** Formatação | **Severidade:** Média | **Critério:** Formatação 7.1 (lista de siglas, sumário e PDF desatualizado) | **Pontos:** −0,15 | **Esforço:** P
**Localização:** `documento.pdf` (p. 4 e p. 6-7); `3-metodologia.tex:577-623` (quatro `\paragraph` das ameaças); `apendice-delimitacao.tex:20-97` (seis `\paragraph`); `Makefile` (passo `makeglossaries`).
**Evidência:** a revisão registra que, no PDF de 15/11, a Lista de Abreviaturas e Siglas sai em branco (p. 4), o sumário lista "4.5.0.0.1 Validade interna" e "B.0.0.0.1 Responsabilidade 1", e o PDF é anterior aos dois últimos commits.
**Problema:** o PDF do repositório não corresponde ao texto atual e tem dois defeitos visíveis nos elementos pré-textuais. As três referências novas de 16/11 ainda não aparecem na lista.
**Como resolver:**
1. Compilar com a sequência do `Makefile` (inclui `makeglossaries`) ou no Overleaf e conferir que as 12 siglas aparecem.
2. Tirar os parágrafos do sumário: trocar `\paragraph{…}` por texto em negrito no início do parágrafo, ou limitar a profundidade do sumário à subseção.
3. Conferir no PDF novo que não há `??`, que as referências de 16/11 entraram e que os quadros cabem na página.
**Critério de aceite:** o PDF versionado é posterior ao último commit de texto; a lista de siglas traz as 12 entradas; o sumário não tem entrada com numeração de cinco níveis; não há referência cruzada nem citação indefinida.
**Depende de:** —

### T06 — Dar métrica-alvo e faixas de exemplo ao critério de decisão
**Tipo:** Conteúdo insuficiente | **Severidade:** Média | **Critério:** Metodologia 5.5 (critério de decisão) | **Pontos:** −0,10 | **Esforço:** M
**Localização:** `2-fundamentacao-teorica.tex`, Seção 3.6.3; `3-metodologia.tex:289-298` (atividade 4) e Seção "Confronto dos resultados" (atividade 13).
**Evidência:** a revisão aponta que o critério de decisão não traz valores de exemplo nem diz sobre qual das cinco métricas primárias do *Benchmark* 1 incide a "redução mínima".
**Problema:** a rubrica aceita critério ainda indefinido desde que haja exemplos ou possibilidades. Sem métrica-alvo, o leitor não sabe o que conta como redução do custo de substituição.
**Como resolver:**
1. Dizer qual métrica (ou combinação) do Quadro 4 representa a redução do custo de substituição no critério, e como as demais entram (condição, desempate ou só relato).
2. Dizer se o "acréscimo máximo de energia" incide sobre a energia medida na GPU, sobre o limite superior do custo direto ou sobre os dois.
3. Dar faixas ilustrativas para os dois limites, marcadas como exemplo, a fixar na atividade 4.
4. Registrar na A30.
**Critério de aceite:** a atividade 4 nomeia a métrica de cada dimensão do critério e traz ao menos um exemplo numérico de cada limite, rotulado como ilustrativo.
**Depende de:** T01, A30.

### T07 — Rever o plano alternativo da atividade 10
**Tipo:** Coerência interna | **Severidade:** Média | **Critério:** Metodologia 5.1 (parte do plano alternativo); Coerência interna, item 3 | **Pontos:** −0,10 | **Esforço:** M
**Localização:** `3-metodologia.tex:497-508` (atividade 10) e `:300-303` (terceiro protocolo, atividade 4); `1-introducao.tex:194-200` (Justificativa).
**Evidência:** a revisão aponta que o plano alternativo troca o *Benchmark* 2 por um *benchmark* de recuperação de falhas, atributo que a Seção 1.3 declara fora da avaliação.
**Problema:** se a contingência for acionada, o trabalho passa a avaliar algo que a Introdução exclui e deixa de responder ao título e aos objetivos (d) e (e).
**Como resolver:**
1. Avaliar uma contingência que preserve a dimensão energética: matriz reduzida (menos repetições ou um só nível), modelo menor ou coleta em janela não exclusiva declarada como amostra degradada.
2. Se a recuperação de falhas for mantida como último recurso, dizer na Justificativa que esse atributo pode entrar por contingência e quais objetivos seriam reescritos.
3. Ajustar a atividade 4 quanto ao terceiro protocolo.
**Critério de aceite:** a contingência da atividade 10 ou preserva os objetivos (d) e (e) em forma reduzida, ou a Justificativa e a atividade 10 dizem a mesma coisa sobre o que muda no escopo.
**Depende de:** T01.

### T08 — Fixar a ordem dos adaptadores para não contaminar o *Benchmark* 1
**Tipo:** Método | **Severidade:** Média | **Critério:** Metodologia 5.3 (risco dos adaptadores) | **Pontos:** −0,10 | **Esforço:** P
**Localização:** `3-metodologia.tex:206-209` (atividade 2), `:311-313` (atividade 5), atividade 7 e parágrafo de validade interna.
**Evidência:** a revisão aponta um risco não listado nas ameaças: se o servidor local for compatível com a OpenAI, o adaptador do modelo local, escrito na atividade 5, antecipa o código da troca medida na atividade 7.
**Problema:** a troca medida iria da Anthropic para a OpenAI com parte do código do destino já escrito nas duas versões, o que reduz artificialmente o custo de substituição.
**Como resolver:**
1. Escolher uma das saídas: escrever o adaptador do modelo local só depois do *Benchmark* 1; usar no servidor local uma interface que não seja a da OpenAI; ou manter a ordem e contar à parte o código reaproveitado.
2. Registrar a saída na atividade 5 ou na 7 e na política de implementação da atividade 4.
3. Acrescentar a ameaça ao parágrafo de validade interna.
**Critério de aceite:** o texto diz quando o adaptador do modelo local é escrito em relação à troca medida e como o código reaproveitado é contado; a ameaça consta da Seção de ameaças à validade.
**Depende de:** A29 (pilha de inferência).

### T09 — Indicar tecnologias candidatas e o conjunto de requisições
**Tipo:** Conteúdo insuficiente | **Severidade:** Média | **Critério:** Metodologia 5.3 (pilha e carga de trabalho) | **Pontos:** −0,10 | **Esforço:** M
**Localização:** `3-metodologia.tex:142-209` (atividades 1 e 2) e Seção do *Benchmark* 2.
**Evidência:** a revisão registra que linguagem, *framework*, servidor de inferência, máquina da aplicação e o conjunto de requisições ficam para as atividades 1 e 2.
**Problema:** o projeto traz critérios de escolha, mas nenhum candidato para a maior parte da pilha, e não diz quantas requisições distintas compõem cada nível do *Benchmark* 2.
**Como resolver:**
1. Nomear, em cada item da atividade 2, o candidato preferido e a alternativa (linguagem, *framework*, servidor de inferência), marcados como a confirmar.
2. Descrever a máquina da aplicação (processador e a potência máxima usada no limite superior).
3. Dizer se cada nível do *Benchmark* 2 repete uma única requisição ou um conjunto, e de que tamanho.
**Critério de aceite:** cada item da pilha tem ao menos um candidato nomeado; a máquina da aplicação está descrita; o número de requisições distintas por nível está declarado.
**Depende de:** A29.

### T10 — Dar fonte às duas afirmações sem citação da Introdução
**Tipo:** Referência | **Severidade:** Média | **Critério:** Introdução 1.2 | **Pontos:** −0,10 | **Esforço:** M
**Localização:** `1-introducao.tex:41-44` ("essa incorporação costuma ocorrer da forma mais direta possível"), `:141-143` ("o benefício mais alegado da camada") e `:191-192` ("o benefício mais associado à camada").
**Evidência:** a revisão aponta que as duas afirmações não têm fonte e que o próprio texto admite que os números da Menlo "não isolam a causa".
**Problema:** o problema prático se apoia em afirmações de frequência sem evidência; a banca pode pedir a fonte.
**Como resolver:**
1. Procurar fonte para a prática de integração direta ao SDK (estudos empíricos de aplicações com LLM; a *string* A7 do Apêndice A cobre o tema).
2. Citar, para "benefício mais alegado", os trabalhos que o alegam (Bucaioni et al., Kandogan et al., Morais et al. já estão no capítulo 2).
3. Onde não houver fonte, trocar a afirmação de frequência por premissa declarada.
**Critério de aceite:** cada uma das três frases tem citação ou está redigida como premissa do autor.
**Depende de:** —

### T11 — Justificar a energia como o preço relevante da camada
**Tipo:** Coesão/argumentação | **Severidade:** Média | **Critério:** Introdução 1.4 | **Pontos:** −0,10 | **Esforço:** P
**Localização:** `1-introducao.tex:112-126` (estimativa de 1%) e `:168-178` (Justificativa, ponto de vista prático).
**Evidência:** a revisão aponta que o lado energético se apoia em números agregados da IEA, enquanto a estimativa do próprio autor prevê acréscimo "inferior a 1%" por requisição, e que falta dizer por que energia, e não latência ou custo financeiro.
**Problema:** a relevância da dimensão energética para desenvolvedores e arquitetos é declarada, não demonstrada, e a estimativa do próprio texto a enfraquece.
**Como resolver:**
1. Acrescentar à Justificativa duas ou três frases sobre a escolha da energia: o que ela mostra que a latência não mostra (a separação entre duração e potência já prevista) e por que um resultado nulo também informa a decisão.
2. Ligar a escolha ao volume de uso e aos fluxos agênticos, onde o texto supõe efeito maior.
**Critério de aceite:** a Seção 1.3 responde, em texto, por que a energia foi escolhida como custo e o que o público-alvo ganha se o efeito medido for desprezível.
**Depende de:** T01.

### T12 — Ajustes pontuais de forma: referências, "multiagente" e Quadro 1
**Tipo:** Formatação | **Severidade:** Média | **Critério:** Formatação 7.1 (referências, grafia e quadro) | **Pontos:** −0,10 | **Esforço:** P
**Localização:** `referencias.bib` (entradas `barros2026` e `matinpour2026`); `1-introducao.tex:49` ("multiagentes"); `trabalhos-relacionados.tex:175-177` (cabeçalho e colunas do Quadro 1).
**Evidência:** a revisão cita "multiagentes" (Seção 1.1) contra "multiagente" (Seção 3.1), "GOMES DE B. FILHO, B." e "Jafari Kaleibar" fora do padrão na lista de referências, e palavras quebradas no Quadro 1 ("substitui-ção", "fra-meworks", "topo-logias").
**Problema:** inconsistências pequenas, visíveis no PDF, que somam na nota de formatação.
**Como resolver:**
1. Padronizar os dois nomes no `.bib` para que saiam em maiúsculas como os demais (fecha a parte de forma da A06).
2. Uniformizar "multiagente" no texto.
3. Alargar as colunas estreitas do Quadro 1 ou encurtar os rótulos, para que nenhuma palavra seja partida.
**Critério de aceite:** no PDF, todos os sobrenomes da lista de referências seguem o mesmo padrão; há uma só grafia de "multiagente"; nenhuma célula do Quadro 1 tem palavra hifenizada no meio.
**Depende de:** A06 (forma do nome do autor).

### T13 — Fechar a redação do objetivo (a)
**Tipo:** Clareza/precisão | **Severidade:** Baixa | **Critério:** Objetivos 3.2 (parte do objetivo a) | **Pontos:** −0,05 | **Esforço:** P
**Localização:** `1-introducao.tex:249-251`; `apendice-delimitacao.tex:15-18`.
**Evidência:** a revisão aponta que (a) diz delimitar as responsabilidades "com base em padrões arquiteturais publicados", que a Seção 3.4.1 afirma que "a lista não vem da literatura" e que o Apêndice B já declara o objetivo atendido.
**Problema:** o objetivo atribui à literatura uma lista que é do autor e que o próprio projeto já delimitou. É o mesmo ponto do passo 3 da VC T02.
**Como resolver:**
1. Levar ao orientador uma redação em que a lista é do autor e é confrontada com padrões publicados (por exemplo, "confrontando as suas responsabilidades com padrões arquiteturais publicados").
2. Mudar o Apêndice B junto, na frase que repete a expressão.
3. Marcar a VC T02 como fechada.
**Critério de aceite:** o objetivo (a), a Seção 3.4.1 e o Apêndice B dizem a mesma coisa sobre a origem da lista de responsabilidades.
**Depende de:** VC T02 (decisão do orientador).

### T14 — Alinhar "hipótese a ser testada" à análise descritiva do *Benchmark* 1
**Tipo:** Coerência interna | **Severidade:** Baixa | **Critério:** Coerência interna, item 4 | **Pontos:** 0 | **Esforço:** P
**Localização:** `1-introducao.tex:159-163`; `3-metodologia.tex:415-423` (atividade 8).
**Evidência:** a revisão aponta que a Seção 1.2 chama de "a ser testada" uma hipótese cuja metade (custo de substituição) terá só comparação descritiva, com uma troca por célula.
**Problema:** "testar" sugere inferência estatística que o *Benchmark* 1 não faz.
**Como resolver:**
1. Na Seção 1.2, distinguir as duas metades: a do custo de substituição é examinada por comparação descritiva; a energética, por teste estatístico.
2. Ou trocar "a ser testada" por "a ser examinada".
**Critério de aceite:** a forma de verificação anunciada para cada metade da hipótese na Seção 1.2 coincide com a análise das atividades 8 e 12.
**Depende de:** —

### T15 — Rever a coluna "Manutenibilidade medida" do Quadro 1
**Tipo:** Coerência interna | **Severidade:** Baixa | **Critério:** Coerência interna, item 5 | **Pontos:** 0 | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:177` (cabeçalho) e `:203` (linha da proposta).
**Evidência:** a revisão aponta que a proposta marca "Manutenibilidade medida: Sim", que a Justificativa restringe o trabalho a duas dimensões e que a coluna conta de novo a medição do custo de substituição.
**Problema:** o quadro atribui à proposta uma dimensão que ela não mede em separado, o que infla a diferença em relação aos demais trabalhos.
**Como resolver:**
1. Escolher entre fundir as duas colunas em uma ("Modificabilidade ou custo de substituição medido") e marcar a proposta como "Só custo de substituição" na coluna de manutenibilidade.
2. Ajustar a frase da síntese que herda de Xiao et al. "a pergunta que confronta energia e manutenibilidade".
**Critério de aceite:** nenhuma célula da linha da proposta afirma medir algo que a Seção 1.3 exclui; o texto da síntese usa o mesmo termo do quadro.
**Depende de:** —

## Ressalvas sem perda (não convertidas)

Constam da revisão sob critério com veredito "Atende" ou como comentário sem efeito na nota; pela regra da skill, não geram task.

- Trabalhos Relacionados: Morais et al. (2026), o trabalho mais próximo quanto ao objetivo, foi julgado só pelo resumo.
- Trabalhos Relacionados: o Apêndice A não registra quantos trabalhos foram triados e excluídos em cada etapa.
- Cronograma: março concentra a versão D, o piloto e a verificação do orçamento de GPU, sem folga.
- Fora da nota: afirmações marcadas "A CONFERIR" nos comentários do fonte (Bass et al., Wohlin et al., Parnas, Sculley et al., Schwartz et al., Fernández et al.) e norma ISO/IEC 25010 registrada como não lida.
- Referências: 34 das 52 não foram verificadas na revisão; nenhuma foi dada como não localizada.

Premissas: severidade derivada das regras da skill `revisao-tcc1-para-tasks`; esforço estimado; pontos conforme a revisão. Onde a revisão deu uma perda única a um critério com correções independentes (3.2, 5.1, 5.3, 5.5 e 7.1), a divisão entre as tasks é minha: 3.2 em −0,10 (T01) e −0,05 (T13); 5.1 em −0,10 (T01) e −0,10 (T07); 5.3 em −0,10 (T08) e −0,10 (T09); 5.5 em −0,15 (T02) e −0,10 (T06); 7.1 em −0,15 (T05) e −0,10 (T12). A soma é 1,55, igual ao total perdido. A nota após as correções depende de nova avaliação.

## Situação em 18/11/2026

Aplicadas as tasks que não dependiam de decisão do autor nem do orientador. O PDF foi recompilado nesta máquina com `tectonic` (53 páginas, sem erro, sem `\ref` nem `\cite` indefinidos) e as páginas alteradas foram conferidas na imagem renderizada. Correção da revisão: ela dizia não haver LaTeX nesta máquina, mas só procurou `pdflatex` e `latexmk`; o `tectonic` está instalado. O `documento.pdf` está no `.gitignore`, de modo que o critério de aceite da T05 ("PDF versionado") vale para o PDF local e para o do Overleaf, não para um arquivo no repositório.

| ID | Situação | O que foi feito / o que falta |
|---|---|---|
| T05 | Feita | Lista de siglas: o `tectonic` não executa o `makeglossaries`, e a lista saía em branco. Passou a ser gerada pelo próprio LaTeX (`\makenoidxglossaries` em `lib/preambulo.tex` e `\printnoidxglossary` em `lib/ufctex.sty`); as 12 siglas aparecem em ordem alfabética, e o resultado não depende mais da ferramenta de compilação. A lista de símbolos e o glossário, desativados, voltariam a exigir `\makeglossaries`. Sumário: os 10 `\paragraph` (4 das ameaças à validade, 6 do Apêndice B) viraram negrito no início do parágrafo, e as entradas "4.5.0.0.n" e "B.0.0.0.n" saíram. **Conferir no Overleaf** que a lista de siglas compila igual. |
| T10 | Feita | Introdução 1.1: "costuma ocorrer da forma mais direta possível" virou "a forma mais direta de fazer essa incorporação é…; é essa a integração que serve de termo de comparação". 1.2: "o benefício mais alegado da camada" virou "o benefício que as propostas de camada lhe atribuem (KANDOGAN et al., 2025; MORAIS et al., 2026)", com base no que o Cap. 2 já diz desses trabalhos. 1.3: "o benefício mais associado à camada" virou o mesmo, com remissão à Seção 1.2. |
| T14 | Feita | Seção 1.2: saiu "a ser testada"; o texto diz que a parte do custo de substituição é examinada por comparação descritiva (uma troca por versão e cenário) e a energética por teste estatístico sobre medições repetidas, com remissão ao Cap. 4. Se a T01 mudar o que é medido em energia, rever esta frase. |
| T15 | Feita | Quadro 1, linha da proposta, coluna "Manutenibilidade medida": "Sim" → "Em parte". Nota abaixo do quadro explica que a proposta mede só a modificabilidade, pelo custo de substituição (remissão à Seção 3.2.1). Na síntese, a herança de Xiao et al. passou a "a pergunta que confronta, na mesma decisão arquitetural, a energia e um atributo de manutenibilidade". |
| T12 | Parcial | Feito: "multiagentes" → "multiagente" (única ocorrência, Seção 1.1); sobrenome de Matinpour et al. sai "JAFARI KALEIBAR, F." (o estilo `abntex2-alf` toma só a última palavra como sobrenome, por isso as chaves com maiúsculas, como em Barros et al.); Quadro 1 sem palavra partida (`\tabcolsep` de 3 pt, colunas redimensionadas, "(desempenho)" em `\mbox`). Falta: a forma de "GOMES DE B. FILHO, B." em Barros et al., que depende da A06. |

Fora das tasks, visto na compilação: todos os quadros do documento transbordam a margem em 5 a 7,5 pt (aviso `Overfull \hbox` no invólucro `\UFCqua` do template). Já ocorria antes destas edições; não foi tratado.

Abertas: T01, T02, T03, T04, T06, T07, T08, T09, T11 e T13 (dependem de decisão do autor ou do orientador, ou de A11, A29, A30, A31 e VC T02) e a parte da T12 que depende da A06.
