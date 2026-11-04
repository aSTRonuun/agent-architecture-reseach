# Tasks de correção — Projeto e avaliação experimental de uma camada arquitetural (harness) para integração de modelos de IA em aplicações web: custo de substituição de provedor e custo energético
Origem: `revision/revisao-trabalhos-relacionados-v1.md` (1ª revisão, somente Trabalhos Relacionados), nota estimada 0,75/1,0 no escopo avaliado | Parecer: apto, com duas ressalvas de coerência (T05, T06)
Total: 17 tasks (0 críticas, 0 altas, 1 média, 16 baixas) | Pontos recuperáveis: 0,25

## Status da execução (02/11/2026, sem o autor presente)

Nada foi compilado: não há LaTeX na máquina. As edições passaram só por conferência estática (chaves, `\ref`, chaves do `.bib`). Compilar no Overleaf e conferir o quadro (T13) e o novo apêndice.

### Enxugamento do capítulo (03/11/2026)

O capítulo passou de 21 para 12 trabalhos e de quatro para duas seções; saiu o parágrafo de abertura sobre as bases de busca (fica só a remissão ao Apêndice). Retirados: Bandeira, Sheneman, Rahaman, Lin, Kaur, Poy, Järvenpää, Ifath e Nascimento (motivos no cabeçalho do `.tex`; entradas mantidas no `.bib`). Efeito nas tasks:

- **T11 resolvida por retirada**: Nascimento et al. não aparece mais (atende ao critério de aceite). Pode sair do backlog.
- **T01 atende ao critério de aceite**: a única negativa sobre trabalho não lido na íntegra (Morais et al.) está como "o resumo não relata"; sobre Matinpour et al. o capítulo só afirma números conferidos no resumo. Ler os dois na íntegra passa a ser melhoria opcional. Pode sair do backlog.
- **T05 continua pendente**, mas encolheu: o capítulo só cita Vellaisamy et al. em uma frase e o protocolo de Barros et al. em outra. Quando a Fund. T01 (A11) fechar, basta conferir essas duas frases; pode ser absorvida pela Fund. T01.
- T13: o quadro caiu para 13 linhas, o que reduz o risco de paginação; ainda falta compilar.
- T17: a definição de táticas arquiteturais (com `bass2021`) foi para a 1ª ocorrência, no parágrafo de Xiao et al.; "requisição agêntica" não aparece mais no capítulo.
- T09 (Lin), T10 (Ifath) e T12 (Kaur): os trechos tratados saíram do capítulo; as correções no `.bib` e na Fundamentação continuam valendo.
- Introdução e Apêndice ajustados: a lacuna remete só ao Apêndice; o Apêndice informa 21 incluídos na triagem e 12 mantidos no capítulo.

### Status por task

| ID | Status | O que foi feito / o que falta |
|---|---|---|
| T01 | Feita (critério de aceite; ver enxugamento) | Lidos na versão arXiv: Kandogan et al. (negativas confirmadas) e Tripathy et al. Matinpour et al. e Morais et al.: só o resumo (ACM DL bloqueia download automático). Negativas sobre Morais reformuladas como "o resumo não relata". **Falta:** ler o texto integral de Morais e Matinpour pelo Portal CAPES e confirmar ou desfazer a reformulação. Cabeçalho do `.tex` atualizado. |
| T02 | Feita | Novo `3-pos-textuais/apendices/apendice-busca.tex` (rótulo `ap:busca`), incluído também na entrega parcial em `documento.tex`; parágrafo de abertura remete a ele. O número de triados por etapa não estava registrado e consta como tal; as buscas complementares (OpenAlex, Crossref, web, SBC) não têm strings registradas. |
| T03 | Feita | Cap. 2 e Introdução citam as mesmas bases; SBC como busca por evento, com os eventos nomeados. |
| T04 | Feita | Parágrafo de Mo et al. traz 42 estudantes e biblioteca pronta, com o que a proposta perde e ganha em cada uma; síntese e quadro ajustados. |
| T05 | **Pendente (decisão)** | Depende do A11 (Fund. T01: medir CPU ou restringir ao efeito indireto). |
| T06 | Feita | Xiao et al. oferecem tabela de compromissos e recomendação de avaliar a carga, mas não um critério de decisão; o capítulo diz que o critério do objetivo (e) é contribuição própria. **Falta:** a Fund. T02 fundamentar esse critério. |
| T07 | Feita | Fundamentação agora diz que Vellaisamy et al. decompõem tempo, transposto aqui para energia. |
| T08 | Feita | `Mo, Di`. |
| T09 | Feita | Lin et al.: dez gateways confirmados. Matinpour et al.: 3–15% e 2–4% confirmados no resumo. Xiao et al.: a nuance não constava; trocada por "três prejudicaram, uma favoreceu, duas não alteraram" (e retirado o exemplo de duplicação e acoplamento, não confirmado). |
| T10 | Feita | Prenomes completos pelo Crossref (Vellaisamy, Ifath, Kandogan). |
| T11 | Feita (retirada em 03/11) | Nascimento et al. saiu do capítulo e do quadro. |
| T12 | Feita | A frase "revisam abordagens…" fica só na Fundamentação; o Cap. 2 só compara. |
| T13 | Feita, sem compilar | Coluna dividida em "Esforço de troca medido" e "Manutenibilidade medida"; só Mo et al. e a proposta têm "Sim" em esforço de troca. Quadro com 7 colunas e 21 linhas em `[h!]`: conferir a paginação e, se quebrar mal, usar `longtable` (o pacote não está carregado no preâmbulo). A célula "Não (resumo)" de Morais et al. e a coluna "Qualitativo" (Liu, Bucaioni, Zhu, Kaur) são julgamento meu: revisar. |
| T14 | Feita | Extensão a LLMs marcada como analogia. |
| T15 | Feita | "do qual o autor é coautor". |
| T16 | Feita | Intro: 1º parágrafo de 1.2 reduzido a duas frases com remissão ao Cap. 2; 1.1 sem repetir a diferença de objeto; lacuna remete ao Cap. 2 e ao Apêndice. |
| T17 | Feita | Definição ou remissão na 1ª ocorrência de táticas arquiteturais (com `bass2021`), requisição agêntica e NVML. |

Também incorporado: Tripathy et al. com taxas de resolução de 4% e 0% (item "Fora da revisão").

## Visão geral

| ID | Título | Tipo | Severidade | Pontos | Esforço | Depende de |
|---|---|---|---|---|---|---|
| T01 | Ler na íntegra os trabalhos que sustentam a lacuna | Conteúdo insuficiente | Média | −0,10 | G | — |
| T02 | Levar o protocolo da busca para o texto ou apêndice | Método | Baixa | −0,05 | M | — |
| T03 | Declarar a cobertura real da busca na SBC | Clareza/precisão | Baixa | −0,05 | P | T02 |
| T04 | Explicitar as diferenças em relação a Mo et al. (2023) | Conteúdo insuficiente | Baixa | −0,05 | P | — |
| T05 | Alinhar o capítulo à fronteira da medição de energia | Coerência interna | Baixa | 0 | M | Fund. T01 |
| T06 | Verificar se Xiao et al. confrontam energia e manutenibilidade | Coerência interna | Baixa | 0 | M | — |
| T07 | Esclarecer que Vellaisamy et al. decompõem tempo, não energia | Coerência interna | Baixa | 0 | P | — |
| T08 | Corrigir o prenome do primeiro autor de Mo et al. | Referência | Baixa | 0 | P | — |
| T09 | Confirmar os números não localizados na verificação | Referência | Baixa | 0 | M | — |
| T10 | Uniformizar prenomes abreviados no `.bib` | Formatação | Baixa | 0 | P | — |
| T11 | Fortalecer ou retirar Nascimento et al. (2026) | Conteúdo insuficiente | Baixa | 0 | P | T05 |
| T12 | Deixar Kaur et al. (2017) só no papel comparativo | Coesão/argumentação | Baixa | 0 | P | — |
| T13 | Separar a coluna mista do quadro e conferir paginação | Formatação | Baixa | 0 | P | T01 |
| T14 | Marcar a extrapolação de Feitosa et al. como analogia | Coesão/argumentação | Baixa | 0 | P | — |
| T15 | Corrigir "trabalho anterior do autor" para coautoria | Redação | Baixa | 0 | P | — |
| T16 | Encurtar a lacuna na Introdução e remeter ao capítulo | Coesão/argumentação | Baixa | 0 | M | T01, T03 |
| T17 | Definir termos técnicos na primeira ocorrência | Clareza/precisão | Baixa | 0 | P | — |

Soma dos pontos: T01 (0,10) + T02 (0,05) + T03 (0,05) + T04 (0,05) = **0,25**, igual ao total perdido na revisão.

"Fund. T01" = T01 de `entregas/fundamentacao/backlog/tasks-fundamentacao-v1.md` (fronteira GPU × CPU, item A11).

## Detalhamento

### T01 — Ler na íntegra os trabalhos que sustentam a lacuna
**Tipo:** Conteúdo insuficiente | **Severidade:** Média | **Critério:** 2.1 — verificação (d) lacuna evidente | **Pontos:** −0,10 | **Esforço:** G
**Localização:** `trabalhos-relacionados.tex:121-147` (Morais et al.; Kandogan et al.), `:269-296` (Matinpour et al.; Tripathy et al.); cabeçalho `:49-51`
**Evidência:** a revisão aponta que o cabeçalho declara "Lidos: resumos de todos os trabalhos novos" e "NÃO lidos na íntegra: Kandogan et al.", e que a negativa sobre Morais et al. (2026), "não mede o esforço de fazê-la nem o compara com uma integração direta" (`:133-135`), é o ponto mais frágil do capítulo.
**Problema:** a lacuna é definida pelo que os outros trabalhos não fazem. Uma negativa tirada só do resumo pode estar errada, porque o resumo omite parte do que o artigo faz, e a banca vai contestar justamente o trabalho mais próximo.
**Como resolver:**
1. Obter pelo Portal CAPES o texto integral de Morais et al. (2026), Kandogan et al. (2025), Matinpour et al. (2026) e Tripathy et al. (2026).
2. Para cada negativa do capítulo sobre esses trabalhos ("não mede", "não compara", "sem medição"), confirmar no texto ou corrigir.
3. Onde a leitura não for possível, trocar a negativa por "o resumo não relata…".
4. Atualizar o registro "Lidos / NÃO lidos" no cabeçalho do `.tex`.
**Critério de aceite:** toda afirmação negativa sobre esses quatro trabalhos foi conferida no texto integral ou está formulada como "o resumo não relata"; o cabeçalho registra o que foi lido na íntegra.
**Depende de:** —

### T02 — Levar o protocolo da busca para o texto ou apêndice
**Tipo:** Método | **Severidade:** Baixa | **Critério:** 2.1 — motivo 1 (protocolo fora do texto compilado) | **Pontos:** −0,05 | **Esforço:** M
**Localização:** `trabalhos-relacionados.tex:13-58` (comentário) e `:63-75` (parágrafo de abertura); `1-introducao.tex:150-154`
**Evidência:** a revisão aponta que as strings, as contagens e o critério de inclusão estão só em comentário LaTeX. O PDF informa bases, período e grupos de termos, mas não permite repetir a busca, embora a Introdução remeta ao capítulo como prova.
**Problema:** a afirmação "não foram encontrados estudos" depende de uma busca que o leitor do PDF não consegue repetir.
**Como resolver:**
1. Criar um apêndice (ou quadro) com, por base: string, campo, filtro de período, data e número de resultados.
2. Registrar a triagem: critério de inclusão ("revisado por pares e com a mesma motivação, objeto ou método"), critérios de exclusão e quantos foram incluídos.
3. No parágrafo de abertura, remeter ao apêndice com `\ref{}`.
**Critério de aceite:** o PDF compilado mostra as strings, as bases, a data, as contagens e os critérios de inclusão e exclusão, e o parágrafo de abertura remete a eles.
**Depende de:** —

### T03 — Declarar a cobertura real da busca na SBC
**Tipo:** Clareza/precisão | **Severidade:** Baixa | **Critério:** 2.1 — motivo 2; Coerência interna (c) | **Pontos:** −0,05 | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:66-67`; `1-introducao.tex:150-151`
**Evidência:** a revisão aponta que o texto diz que a busca usou a "Biblioteca Digital da Sociedade Brasileira de Computação", mas o cabeçalho registra que a busca geral exige login e que ela foi feita por evento. A Introdução também omite OpenAlex e Crossref.
**Problema:** a cobertura declarada é maior do que a cobertura real.
**Como resolver:**
1. No capítulo, citar os eventos efetivamente buscados (SBES, SBCARS, SEMISH, WSCAD/SSCAD, WCAMA, SBSI).
2. Na Introdução, usar a mesma lista de bases do capítulo, ou só "nas buscas descritas no Capítulo X".
**Critério de aceite:** Introdução e capítulo descrevem as mesmas bases, e a SBC aparece como busca por evento, com os eventos nomeados.
**Depende de:** T02

### T04 — Explicitar as diferenças em relação a Mo et al. (2023)
**Tipo:** Conteúdo insuficiente | **Severidade:** Baixa | **Critério:** 2.1 — motivo 3 | **Pontos:** −0,05 | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:194-208` (parágrafo de Mo et al.) e `:386-387` (síntese)
**Evidência:** a revisão conferiu no artigo que o esforço de portabilidade foi medido com 42 estudantes (tempo, esforço percebido e sucesso) e que a abstração foi uma biblioteca pronta (Apache jclouds), diferenças que o capítulo omite.
**Problema:** a síntese diz que o trabalho "herda o desenho com e sem a camada e as métricas de código" de Mo et al. sem dizer que lá o esforço foi medido com pessoas e com uma biblioteca de terceiros.
**Como resolver:**
1. No parágrafo de Mo et al., acrescentar as duas diferenças: participantes × métricas de código aplicadas pelo autor; biblioteca pronta × camada própria.
2. Dizer o que a proposta perde (validade de construto do esforço) e ganha (isolamento da camada) com cada uma, reaproveitando o argumento dado a Zhu et al. (`:175-178`).
**Critério de aceite:** o parágrafo nomeia as duas diferenças e a consequência de cada uma para o desenho do trabalho.
**Depende de:** —

### T05 — Alinhar o capítulo à fronteira da medição de energia
**Tipo:** Coerência interna | **Severidade:** Baixa | **Critério:** Coerência interna (b) | **Pontos:** 0 | **Esforço:** M
**Localização:** `trabalhos-relacionados.tex:258-260` (Vellaisamy et al.), `:283-292` e `:389-390` (protocolo herdado de Barros et al.)
**Evidência:** a revisão aponta que o capítulo afirma que a sobrecarga do hospedeiro (CPU) é custo oculto e, ao mesmo tempo, herda de Barros et al. um protocolo só de GPU, o que reforça a ressalva da Fundamentação: o instrumento não alcança o custo direto da camada.
**Problema:** o capítulo dá argumento contra o próprio instrumento herdado sem tratar disso.
**Como resolver:**
1. Fechar a decisão do A11 (Fund. T01).
2. Se medir CPU, dizer na síntese que o protocolo de Barros et al. é estendido e com que instrumento; se não medir, dizer que o efeito capturado é o indireto e usar Vellaisamy et al. como a limitação reconhecida.
**Critério de aceite:** o capítulo e a Fundamentação descrevem a mesma fronteira de medição, e a frase da síntese sobre o protocolo herdado é compatível com ela.
**Depende de:** Fund. T01

### T06 — Verificar se Xiao et al. confrontam energia e manutenibilidade
**Tipo:** Coerência interna | **Severidade:** Baixa | **Critério:** Coerência interna (a), objetivo (e) | **Pontos:** 0 | **Esforço:** M
**Localização:** `trabalhos-relacionados.tex:235-246` e `:387-388`
**Evidência:** a revisão aponta que o objetivo (e) só tem Xiao et al. (2025) como precedente de pergunta, e o capítulo não diz se eles propõem alguma forma de comparar as duas grandezas, o que reforça a perda 4.1-(i) da Fundamentação.
**Problema:** o critério de decisão do objetivo (e) continua sem base na literatura.
**Como resolver:**
1. Ler a seção de resultados e discussão de Xiao et al. (arXiv 2501.14402) e anotar como eles relatam o compromisso entre energia e manutenibilidade.
2. Se houver método, citá-lo no capítulo como o que se herda para o objetivo (e) e usá-lo na Fund. T02; se não houver, dizer que o critério de decisão é contribuição própria e fundamentá-lo na Fund. T02.
**Critério de aceite:** o capítulo diz explicitamente se Xiao et al. oferecem ou não uma forma de confrontar as duas dimensões, e a frase é coerente com a solução da Fund. T02.
**Depende de:** — (alimenta a Fund. T02)

### T07 — Esclarecer que Vellaisamy et al. decompõem tempo, não energia
**Tipo:** Coerência interna | **Severidade:** Baixa | **Critério:** Coerência interna (b) | **Pontos:** 0 | **Esforço:** P
**Localização:** `2-fundamentacao-teorica.tex:485-488`; quadro em `trabalhos-relacionados.tex:362`
**Evidência:** a revisão aponta que o quadro marca Vellaisamy et al. como "Energia medida: Não (latência)", enquanto a Fundamentação os cita como precedente para decompor o custo energético.
**Problema:** os dois capítulos atribuem papéis diferentes ao mesmo trabalho.
**Como resolver:**
1. Na Fundamentação, dizer que o precedente é a decomposição do tempo entre hospedeiro e dispositivo, transposta aqui para energia.
**Critério de aceite:** a Fundamentação não sugere que Vellaisamy et al. mediram energia, e o texto é compatível com a linha do quadro.
**Depende de:** —

### T08 — Corrigir o prenome do primeiro autor de Mo et al.
**Tipo:** Referência | **Severidade:** Baixa | **Critério:** Verificação de referências (sem perda) | **Pontos:** 0 | **Esforço:** P
**Localização:** `3-pos-textuais/referencias.bib:142`
**Evidência:** a revisão verificou no PDF dos autores e no Crossref que o primeiro autor é **Di Mo**, e não "David".
**Problema:** a referência sai com o nome errado na lista final.
**Como resolver:**
1. Trocar `Mo, David` por `Mo, Di`.
**Critério de aceite:** a entrada `mo2023` tem `author = {Mo, Di and Cordingly, Robert and Chinn, Donald and Lloyd, Wes}`.
**Depende de:** —

### T09 — Confirmar os números não localizados na verificação
**Tipo:** Referência | **Severidade:** Baixa | **Critério:** Verificação de referências (sem perda) | **Pontos:** 0 | **Esforço:** M
**Localização:** `trabalhos-relacionados.tex:275-277` (Matinpour et al.), `:159-160` (Lin et al.), `:239-241` (Xiao et al.)
**Evidência:** a revisão não localizou a latência 3–15% menor e a energia 2–4% maior do LlamaIndex (Matinpour et al.), as "dez" gateways auditadas (Lin et al.) e a nuance "as que também melhoraram o desempenho tenderam a prejudicar a manutenibilidade" (Xiao et al.).
**Problema:** são números e afirmações específicas atribuídas às fontes sem confirmação independente.
**Como resolver:**
1. Conferir cada um no texto integral (pode ser feito junto com a T01 para Matinpour et al.).
2. Corrigir o valor ou retirar o detalhe que não constar da fonte.
**Critério de aceite:** os três trechos batem com a fonte ou foram reformulados sem o detalhe não confirmado.
**Depende de:** —

### T10 — Uniformizar prenomes abreviados no `.bib`
**Tipo:** Formatação | **Severidade:** Baixa | **Critério:** 7 Formatação (observação sem nota) | **Pontos:** 0 | **Esforço:** P
**Localização:** `referencias.bib:47` (Vellaisamy et al.), `:59` (Ifath e Haque), `:94` (Kandogan et al., parte dos autores)
**Evidência:** a revisão aponta prenomes abreviados nessas entradas e por extenso nas demais.
**Problema:** a lista de referências sai com padrão misto.
**Como resolver:**
1. Completar os prenomes pelo Crossref (DOI de cada entrada) ou abreviar todos, conforme o padrão do template.
**Critério de aceite:** todas as entradas citadas no Cap. 2 seguem o mesmo padrão de prenome.
**Depende de:** —

### T11 — Fortalecer ou retirar Nascimento et al. (2026)
**Tipo:** Conteúdo insuficiente | **Severidade:** Baixa | **Critério:** 2.1 — verificação (c), exceção (i) | **Pontos:** 0 | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:298-305`
**Evidência:** a revisão aponta relação fraca ("compartilha a preocupação", `:303`), que não passa no teste "fez assim e posso fazer parecido".
**Problema:** o trabalho parece incluído para cobrir a literatura nacional, sem papel na proposta.
**Como resolver:**
1. Se a T05 decidir medir CPU, usar Nascimento et al. (medição em CPU local com CodeCarbon) como alternativa de instrumento considerada, dizendo por que foi adotada ou não.
2. Caso contrário, retirar o trabalho do capítulo e do quadro.
**Critério de aceite:** o parágrafo diz o que a proposta aproveita ou recusa de Nascimento et al., ou o trabalho não aparece mais.
**Depende de:** T05

### T12 — Deixar Kaur et al. (2017) só no papel comparativo
**Tipo:** Coesão/argumentação | **Severidade:** Baixa | **Critério:** 2.1 — verificação (c), exceção (ii) | **Pontos:** 0 | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:185-192`; `2-fundamentacao-teorica.tex:194`
**Evidência:** a revisão aponta que Kaur et al. são usados como conceito ("problema estabelecido de arquitetura"), papel de Fundamentação, e que a mesma frase está nos dois capítulos.
**Problema:** a referência aparece repetida e com papel trocado.
**Como resolver:**
1. Manter na Fundamentação a frase conceitual.
2. No Cap. 2, deixar só a comparação (domínio de nuvem × provedores de modelos; revisão × experimento), sem repetir a frase.
**Critério de aceite:** a frase "revisam abordagens de interoperabilidade e portabilidade…" aparece uma única vez no documento.
**Depende de:** —

### T13 — Separar a coluna mista do quadro e conferir paginação
**Tipo:** Formatação | **Severidade:** Baixa | **Critério:** 2.1 (observação sem nota) | **Pontos:** 0 | **Esforço:** P
**Localização:** Quadro `qua:trabalhos-relacionados`, `trabalhos-relacionados.tex:324-380`
**Evidência:** a revisão aponta que a coluna "Esforço de troca ou manutenibilidade" junta dois construtos, o que dá o mesmo "Sim" a Xiao et al. e a Mo et al. e esconde a característica exclusiva da proposta, e que não conferiu se o quadro de 21 linhas cabe em uma página.
**Problema:** o quadro não mostra a diferença que a síntese afirma.
**Como resolver:**
1. Separar em "Esforço de troca medido" e "Manutenibilidade medida".
2. Atualizar as células com o que a T01 confirmar.
3. Compilar e, se o quadro quebrar mal, usar `longtable` ou reduzir linhas.
**Critério de aceite:** as duas colunas existem, só Mo et al. e a proposta têm "Sim" em esforço de troca (salvo achado novo na T01), e o quadro compila sem estourar a página.
**Depende de:** T01

### T14 — Marcar a extrapolação de Feitosa et al. como analogia
**Tipo:** Coesão/argumentação | **Severidade:** Baixa | **Critério:** 2.1 (observação sem nota) | **Pontos:** 0 | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:229-231`
**Evidência:** a revisão aponta que "o peso relativo da indireção cai quando o trabalho envolvido cresce, o que é o caso de uma requisição a um LLM" leva um achado sobre métodos Java para requisições a LLM, enquanto a Introdução trata extensão parecida como "analogia, e não um achado".
**Problema:** o capítulo usa um critério mais frouxo que a Introdução para a mesma operação.
**Como resolver:**
1. Reformular como analogia ("por analogia, é de esperar que…").
**Critério de aceite:** o trecho não apresenta a extensão a LLMs como achado de Feitosa et al.
**Depende de:** —

### T15 — Corrigir "trabalho anterior do autor" para coautoria
**Tipo:** Redação | **Severidade:** Baixa | **Critério:** 2.1 (observação sem nota) | **Pontos:** 0 | **Esforço:** P
**Localização:** `trabalhos-relacionados.tex:283`
**Evidência:** a revisão aponta que o autor é segundo autor de Barros et al. (2026).
**Problema:** a frase atribui o trabalho só ao autor.
**Como resolver:**
1. Trocar por "Em trabalho anterior, do qual o autor é coautor, …".
**Critério de aceite:** o texto indica coautoria.
**Depende de:** —

### T16 — Encurtar a lacuna na Introdução e remeter ao capítulo
**Tipo:** Coesão/argumentação | **Severidade:** Baixa | **Critério:** 2.1 (observação sem nota) | **Pontos:** 0 | **Esforço:** M
**Localização:** `1-introducao.tex:135-146` (Liu, Kandogan, Zhu) e `:107-116` (Vellaisamy, Ifath); `trabalhos-relacionados.tex:258-267`
**Evidência:** a revisão aponta que o 1º parágrafo de 1.2 descreve Liu, Kandogan e Zhu com as mesmas limitações que o capítulo detalha, e que o par Vellaisamy/Ifath da Introdução é quase o mesmo texto do capítulo.
**Problema:** a mesma comparação aparece duas vezes.
**Como resolver:**
1. Reduzir o 1º parágrafo de 1.2 a duas frases sobre o estado da literatura, com remissão ao Cap. 2.
2. Na 1.1, manter Vellaisamy/Ifath só como contexto da hipótese, sem repetir a diferença de objeto, que fica no Cap. 2.
3. Ajustar a frase da lacuna à formulação final da T01 e da T03.
**Critério de aceite:** nenhum trecho da Introdução repete quase literalmente o Cap. 2, e a lacuna da Introdução bate com a síntese do capítulo.
**Depende de:** T01, T03

### T17 — Definir termos técnicos na primeira ocorrência
**Tipo:** Clareza/precisão | **Severidade:** Baixa | **Critério:** 2.1 (observação sem nota) | **Pontos:** 0 | **Esforço:** P
**Localização:** Cap. 2, primeiras ocorrências de "táticas arquiteturais" (`:73`), "requisição agêntica" (`:207`) e "NVML" (`:283`)
**Evidência:** a revisão aponta que, com o capítulo antes da Fundamentação, esses termos aparecem antes de ser definidos.
**Problema:** o leitor encontra termos que só a Fundamentação define.
**Como resolver:**
1. Na primeira ocorrência, acrescentar definição de uma oração ou remissão (`\ref{}`) à seção da Fundamentação.
**Critério de aceite:** cada um dos três termos tem definição curta ou remissão na primeira ocorrência no Cap. 2.
**Depende de:** —

## Fora da revisão (não convertido)
- Tripathy et al. (2026): segundo o arXiv, as taxas de resolução ficaram perto de zero (4% e 0%), o que indica que boa parte da energia foi gasta em ciclos improdutivos. Vale considerar ao citar a razão de 9,4×.
- As revisões da Introdução e da Fundamentação (v1, 21/10) são anteriores às mudanças de 02/11; uma nova revisão das duas atualizaria a nota acumulada.

Premissas: severidade derivada das regras da skill. As ressalvas de coerência (T05–T07) não foram classificadas como Críticas porque a revisão concluiu "apto" (desvios corrigíveis, não estruturais). A perda única do critério 2.1 (−0,25) foi dividida sem dupla contagem entre os quatro motivos da revisão: (d) lacuna = T01 (−0,10); protocolo = T02 (−0,05); cobertura da SBC = T03 (−0,05); diferenças de Mo et al. = T04 (−0,05). Essa divisão é estimativa a partir do peso que a revisão dá a cada motivo. Observações sem perda e referências não localizadas viraram tasks Baixa (nenhuma das não localizadas sustenta a lacuna, exceto Morais et al., já coberta pela T01). Esforço estimado. A nova nota depende de nova avaliação.
