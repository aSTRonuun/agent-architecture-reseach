# Tasks de correção — validação cruzada (Introdução, Trabalhos Relacionados, Fundamentação Teórica e Metodologia)
Origem: `../validacao-inconsistencias-v1.md` (10/11/2026, commit `ab5b06d`). Não é revisão pela rubrica: nenhuma task tem pontos atribuídos.
Total: 19 tasks (0 críticas, 0 altas, 7 médias, 12 baixas)

Só entram aqui os achados novos e as partes dos achados antigos que os backlogs existentes não cobrem. O achado 1 (fronteira da medição de energia) e o achado 12 (bases de busca) já têm task e não foram duplicados: ver Fund T01, TR T05 e TR T03.

Abreviações: "Fund Tnn", "TR Tnn" e "Intro Tnn" são tasks dos backlogs em `entregas/fundamentacao`, `entregas/trabalhos-relacionados` e `entregas/introduction`. "Ann" são itens do `context/action_log.md`.

## Visão geral

| ID | Título | Tipo | Severidade | Esforço | Depende de | Achado |
|---|---|---|---|---|---|---|
| T01 | Declarar o que difere entre as versões H e D na orquestração | Coerência interna | Média | G | A07, A19, Fund T01 | 2 |
| T02 | Alinhar a origem das responsabilidades da camada | Coerência interna | Média | P | — | 3 |
| T03 | Igualar a definição e as métricas do custo de substituição | Coerência interna | Média | M | — | 4 |
| T04 | Dizer o que a versão D executa das responsabilidades 3 a 5 | Coerência interna | Média | M | T01 | 5 |
| T05 | Prever na Metodologia a seção do critério de decisão | Conteúdo ausente | Média | M | Fund T02 | 6 |
| T06 | Descrever a aplicação, os casos de uso e a interface do modelo local | Conteúdo ausente | Média | G | A29 | 6 |
| T07 | Unificar o nome do construto medido no *Benchmark* 1 | Clareza/precisão | Média | M | T03 | 7 |
| T08 | Registrar a ameaça externa de modelo e *hardware* | Conteúdo ausente | Baixa | P | — | 6 |
| T09 | Corrigir a atribuição da posição do *harness* à literatura | Coerência interna | Baixa | P | — | 8 |
| T10 | Resolver o uso de "agêntica" para agente único | Clareza/precisão | Baixa | P | — | 9 |
| T11 | Tirar Vellaisamy et al. dos "estudos de energia" no TR | Coerência interna | Baixa | P | TR T07 | 10 |
| T12 | Indicar coautoria de Barros et al. na Introdução e na Fundamentação | Redação | Baixa | P | TR T15 | 11 |
| T13 | Dizer se o servidor institucional conta como provedor | Clareza/precisão | Baixa | P | T06 | 13 |
| T14 | Igualar a lista de responsabilidades não avaliadas | Coerência interna | Baixa | P | T04 | 14 |
| T15 | Ajustes pontuais em Trabalhos Relacionados | Coesão/argumentação | Baixa | P | — | 15 |
| T16 | Ajustes pontuais na Fundamentação | Coesão/argumentação | Baixa | P | — | 3, 15 |
| T17 | Conferir "em seis meses" no relatório da Menlo | Referência | Baixa | P | — | 15 |
| T18 | Atualizar comentários de cabeçalho desatualizados | Formatação | Baixa | P | — | 15 |
| T19 | Reduzir os contrastes "X, e não Y" e uniformizar os travessões | Redação | Baixa | M | — | Estilo |

Ordem sugerida: T01 primeiro, porque T04 e T14 dependem dela e ela condiciona a Fund T01; depois T03 e T07, que são independentes das decisões pendentes; o restante em qualquer ordem.

## Situação em 10/11/2026

Aplicadas no texto as tasks que não dependiam de decisão. O PDF não foi compilado depois das edições (não há LaTeX neste ambiente).

| ID | Situação | O que foi feito / o que falta |
|---|---|---|
| T02 | Parcial | Passos 1 e 2 feitos no TR (`:95-96` e síntese). Falta o passo 3: redação do objetivo (a), com o orientador. |
| T03 | Feita | Decisão do autor (10/11/2026): manter os 3 componentes e mapear. Parágrafo novo na Metodologia, antes da tabela do *Benchmark* 1, liga as seis métricas aos três componentes e deixa o tempo como secundária, fora da definição. Fundamentação `:533` ajustada. |
| T17 | Encerrada sem alteração | A verificação anterior (`entregas/introduction/revision/t14-verificacao-numeros-e-fontes.md`, linha 11) registra que o relatório diz "more than doubled in just six months" com as mesmas datas. O texto segue a fonte; o apontamento da validação não procede. |
| T08 | Feita | Marcador de validade externa da Metodologia ampliado. |
| T09 | Feita | Frase da Introdução reescrita; "é um *middleware*" suavizado na Fundamentação. |
| T11 | Feita | Abertura da seção e síntese do TR separadas em latência e energia. |
| T12 | Feita | Coautoria indicada na Introdução e na Fundamentação. |
| T13 | Parcial | Passo 1 feito ("provedores comerciais"). O passo 2 depende da T06. |
| T15 | Parcial | Itens (a) e (b) feitos. Falta (c), a célula de Barros et al. no quadro, que pede julgamento sobre o critério da coluna. |
| T16 | Parcial | Itens (a), (b) e (c) feitos. Falta (d), o *Tool/agent registry* no Quadro, que pede escolha entre marcar e retirar. |
| T18 | Feita | Comentários renumerados para Cap. 3 / 3.x; nota do quadro "não produzido" removida. |
| T19 | Feita | Contrastes ", e não ..." reduzidos de 43 para 29 (Introdução 10→6, TR 11→8, Fundamentação 18→11, Metodologia 4→4, contando um novo do parágrafo da T03); os que ficaram delimitam escopo ou dizem o que a fonte cobre. Travessões em inciso da Introdução: 7→0. "Mais próximo" no TR: 5→2. Duas frases foram cortadas por repetirem ressalva já feita (Fundamentação, OpenTelemetry; Introdução, "material promocional"). |
| TR T07 | Feita | Fundamentação diz que Vellaisamy et al. decompõem tempo, transposto aqui para energia. |
| TR T08 | Feita | `Mo, David` → `Mo, Di` no `.bib`. |
| TR T15 | Feita | Coautoria indicada no TR. |

Abertas, por dependerem de decisão, de fonte ou de reescrita mais ampla: T01, T04, T05, T06, T07, T10, T14.

## Detalhamento

### T01 — Declarar o que difere entre as versões H e D na orquestração
**Tipo:** Coerência interna | **Severidade:** Média | **Esforço:** G
**Localização:** `1-introducao.tex:127-129`; `trabalhos-relacionados.tex:176-177` e `:294-295`; `2-fundamentacao-teorica.tex:527-528`; `3-metodologia.tex:126-127`
**Evidência:** a Introdução diz que a camada "pode alterar o número de chamadas e o tamanho do contexto enviado ao modelo". O TR diz que a comparação mantém "fixa a orquestração" e que "a única diferença entre as duas versões da aplicação" é a presença da camada.
**Problema:** as duas afirmações não cabem juntas sem explicação. Com chamadas e contexto idênticos, o efeito indireto previsto na Introdução não existe por construção; com chamadas e contexto diferentes, a diferença medida mistura a camada com decisões de orquestração, que é a crítica feita a Matinpour et al. e Tripathy et al.
**Como resolver:**
1. Fechar a política da versão D (A07) e o critério de paridade (A19): decidir se H e D enviam ao modelo as mesmas chamadas, com o mesmo contexto.
2. Escrever a decisão na Metodologia (subseção da versão D).
3. Ajustar a frase da Introdução ou as duas frases do TR para a decisão tomada.
4. Conferir a consequência para a Fund T01: se chamadas e contexto forem idênticos e a medição for só de GPU, dizer o que se espera que a medição capture.
**Critério de aceite:** Introdução, TR e Metodologia descrevem a mesma relação entre H e D quanto a número de chamadas e tamanho do contexto.
**Depende de:** A07, A19, Fund T01

### T02 — Alinhar a origem das responsabilidades da camada
**Tipo:** Coerência interna | **Severidade:** Média | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:95-96` e `:388-389`; `1-introducao.tex:263-264`; `2-fundamentacao-teorica.tex:340`, `:375-378`
**Evidência:** o TR diz que o trabalho herda "as responsabilidades da camada do catálogo" de Liu et al. e fala em correspondência "completa ou por analogia". A Fundamentação diz que "a lista não vem da literatura" e usa os graus parcial, analogia e nenhuma. O objetivo (a) fala em "padrões arquiteturais publicados".
**Problema:** o TR e o objetivo (a) afirmam mais do que a Fundamentação sustenta.
**Como resolver:**
1. No TR `:95-96`, trocar "completa ou por analogia" pelos graus da Fundamentação.
2. No TR `:388-389`, dizer que o catálogo serve de referência para confrontar as responsabilidades, e não de origem delas.
3. Avaliar com o orientador se o objetivo (a) deve dizer "com base na literatura" ou formulação equivalente, já que as responsabilidades 1 e 5 se apoiam em *middleware* e em documentação técnica.
**Critério de aceite:** nenhum trecho diz que a lista de responsabilidades vem do catálogo, e o termo "completa" não aparece para descrever a correspondência.
**Depende de:** —

### T03 — Igualar a definição e as métricas do custo de substituição
**Tipo:** Coerência interna | **Severidade:** Média | **Esforço:** M
**Localização:** `1-introducao.tex:161-165`; `2-fundamentacao-teorica.tex:200-206` e `:533`; `3-metodologia.tex:145-150`
**Evidência:** a definição lista três componentes (extensão do código alterado, pontos de dependência direta ao SDK, casos de uso que continuam funcionando). A tabela do *Benchmark* 1 lista seis métricas, cinco primárias, incluindo impacto estrutural, testes alterados ou quebrados e tempo.
**Problema:** o leitor não sabe se o construto tem três ou seis indicadores, nem quais entram no critério de decisão.
**Como resolver:**
1. Decidir quais métricas compõem o construto e quais são complementares.
2. Atualizar a definição (Introdução e Fundamentação) ou a tabela, para que listem a mesma coisa.
3. Na Fundamentação `:533`, trocar "métricas de estrutura de código" por uma formulação que inclua a métrica comportamental.
**Critério de aceite:** a definição e a tabela listam os mesmos indicadores primários, ou a definição diz explicitamente quais métricas da tabela são complementares.
**Depende de:** —

### T04 — Dizer o que a versão D executa das responsabilidades 3 a 5
**Tipo:** Coerência interna | **Severidade:** Média | **Esforço:** M
**Localização:** `2-fundamentacao-teorica.tex:455-460`; `1-introducao.tex:88-90`; `3-metodologia.tex:126-127`
**Evidência:** a Fundamentação diz que as responsabilidades 3, 4 e 5 "ficam fora da avaliação". A Introdução inclui "registro de eventos" no trabalho que a camada acrescenta a cada requisição.
**Problema:** se só a versão H gerencia contexto, trata falhas e registra eventos, a diferença H−D inclui a energia dessas funções, e não só a da indireção. O texto não diz o que a versão D faz.
**Como resolver:**
1. Decidir, junto com a T01, se a versão D implementa essas funções no código de negócio ou não as tem.
2. Escrever a decisão na Metodologia.
3. Na Fundamentação `:455-460`, dizer que as responsabilidades 3 a 5 não são avaliadas como atributos, mas que a energia delas está (ou não está) na diferença medida.
**Critério de aceite:** o texto diz o que a versão D executa e se a energia das responsabilidades 3 a 5 entra na diferença H−D.
**Depende de:** T01

### T05 — Prever na Metodologia a seção do critério de decisão
**Tipo:** Conteúdo ausente | **Severidade:** Média | **Esforço:** M
**Localização:** `3-metodologia.tex` (estrutura de seções); `1-introducao.tex:273-276`; `2-fundamentacao-teorica.tex:534-536`
**Evidência:** o objetivo (e) e a Fundamentação prometem um "critério de decisão definido antes da coleta de dados". O esqueleto da Metodologia tem Fase de solução, *Benchmark* 1, *Benchmark* 2, Ameaças e Base reaproveitada.
**Problema:** o objetivo (e) não tem atividade nem seção no capítulo que deveria atendê-lo.
**Como resolver:**
1. Criar uma seção para o confronto dos dois *benchmarks*, com o critério de decisão.
2. Preencher o critério com o resultado da Fund T02.
**Critério de aceite:** a Metodologia tem uma seção que atende ao objetivo (e) e enuncia o critério.
**Depende de:** Fund T02

### T06 — Descrever a aplicação, os casos de uso e a interface do modelo local
**Tipo:** Conteúdo ausente | **Severidade:** Média | **Esforço:** G
**Localização:** `3-metodologia.tex:16-21`, `:53`, `:123-127`
**Evidência:** nenhuma seção descreve a aplicação *web*, os seus casos de uso ou as ferramentas. O texto diz apenas que o conjunto de ferramentas será "pequeno e conhecido de antemão". Também não diz por qual interface as duas versões acessam o Qwen3.6.
**Problema:** a métrica "casos de uso que continuam funcionando" e a requisição agêntica dependem dessas definições. Pela skill `metodologia-tcc`, falta a atividade de requisitos e projeto da aplicação antes da implementação.
**Como resolver:**
1. Acrescentar à Fase de solução uma subseção sobre a aplicação: domínio, casos de uso, ferramentas e pontos de integração com o modelo.
2. Fechar o A29 e registrar a interface do modelo local.
3. Onde a decisão ainda não existir, deixar marcador explícito em vez de texto.
**Critério de aceite:** a Metodologia nomeia a aplicação, lista os casos de uso e as ferramentas e diz como o modelo local é acessado, ou marca cada item como pendente.
**Depende de:** A29

### T07 — Unificar o nome do construto medido no *Benchmark* 1
**Tipo:** Clareza/precisão | **Severidade:** Média | **Esforço:** M
**Localização:** `1-introducao.tex:155-156`, `:206`, `:214`; `trabalhos-relacionados.tex:242-243` e quadro; `3-metodologia.tex:130`, `:165`, `:126`, `:175`; referência em `2-fundamentacao-teorica.tex:172-180`
**Evidência:** o mesmo construto aparece como custo de substituição, substituibilidade, facilidade de trocar, esforço de troca, manutenibilidade e desacoplamento. A Fundamentação separa substituibilidade (do provedor, sob flexibilidade) de modificabilidade (da aplicação, sob manutenibilidade).
**Problema:** o *benchmark* se chama "Substituibilidade" e mede propriedades da aplicação; o TR chama a dimensão de "manutenibilidade".
**Como resolver:**
1. Escolher um termo para o construto ("custo de substituição do provedor" já é o do título) e usar os demais só com o sentido que a Fundamentação lhes dá.
2. Renomear o *Benchmark* 1 de acordo.
3. No TR `:242-243`, dizer de que forma a manutenibilidade de Xiao et al. se relaciona com o custo de substituição, em vez de chamá-la de "dimensão deste trabalho".
4. Fazer o mesmo para "custo energético" × "Eficiência energética" e para "equivalência funcional" × "paridade funcional" × "corretude".
**Critério de aceite:** cada um dos três construtos tem um único nome nos quatro capítulos, e os termos da ISO/IEC 25010 são usados com o sentido definido na Fundamentação.
**Depende de:** T03

### T08 — Registrar a ameaça externa de modelo e *hardware*
**Tipo:** Conteúdo ausente | **Severidade:** Baixa | **Esforço:** P
**Localização:** `3-metodologia.tex:189-190`; `1-introducao.tex:238-239`
**Evidência:** a Introdução diz que o limite de generalização a outros modelos, equipamentos e provedores em nuvem "é tratado como ameaça à validade externa na metodologia". O marcador de validade externa só cita o número de pontos de integração (A07).
**Problema:** a promessa da Introdução não está registrada no esqueleto.
**Como resolver:**
1. Acrescentar ao marcador de validade externa o item "um modelo e um *hardware*; sem provedores em nuvem".
**Critério de aceite:** o marcador (ou o texto) de validade externa cita o limite de modelo e *hardware*.
**Depende de:** —

### T09 — Corrigir a atribuição da posição do *harness* à literatura
**Tipo:** Coerência interna | **Severidade:** Baixa | **Esforço:** P
**Localização:** `1-introducao.tex:75-78`; `2-fundamentacao-teorica.tex:275-285`, `:288-290`; `3-metodologia.tex:44-47`
**Evidência:** a Introdução diz que a camada entre a aplicação e o provedor "passou a ser chamada de *harness*" na literatura. A Fundamentação diz que Rafique e Bindschaedler usam o termo para a camada que envolve o modelo e que a posição entre aplicação e provedor é acréscimo do autor.
**Problema:** a Introdução atribui à fonte o que a Fundamentação declara ser do autor.
**Como resolver:**
1. Reescrever a frase da Introdução para dizer que o termo vem da literatura sobre agentes e que este trabalho o aplica à camada entre aplicação e provedor.
2. Na Fundamentação `:288-290`, alinhar "é um *middleware*" com a formulação da Metodologia ("correspondência de propósito").
**Critério de aceite:** a Introdução não diz que a literatura chama de *harness* a camada entre aplicação e provedor.
**Depende de:** —

### T10 — Resolver o uso de "agêntica" para agente único
**Tipo:** Clareza/precisão | **Severidade:** Baixa | **Esforço:** P
**Localização:** `2-fundamentacao-teorica.tex:126-130` e `:150-153`; objetivos (d) e (e) em `1-introducao.tex:271-276`
**Evidência:** o trabalho adota a distinção de Sapkota et al., em que "IA agêntica" designa sistemas multiagente, fora do escopo, e usa "requisição agêntica" para o agente único com ciclo de ferramentas.
**Problema:** o adjetivo é o que a taxonomia adotada reserva ao que foi excluído. A Intro T07 tratou só o título.
**Como resolver:**
1. Decidir com o orientador: manter o termo e acrescentar, na definição operacional, uma frase dizendo que ele não remete à "IA agêntica" de Sapkota et al.; ou trocá-lo (por exemplo, "requisição com ferramentas").
**Critério de aceite:** a definição de requisição agêntica trata explicitamente da diferença em relação à "IA agêntica", ou o termo foi substituído em todo o texto.
**Depende de:** —

### T11 — Tirar Vellaisamy et al. dos "estudos de energia" no TR
**Tipo:** Coerência interna | **Severidade:** Baixa | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:257-260`, `:320-322`, quadro `:362`
**Evidência:** o quadro marca "Energia medida: Não (latência)". A abertura da seção e a síntese incluem o trabalho entre os que medem energia.
**Problema:** o capítulo se contradiz. A TR T07 corrige só a Fundamentação.
**Como resolver:**
1. Na abertura da seção, dizer que os estudos tratam de energia e de latência na pilha de inferência.
2. Na síntese, separar Vellaisamy et al. dos estudos de energia.
**Critério de aceite:** nenhum trecho do TR apresenta Vellaisamy et al. como medição de energia.
**Depende de:** TR T07 (fazer junto)

### T12 — Indicar coautoria de Barros et al. na Introdução e na Fundamentação
**Tipo:** Redação | **Severidade:** Baixa | **Esforço:** P
**Localização:** `1-introducao.tex:243`; `2-fundamentacao-teorica.tex:499`
**Evidência:** as duas frases dizem "empregado pelo autor". No `.bib`, o autor do TCC é o segundo de cinco autores.
**Problema:** a TR T15 corrige só a ocorrência do TR.
**Como resolver:**
1. Usar a mesma formulação da TR T15 nas duas ocorrências.
**Critério de aceite:** as três ocorrências indicam coautoria.
**Depende de:** TR T15 (fazer junto)

### T13 — Dizer se o servidor institucional conta como provedor
**Tipo:** Clareza/precisão | **Severidade:** Baixa | **Esforço:** P
**Localização:** `2-fundamentacao-teorica.tex:135`, `:324-325`; `1-introducao.tex:216-231`
**Evidência:** a Fundamentação fala nos "dois provedores usados neste trabalho"; a Introdução define três fontes de modelo.
**Problema:** o leitor não sabe se o modelo local é um terceiro provedor para a camada.
**Como resolver:**
1. Na Fundamentação `:135`, trocar por "dos dois provedores comerciais usados neste trabalho".
2. Na Introdução ou na Metodologia, dizer como o modelo local se encaixa na definição de provedor (depende da T06).
**Critério de aceite:** o texto diz quantas fontes de modelo a camada integra e qual é o papel de cada uma.
**Depende de:** T06

### T14 — Igualar a lista de responsabilidades não avaliadas
**Tipo:** Coerência interna | **Severidade:** Baixa | **Esforço:** P
**Localização:** `1-introducao.tex:210-212`; `2-fundamentacao-teorica.tex:458-460`
**Evidência:** a Introdução cita "a recuperação de falhas e a auditabilidade"; a Fundamentação cita as responsabilidades 3, 4 e 5 e remete à mesma seção da Introdução.
**Problema:** a remissão aponta para um trecho que não menciona a gestão de contexto e estado.
**Como resolver:**
1. Incluir a gestão de contexto e estado na frase da Introdução, ou retirar a responsabilidade 3 da frase da Fundamentação, conforme a decisão da T04.
**Critério de aceite:** as duas frases citam as mesmas responsabilidades.
**Depende de:** T04

### T15 — Ajustes pontuais em Trabalhos Relacionados
**Tipo:** Coesão/argumentação | **Severidade:** Baixa | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:77-78`, `:311-322`, `:370`
**Evidência:** (a) "quatro grupos, um para cada parte da pergunta de pesquisa", e a pergunta tem duas partes; (b) Lin et al. está no quadro e não no parágrafo de síntese; (c) na coluna "Compara com e sem a decisão", Barros et al. recebe "Sim", embora o texto o agrupe com os trabalhos que comparam configurações inteiras.
**Problema:** pequenas divergências entre o texto e o quadro.
**Como resolver:**
1. Reescrever (a) sem ligar os quatro grupos às partes da pergunta.
2. Incluir Lin et al. no parágrafo de síntese.
3. Conferir o critério da coluna para Barros et al. e ajustar a célula ou o texto. Fazer junto com a TR T13, que já mexe no quadro.
**Critério de aceite:** o parágrafo de síntese cobre todos os grupos do quadro, e a célula de Barros et al. é coerente com `:291-293`.
**Depende de:** —

### T16 — Ajustes pontuais na Fundamentação
**Tipo:** Coesão/argumentação | **Severidade:** Baixa | **Esforço:** P
**Localização:** `2-fundamentacao-teorica.tex:396-404`, `:409`, `:422-428`, `:450`
**Evidência:** (a) "só a segunda tem correspondência parcial direta", quando o Quadro marca a 2 e a 3 como "Parcial" e a escala não tem "direta"; (b) Sedghpour et al. é citado no Quadro e na síntese e só é descrito na Metodologia; (c) "O exame de cada correspondência [...] pertence ao projeto da camada", sem remissão; (d) o *Tool/agent registry* está listado para a responsabilidade 2, e a Metodologia diz que o problema dele "pouco se coloca" aqui.
**Problema:** na entrega parcial, sem a Metodologia, os itens (b) e (c) ficam sem apoio no texto.
**Como resolver:**
1. Reescrever a frase de (a) com os termos da escala.
2. Acrescentar uma oração sobre Sedghpour et al. em `:430-434`, com o que a Metodologia já diz deles.
3. Em (c), usar a mesma remissão condicional da abertura do capítulo (`\ifentregaparcial`).
4. Em (d), marcar o padrão como de aplicação limitada, ou retirá-lo do Quadro.
**Critério de aceite:** a frase de (a) usa só os três graus; toda fonte do Quadro é descrita no capítulo; a remissão de (c) existe.
**Depende de:** —

### T17 — Conferir "em seis meses" no relatório da Menlo
**Tipo:** Referência | **Severidade:** Baixa | **Esforço:** P
**Localização:** `1-introducao.tex:37-38`
**Evidência:** o texto diz "em seis meses, de 3,5 bilhões de dólares em novembro de 2024 para 8,4 bilhões em meados de 2025". O intervalo descrito é de cerca de sete a oito meses. A fonte não foi aberta na validação.
**Problema:** o prazo e as datas da mesma frase não batem entre si.
**Como resolver:**
1. Conferir no relatório as datas e a expressão usada.
2. Ajustar o prazo ou as datas.
**Critério de aceite:** o prazo e as datas da frase são coerentes e batem com a fonte.
**Depende de:** —

### T18 — Atualizar comentários de cabeçalho desatualizados
**Tipo:** Formatação | **Severidade:** Baixa | **Esforço:** P
**Localização:** `2-fundamentacao-teorica.tex:10-17`, `:79-80`; `3-metodologia.tex:22-24`; `lib/preambulo.tex:105`
**Evidência:** a Fundamentação passou a ser o Capítulo 3, e os comentários ainda a numeram como 2.x ou "Cap. 2". Um comentário diz que o quadro de síntese "ainda não foi produzido", e ele existe (`qua:conceitos-uso`).
**Problema:** não afeta o PDF, mas confunde quem mantém os arquivos e as tasks que citam seções por número.
**Como resolver:**
1. Renumerar as referências dos comentários para 3.x e "Cap. 3".
2. Remover a nota sobre o quadro não produzido.
**Critério de aceite:** nenhum comentário se refere à Fundamentação como Capítulo 2.
**Depende de:** —

### T19 — Reduzir os contrastes "X, e não Y" e uniformizar os travessões
**Tipo:** Redação | **Severidade:** Baixa | **Esforço:** M
**Localização:** os quatro capítulos; travessões em `1-introducao.tex`
**Evidência:** 43 ocorrências de ", e não ..." (10 na Introdução, 11 no TR, 18 na Fundamentação, 4 na Metodologia). Sete travessões em incisos na Introdução e nenhum nos demais capítulos. Cinco trabalhos do TR apresentados como "mais próximo" (`:90`, `:121`, `:194`, `:241`, `:269`).
**Problema:** a repetição do mesmo molde de frase pesa na leitura. Parte das ocorrências delimita escopo e deve ficar.
**Como resolver:**
1. Manter os contrastes em que as duas metades informam (escopo, o que a fonte cobre e não cobre).
2. Reescrever de forma direta aqueles em que a metade negada não foi afirmada por ninguém (exemplo: `1-introducao.tex:192`).
3. Trocar os travessões da Introdução por vírgulas ou parênteses.
4. No TR, variar a abertura dos parágrafos que usam "mais próximo".
5. Fazer junto com a Fund T05, que trata das ressalvas de processo.
**Critério de aceite:** a Introdução não usa travessão em inciso, e cada ", e não" restante delimita escopo ou corrige uma leitura plausível.
**Depende de:** —

## Fora das tasks

- Faltam na Metodologia o diagrama de atividades, o cronograma e a redação das seções marcadas com `\pendencia`. Não viraram task porque são a redação do capítulo em si, e não correção.
- O cabeçalho da Fundamentação lista fontes "não lidas na íntegra" e afirmações "a conferir" (`:32-36`, `:60-70`). A validação não conseguiu saber se foram fechadas.
- `referencias.bib:142` continua com `Mo, David` (TR T08, aberta).

Premissas: severidade "Média" para os achados classificados como importantes no relatório e "Baixa" para os menores. Esforço estimado. Nenhuma fonte foi aberta para gerar estas tasks; as evidências são trechos do próprio texto.
