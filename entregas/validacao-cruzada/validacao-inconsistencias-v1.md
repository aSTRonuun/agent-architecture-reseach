# Validação cruzada: Introdução, Trabalhos Relacionados, Fundamentação Teórica e Metodologia

Data: 10/11/2026. Branch: `revisao-trabalhos-relacionados-v1` (commit `ab5b06d`).

## Escopo e método

Arquivos lidos na íntegra: `2-textuais/1-introducao.tex`, `trabalhos-relacionados.tex`, `2-fundamentacao-teorica.tex`, `3-metodologia.tex`, além de `documento.tex`, da lista de siglas e dos backlogs já existentes em `entregas/`.

O que foi feito:

- leitura cruzada das quatro seções, procurando afirmações que se contradizem ou que usam termos diferentes para a mesma coisa;
- conferência mecânica de citações, rótulos (`\label`/`\ref`) e siglas;
- conferência da aritmética dos números citados (só a conta, não a fonte);
- aplicação dos checklists das skills `trabalhos-relacionados-tcc`, `fundamentacao-teorica-tcc` e `metodologia-tcc`, e diagnóstico de estilo com a skill `humanizer`.

O que **não** foi feito:

- nenhum artigo citado foi aberto. Nada aqui confirma ou desmente o que o texto atribui às fontes;
- o PDF não foi compilado. Paginação, quadros e sumário não foram vistos;
- nenhum arquivo `.tex` foi alterado. O diagnóstico de estilo é só contagem e apontamento, sem reescrita.

Cada achado está marcado como **novo** ou **já no backlog** (com o ID da task existente). As linhas citadas são as dos arquivos no commit acima.

## Resumo

| # | Achado | Seções | Severidade | Situação |
|---|---|---|---|---|
| 1 | O que a medição de energia alcança (GPU) não coincide com o que os objetivos prometem (custo da camada) | Intro, TR, Fund, Metod | Crítica | Já no backlog (Fund T01, TR T05), aberto |
| 2 | "Orquestração fixa" (TR) contra "a camada pode alterar chamadas e contexto" (Intro) | Intro, TR, Fund | Importante | Novo |
| 3 | Responsabilidades da camada: "herdadas do catálogo" (TR) contra "a lista não vem da literatura" (Fund) | TR, Fund, Intro | Importante | Novo |
| 4 | Definição do custo de substituição tem 3 componentes; a tabela da Metodologia tem 6 métricas | Intro, Fund, Metod | Importante | Novo |
| 5 | Responsabilidades 3 a 5 "fora da avaliação", mas dentro da energia medida | Intro, Fund | Importante | Novo |
| 6 | Objetivo (e) e a ameaça externa prometida não têm lugar no esqueleto da Metodologia | Intro, Fund, Metod | Importante | Novo |
| 7 | Vários nomes para o mesmo construto (substituibilidade, manutenibilidade, esforço de troca...) | Todas | Importante | Novo |
| 8 | Origem do termo *harness*: a Introdução atribui à literatura o que a Fundamentação diz ser acréscimo do autor | Intro, Fund | Menor | Novo |
| 9 | "Agêntica" usada para agente único, embora a taxonomia adotada reserve o termo a sistemas multiagente | Intro, Fund | Menor | Parcial (Intro T07 tratou só o título) |
| 10 | Vellaisamy et al. chamados de "estudo de energia" no texto e "Não (latência)" no quadro | TR, Fund | Menor | Parcial (TR T07 cobre só a Fund) |
| 11 | "Trabalho anterior do autor" em três capítulos; o `.bib` mostra coautoria | Intro, TR, Fund | Menor | Parcial (TR T15 cobre só o TR) |
| 12 | Bases de busca diferentes na Introdução e no capítulo | Intro, TR | Menor | Já no backlog (TR T03), aberto |
| 13 | "Dois provedores usados neste trabalho" contra três fontes de modelo | Intro, Fund | Menor | Novo |
| 14 | Introdução cita duas responsabilidades não avaliadas; a Fundamentação, três | Intro, Fund | Menor | Novo |
| 15 | Itens menores de redação, quadro e comentários desatualizados | Várias | Menor | Novo |

Conferências mecânicas: sem erros (seção "O que está consistente").

## Achados

### 1. Fronteira da medição de energia (crítica, já no backlog)

- Objetivo (d): "mensurar o custo energético que a camada de *harness* acrescenta" (`1-introducao.tex:271-272`). O título e o TR (`:383-385`) dizem o mesmo.
- A Introdução estima o trabalho próprio da camada na **CPU** (`:123-126`).
- A Fundamentação fundamenta só a telemetria de **GPU** por NVML (`2-fundamentacao-teorica.tex:498-507`), e a Metodologia prevê "NVML a 100 ms" (`3-metodologia.tex:178`).
- O item A11 do `context/action_log.md` segue aberto. A nota de 12/10/2026 registra que a aplicação e o *harness* rodariam na máquina do autor, e não no servidor medido.

Enquanto o A11 não for fechado, o instrumento descrito não mede o custo direto da camada. A justificativa da Introdução já usa a formulação mais estreita ("efeito da camada sobre a energia de inferência", `:235-236`), mas o objetivo (d), o título e a síntese do TR continuam com a formulação larga. Os backlogs existentes (Fund T01, TR T05) já descrevem as duas saídas.

### 2. Orquestração fixa ou alterada pela camada (importante, novo)

- Introdução: em fluxos agênticos "a camada conduz o ciclo de ferramentas e pode alterar o número de chamadas e o tamanho do contexto enviado ao modelo" (`:127-129`). É por aí que o texto espera um efeito maior.
- TR: nenhum trabalho compara "a mesma aplicação com e sem uma camada de integração, **mantendo fixa a orquestração**" (`trabalhos-relacionados.tex:294-295`); a camada é própria "para que a única diferença entre as duas versões da aplicação seja a presença dela" (`:176-177`).
- Fundamentação: a equivalência funcional "é o que permite atribuir a diferença observada à camada" (`:527-528`).

As duas leituras não cabem juntas sem explicação. Se as versões H e D fazem as mesmas chamadas com o mesmo contexto, o efeito indireto previsto na Introdução não existe por construção. Se a camada pode mudar chamadas e contexto, a orquestração não está fixa, e a diferença medida mistura a presença da camada com decisões de orquestração, que é a crítica feita a Matinpour et al. e Tripathy et al.

Combinado com o achado 1 (medição só de GPU), isto é o que decide se o Benchmark 2 tem algo a medir. O texto não diz qual das duas leituras vale; a política da versão D (A07) e o critério de paridade (A19) estão pendentes na Metodologia (`:126-127`). Esta é uma leitura minha do texto, não uma afirmação sobre o desenho final.

### 3. De onde vêm as responsabilidades da camada (importante, novo)

- TR, síntese: o trabalho herda "as responsabilidades da camada do catálogo de Liu et al." (`:388-389`).
- TR, seção 2.1: parte das responsabilidades "tem correspondência, **completa** ou por analogia, com padrões do catálogo" (`:95-96`).
- Fundamentação: "Como a lista não vem da literatura..." (`:340`); a lista é "decisão do autor" (`:101-104`); os graus são *parcial*, *analogia* e *nenhuma* (`:375-378`), ou seja, não há grau "completa"; duas das cinco responsabilidades não têm correspondência (`:422-425`).
- Objetivo (a): "delimitando suas responsabilidades com base em padrões arquiteturais publicados" (`1-introducao.tex:263-264`). Pela própria Fundamentação, a responsabilidade 5 se apoia em documentação técnica do OpenTelemetry e a 1, no conceito de *middleware*.

A Fundamentação é a versão mais cuidadosa. O TR e o objetivo (a) afirmam mais do que ela sustenta.

Ponto relacionado, na mesma frase da Fundamentação (`:422-424`): "só a segunda tem correspondência parcial direta" e "a terceira em parte". No Quadro (`:396-404`), as duas aparecem como "Parcial", e o termo "direta" não pertence à escala de três graus.

### 4. Definição e métricas do custo de substituição (importante, novo)

- Definição (Introdução `:161-165`, repetida na Fundamentação `:200-206`): três componentes, que são a extensão do código alterado, os pontos de dependência direta ao SDK e os casos de uso que continuam funcionando.
- Tabela da Metodologia (`3-metodologia.tex:145-150`): seis métricas, cinco delas primárias. Entram "Impacto estrutural (componentes ou interfaces afetados)", "Testes alterados ou quebrados" e "Tempo de implementação" (secundária), que não constam da definição.
- A Fundamentação fala em "métricas de estrutura de código como medida do custo de substituição" (`:533`), mas uma das primárias é comportamental (casos de uso).

A definição e a tabela precisam listar a mesma coisa, ou a definição precisa dizer que as demais métricas são complementares.

### 5. Responsabilidades "fora da avaliação" que entram na energia medida (importante, novo)

- Fundamentação: o custo energético da camada "inclui a orquestração de ferramentas da responsabilidade 2"; as responsabilidades 3, 4 e 5 "ficam fora da avaliação" (`:455-460`).
- Introdução: o trabalho que a camada acrescenta a cada requisição inclui "registro de eventos" (`:88-90`), que é a responsabilidade 5.

Se a versão H executa gestão de contexto, tratamento de falhas e registro de eventos a cada requisição, a energia desses componentes está dentro do que se mede, mesmo que eles não sejam avaliados como atributos de qualidade. O texto não diz se a versão D também registra eventos e trata falhas. Sem isso, não dá para saber se a diferença H−D é o custo da indireção ou o custo dessas funções.

### 6. Promessas sem lugar no esqueleto da Metodologia (importante, novo)

Estado do capítulo: 1.191 palavras e 17 marcadores `\pendencia`. Só a subseção "Delimitação das responsabilidades" (`:26-118`) está redigida. O capítulo não entra na entrega parcial (`documento.tex:285`).

O que os outros capítulos prometem e o esqueleto ainda não prevê:

- **Objetivo (e)**, critério de decisão "definido antes da coleta de dados" (Introdução `:273-276`; Fundamentação `:534-536`): não há seção para o confronto dos dois *benchmarks* nem para o critério. As seções existentes são Fase de solução, *Benchmark* 1, *Benchmark* 2, Ameaças e Base reaproveitada.
- **Ameaça externa de modelo e *hardware***: a Introdução diz que o limite de generalização "é tratado como ameaça à validade externa na metodologia" (`:238-239`). O marcador de validade externa só menciona "número de pontos de integração (A07)" (`3-metodologia.tex:190`).
- **A aplicação *web***: nenhuma seção descreve a aplicação, os seus casos de uso e o conjunto de ferramentas. A métrica "casos de uso que continuam funcionando" e a requisição agêntica dependem disso. O texto só diz que o conjunto de ferramentas será "pequeno e conhecido de antemão" (`:53`).
- **Interface do modelo local**: o texto não diz por qual interface as duas versões acessam o Qwen3.6 no servidor (A29 pendente).

Pelo checklist da skill `metodologia-tcc`, faltam também o diagrama de atividades no início do capítulo, o cronograma e o tempo verbal no futuro. A subseção redigida está no presente, o que é aceitável por ser análise, e não atividade. Dos objetivos, só o (a) tem atividade escrita.

### 7. Nomes diferentes para o mesmo construto (importante, novo)

Termos usados para o que o *Benchmark* 1 mede:

| Termo | Onde |
|---|---|
| custo de substituição do provedor | título, objetivos, definição |
| substituibilidade | Introdução `:206`; título do *Benchmark* 1 (`3-metodologia.tex:130`) |
| facilidade de trocar de provedor | Introdução `:155-156` |
| esforço de troca | TR, quadro e texto |
| manutenibilidade | TR `:242-243`: "energia e manutenibilidade, que são as duas dimensões deste trabalho" |
| desacoplamento | Introdução `:214` |

A Fundamentação separa os conceitos (`:172-180`): substituibilidade é propriedade do **provedor** e fica sob *flexibilidade* na ISO/IEC 25010:2023; modificabilidade é propriedade da **aplicação** e fica sob *manutenibilidade*. As métricas do *Benchmark* 1 (linhas alteradas, referências ao SDK) são da aplicação, portanto de modificabilidade, mas o *benchmark* se chama "Substituibilidade". E o TR chama a dimensão de "manutenibilidade", que pela Fundamentação é a característica acima da modificabilidade, não da substituibilidade.

O mesmo ocorre, em menor grau, com a energia: "custo energético" em todo o texto e "Eficiência energética" no título do *Benchmark* 2 (`3-metodologia.tex:165`). E com a equivalência das versões: "equivalência funcional" (Introdução, Fundamentação), "paridade funcional" e "corretude" (Metodologia `:126`, `:175`).

### 8. Origem do termo *harness* (menor, novo)

- Introdução (`:75-78`): interpor uma camada entre a aplicação e o provedor; "Na literatura recente, essa camada passou a ser chamada de *harness*" (Rafique e Bindschaedler).
- Fundamentação (`:275-285`): os autores usam o termo para a camada que **envolve o modelo**; a posição "entre a aplicação e o provedor" é acréscimo da definição operacional do autor.

A frase da Introdução atribui à literatura a posição arquitetural que a Fundamentação declara ser do autor.

Relacionado: a Fundamentação afirma que o *harness* "é um *middleware* aplicado aos provedores de modelos" (`:288-290`), enquanto a Metodologia qualifica a relação como "de propósito, e não de projeto" (`:44-47`). A formulação da Metodologia é a mais cautelosa.

### 9. "Agêntica" (menor, parcialmente tratado)

O trabalho adota a distinção de Sapkota et al.: agente de IA (dentro do escopo) e IA agêntica, que são sistemas multiagente (fora do escopo) (Fundamentação `:126-130`). Em seguida usa "requisição agêntica" e "fluxos agênticos" para o agente único com ciclo de ferramentas (`:150-153`; objetivos (d) e (e)). A definição operacional avisa o leitor, mas o adjetivo é o mesmo que a taxonomia adotada reserva ao que foi excluído. A task T07 da Introdução tratou só o título.

### 10. Vellaisamy et al.: energia ou latência (menor, parcialmente tratado)

- Quadro do TR: "Energia medida: Não (latência)" (`:362`).
- O mesmo capítulo abre a seção com "A medição de energia na inferência de LLMs concentra-se na pilha que executa o modelo" e cita o trabalho em seguida (`:257-260`); a síntese o inclui entre "os estudos de energia em sistemas com LLMs" (`:320-322`).
- Fundamentação: precedente para decompor o custo, com o verbo "gasta" (`:485-488`).

A task TR T07 corrige a Fundamentação. A contradição dentro do próprio TR não está coberta.

### 11. "Trabalho anterior do autor" (menor, parcialmente tratado)

A expressão aparece na Introdução (`:243`), no TR (`:282`) e na Fundamentação (`:499`). No `.bib`, o autor do TCC é o segundo de cinco autores de Barros et al. (2026). A task TR T15 cobre só a ocorrência do TR.

### 12. Bases de busca (menor, já no backlog)

Introdução (`:150-151`): ACM DL, IEEE Xplore e Biblioteca Digital da SBC. TR (`:64-68`): as mesmas, mais OpenAlex e Crossref. O comentário do cabeçalho do TR acrescenta "busca na web" e registra que a busca na SBC foi feita por evento. TR T03, aberto.

### 13. Dois ou três provedores (menor, novo)

A Fundamentação fala na "documentação dos dois provedores usados neste trabalho" (`:135`), e a Figura mostra "Provedor A" e "Provedor B" (`:324-325`). A Introdução define três fontes de modelo: Anthropic e OpenAI no *Benchmark* 1 e o Qwen3.6 em servidor institucional no *Benchmark* 2 (`:216-231`). O texto não diz se o servidor institucional conta como "provedor" na definição da camada.

### 14. Quais responsabilidades ficam sem avaliação (menor, novo)

Introdução (`:210-212`): "a recuperação de falhas e a auditabilidade" (responsabilidades 4 e 5). Fundamentação (`:458-460`): responsabilidades 3, 4 e 5, com remissão à mesma seção da Introdução. A gestão de contexto e estado não aparece na Introdução.

### 15. Itens menores

- **TR, abertura** (`:77-78`): quatro grupos, "um para cada parte da pergunta de pesquisa". A pergunta tem duas partes.
- **TR, síntese** (`:311-322`): Lin et al. está no quadro, mas não no parágrafo que o resume. Poy, Feitosa, Järvenpää, Kaur e Nascimento também não.
- **TR, quadro, coluna "Compara com e sem a decisão"**: Barros et al. recebe "Sim" (`:370`), embora o texto diga que o trabalho compara topologias inteiras, ao lado de Matinpour e Tripathy, que recebem "Não (*frameworks* inteiros)" (`:291-293`).
- **Fundamentação**: Sedghpour et al. é citado no Quadro e na síntese (`:409`, `:450`), mas só é descrito na Metodologia (`3-metodologia.tex:85-86`), que não entra na entrega parcial.
- **Fundamentação** (`:427-428`): "O exame de cada correspondência [...] pertence ao projeto da camada", sem remissão. Na entrega parcial, o leitor não tem onde encontrá-lo.
- **Quadro `qua:harness-liu`**: o *Tool/agent registry* está listado como padrão da responsabilidade 2, e a Metodologia diz que o problema dele "pouco se coloca" neste trabalho (`:51-54`).
- **Introdução** (`:37-38`): "em seis meses, de [...] novembro de 2024 para [...] meados de 2025". O intervalo descrito é de cerca de sete a oito meses. **Correção (10/11/2026):** não procede; a verificação anterior (`entregas/introduction/revision/t14-verificacao-numeros-e-fontes.md`, linha 11) registra que o relatório usa "more than doubled in just six months" com essas datas.
- **Comentários desatualizados** (não aparecem no PDF): a Fundamentação é o Capítulo 3, mas o cabeçalho ainda numera as seções como 2.1 a 2.7 (`:10-17`) e diz que o quadro de síntese "ainda não foi produzido" (`:79-80`), embora ele exista (`qua:conceitos-uso`). A Metodologia (`:22-24`) e o `preambulo.tex:105` ainda se referem à Fundamentação como "Cap. 2".
- **`referencias.bib:142`**: `Mo, David` continua sem a correção da task TR T08 (`Mo, Di`).

## O que está consistente

- **Citações**: todas as chaves citadas existem no `.bib`, e todas as entradas do `.bib` são citadas.
- **Remissões**: todo `\ref` aponta para um `\label` existente.
- **Siglas**: as dez siglas marcadas com `\glsadd` estão definidas na lista.
- **Aritmética**: 0,047 kWh por mil inferências ≈ 169 J por requisição ("cerca de 170 J"); 10 ms × 100 W = 1 J, menos de 1%; 0,047/0,002 ≈ 23,5 ("mais de vinte vezes" na Introdução, "mais de uma ordem de grandeza" na Fundamentação); 415 → 945 TWh e 3,5 → 8,4 bilhões são mais que o dobro; Anthropic (32%) e OpenAI (25%) são de fato os dois maiores nos números citados.
- **Entre capítulos**: 18 padrões e 57 estudos de Liu et al.; período da busca (2023 a 2026); descrições de Kandogan et al. e Zhu et al.; título, objetivo geral, pergunta e hipótese; desenho 2×2 e duas variáveis dependentes; taxonomia de ameaças de Wohlin et al.; escopo sem sistemas multiagente.
- **Papéis das seções**: não encontrei definição de conceito no TR nem comparação com outros trabalhos na Fundamentação, exceto a menção a Mo et al. como precedente de método (`:533-534`), que o cabeçalho do arquivo declara intencional.

## Checklists das skills

**Trabalhos Relacionados.** Cada trabalho tem relação, semelhança e diferença, e as diferenças são verificáveis (domínio, tipo de avaliação, o que é medido). O quadro tem título descritivo, fonte e a proposta como linha. Pontos fracos: os achados 3, 10 e os itens de quadro do 15; os termos usados antes de definidos (TR T17, aberto); e as negativas tiradas só de resumos, que o cabeçalho do arquivo declara (TR T01, aberto).

**Fundamentação Teórica.** Os conceitos têm definição adotada com referência, as divergências (agente, *harness*) têm a opção adotada explícita, as seções fecham ligando o conceito ao trabalho, e há figura e quadros com fonte. O conceito "aplicação *web*", que está no título, não tem seção nem definição. O cabeçalho do arquivo lista fontes "não lidas na íntegra" e afirmações "a conferir no texto das fontes" (`:32-36`, `:60-70`); não foi possível saber aqui se essas pendências foram fechadas.

**Metodologia.** Ver achado 6. O capítulo é um esqueleto, e o que está redigido é análise de correspondência com a literatura, e não lista de atividades.

## Estilo (diagnóstico com a skill `humanizer`, sem reescrita)

Contagens no texto compilável, sem comentários:

| Arquivo | Palavras | ", e não ..." | Travessões (`---`) | `\textbf` |
|---|---|---|---|---|
| Introdução | 2.338 | 10 | 7 | 4 |
| Trabalhos Relacionados | 3.051 | 11 | 0 | 12 |
| Fundamentação | 3.968 | 18 | 0 | 17 |
| Metodologia | 1.191 | 4 | 2 | 0 |

- **Contraste "X, e não Y"**: 43 ocorrências nos quatro arquivos, cerca de uma a cada 245 palavras. Parte delas delimita escopo e carrega informação (por exemplo, "analogia, e não um achado"). Outras negam algo que ninguém afirmou (por exemplo, "permite tomá-la com base em dados, e não apenas em princípios de projeto", Introdução `:192`). É o padrão mais repetido do texto.
- **Travessões**: só a Introdução os usa em incisos (7), o que destoa dos outros capítulos. Os dois da Metodologia são títulos de seção.
- **"Mais próximo"**: cinco trabalhos do TR são apresentados como "o mais próximo" sob algum aspecto (`:90`, `:121`, `:194`, `:241`, `:269`).
- **Ressalvas de processo**: "leitura própria", "analogia do autor", "decisão do autor", "não sustenta afirmação empírica" se repetem na Fundamentação e na Metodologia. A task Fund T05 já trata disso.
- **Negrito**: boa parte está em cabeçalhos de quadro e em termos definidos, uso normal.

Não encontrei resíduos de conversa, linguagem promocional nem tríades forçadas.

## Impressões

1. O texto é cuidadoso em separar o que vem da literatura do que é decisão do autor. A maior parte das inconsistências nasce quando um capítulo resume outro de forma mais forte do que o original (achados 3, 8, 10).
2. Os achados 1, 2 e 5 são o mesmo problema visto de três lados: ainda não está escrito o que exatamente difere entre as versões H e D e o que o instrumento enxerga dessa diferença. Enquanto A07, A11 e A19 estiverem abertos, o objetivo (d) promete mais do que o desenho descrito entrega.
3. A Metodologia é o capítulo que deveria resolver as tensões acima, e hoje é um esqueleto. Vários marcadores de pendência correspondem a promessas já feitas nos capítulos entregues.
4. A terminologia do construto principal (achado 7) é o ajuste de menor custo e maior efeito na leitura: a Fundamentação já tem a distinção pronta, falta aplicá-la aos outros capítulos.
5. Dos backlogs existentes, as tasks conferidas aqui e ainda abertas no texto são: Fund T01, TR T03, TR T05, TR T07, TR T08, TR T15 e TR T17. As demais não foram reconferidas.
