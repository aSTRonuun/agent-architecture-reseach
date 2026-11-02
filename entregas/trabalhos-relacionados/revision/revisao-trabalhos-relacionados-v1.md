# Avaliação do projeto de TCC I — 1ª revisão (Trabalhos Relacionados)

**Avaliador:** — | **Projeto avaliado:** *Projeto e avaliação experimental de uma camada arquitetural (harness) para integração de modelos de IA em aplicações web: custo de substituição de provedor e custo energético* (Vitor Manoel Alves da Silva; orientador: Prof. Dr. Sidarta Carvalho)
**Arquivo avaliado:** `2-textuais/trabalhos-relacionados.tex` (versão de 02/11/2026, commit `d5edb78`), lido junto com `2-textuais/1-introducao.tex` e `2-textuais/2-fundamentacao-teorica.tex` para o cruzamento de coerência e de repetição. O comentário de cabeçalho do `.tex` (registro da busca T09) foi usado como evidência do que foi lido e de como se buscou.
**Tipo de pesquisa:** implementação com experimento controlado (duas versões de uma aplicação web, medição de código e de energia). Sem pesquisa de campo com pessoas.
**Apoio:** rubrica do `revisor-tcc1` (critério 2.1) complementada pelo checklist de revisão da skill `trabalhos-relacionados-tcc`.

## Nota estimada

| Escopo | Pontos |
|---|---|
| Trabalhos Relacionados (1 critério) | **0,75 / 1,0** |
| Demais partes da rubrica | não avaliadas nesta revisão (Introdução em `entregas/introduction/revision/revisao-introducao-v1.md`; Fundamentação em `entregas/fundamentacao/revision/revisao-fundamentacao-v1.md`; Metodologia ainda em `\pendencia{}`) |

**Parecer (coerência interna, no recorte Introdução × Trabalhos Relacionados × Fundamentação):** apto, com duas ressalvas corrigíveis (seção "Coerência interna").
**Maior perda:** a lacuna se apoia em afirmações negativas ("não mede", "não compara") sobre trabalhos lidos só pelo resumo, e o protocolo da busca que a sustenta não aparece no texto compilado.

---

## 2. Trabalhos Relacionados (0,75 / 1,0)

O critério da rubrica é único (2.1), mas pede quatro verificações. A tabela mostra cada uma; a perda é uma só, sobre o critério.

| Verificação | Observações do avaliador |
|---|---|
| (a) Trabalhos acadêmicos | **Atende.** Os 21 trabalhos citados estão no `.bib` com venue revisado por pares: 5 anais IEEE, 10 publicações ACM (9 anais e o *ACM Computing Surveys*), 4 periódicos de outras editoras (2 no JSS, 1 no JSEP, 1 no *Future Internet*) e 2 anais da SBC (SEMISH). Ressalva sem perda: Ifath e Haque (2026) é resumo estendido (*Abstracts* do SIGMETRICS), o que o texto e o quadro já declaram. |
| (b) Atualidade | **Atende.** Critério adotado: até 5 anos (2021 em diante). 19 de 21 trabalhos são de 2023 a 2026; os dois de 2017 (Kaur et al.; Feitosa et al.) estão fora do domínio da IA e a exceção é declarada no texto (`trabalhos-relacionados.tex:74`). |
| (c) Relação explícita com o projeto | **Atende, com exceções pontuais.** Quase todo parágrafo traz relação, semelhança e diferença verificáveis (domínio, tipo de avaliação, direção do compromisso), e a síntese diz o que o trabalho herda de quem (`:386-390`). Exceções: (i) Nascimento et al. (2026) tem relação fraca ("compartilha a preocupação", `:303`) e não passa no teste "fez assim e posso fazer parecido"; (ii) Kaur et al. (2017) é usado como conceito ("problema estabelecido de arquitetura", `:187`), papel de Fundamentação, e a mesma frase está em `2-fundamentacao-teorica.tex:194`. |
| (d) Lacuna evidente | **Parcial.** A lacuna está bem formulada: conjunção de três características, com quadro em que só a proposta tem "Sim" nas três últimas colunas (`:382-385`). Mas ela depende de afirmações negativas sobre os trabalhos, e o cabeçalho declara: "Lidos: resumos de todos os trabalhos novos" e "NÃO lidos na íntegra: Kandogan et al." (`:49-51`). Afirmar pelo resumo que Morais et al. (2026), o trabalho mais próximo quanto ao objetivo, "não mede o esforço de fazê-la nem o compara com uma integração direta" (`:133-135`) é o ponto mais frágil do capítulo, porque resumo omite o que o artigo faz. |

**Veredito do critério 2.1: Parcial (−0,25, 25% — menor gravidade).** Motivos, além de (d):

1. **Protocolo da busca fora do texto compilado.** As strings, as contagens e o critério de inclusão ("mesma motivação, objeto ou método") estão só em comentário LaTeX (`:13-58`). O PDF informa bases, período e grupos de termos (`:63-75`), mas não as strings nem quantos trabalhos foram triados e incluídos. A frase da lacuna na Introdução (`1-introducao.tex:150-154`) remete a este capítulo como prova de repetibilidade, e o leitor do PDF não consegue repetir a busca.
2. **Cobertura da SBC declarada de forma ampla.** O texto diz que a busca usou a "Biblioteca Digital da Sociedade Brasileira de Computação" (`:66-67`) e a Introdução repete isso (`1-introducao.tex:151`), mas o cabeçalho registra que a busca geral exige login e que foi feita por evento (SBES, SBCARS, SEMISH, WSCAD/SSCAD, WCAMA, SBSI). Isso é cobertura parcial, e o texto deveria dizer quais eventos.
3. **Diferenças omitidas em relação a Mo et al. (2023), o precedente de que o trabalho mais herda.** Conferido no texto do artigo: o esforço de portabilidade foi medido com **42 estudantes** migrando código, por tempo, esforço percebido e sucesso da tarefa, e a abstração foi uma **biblioteca pronta** (Apache jclouds). A proposta mede o esforço só por métricas de código, aplicadas pelo próprio autor, sobre uma camada construída por ele. As duas diferenças afetam o que "herda o desenho com e sem a camada e as métricas de código" (`:386-387`) quer dizer e são as primeiras que a banca vai notar.

**Correção sugerida (em ordem de prioridade):**
- Ler na íntegra os trabalhos cujas negativas sustentam a lacuna: Morais et al. (2026), Kandogan et al. (2025), Matinpour et al. (2026) e Tripathy et al. (2026). Onde a leitura não for possível, trocar "não mede" por "o resumo não relata medição de…".
- Levar o protocolo para o texto: um parágrafo ou apêndice com as strings, as bases, a data, o número de resultados, a triagem e os incluídos, e citar os eventos da SBC efetivamente buscados.
- No parágrafo de Mo et al., acrescentar as duas diferenças (participantes × métricas de código; biblioteca pronta × camada própria) e dizer o que a proposta perde e ganha com cada uma. A justificativa já dada a Zhu et al. (isolar a camada, `:175-178`) serve para a segunda.
- Nascimento et al.: ligar a um uso concreto (por exemplo, a medição em CPU que a Fundamentação deixou em aberto, ver "Coerência interna") ou retirar. Kaur et al.: deixar a frase conceitual só na Fundamentação e, aqui, só a comparação.

### Observações sem efeito na nota

- **Quadro.** A coluna "Esforço de troca ou manutenibilidade" junta dois construtos. Assim, Xiao et al. (2025), que medem manutenibilidade, e Mo et al. (2023), que medem esforço de migração, aparecem com o mesmo "Sim", e a característica que a síntese diz ser exclusiva da proposta ("medir o esforço de trocar o provedor", `:384`) fica escondida. Sugestão: separar em duas colunas. O quadro tem 21 linhas em `\scriptsize` com `[h!]`. Não compilei o documento, então confira se cabe em uma página ou se deve usar `longtable`.
- **Extrapolação de Feitosa et al. (2017).** "o peso relativo da indireção cai quando o trabalho envolvido cresce, o que é o caso de uma requisição a um LLM" (`:229-231`) leva um achado sobre métodos Java para requisições a LLM. A Introdução trata uma extensão parecida como "analogia, e não um achado" (`1-introducao.tex:115-116`), e a mesma ressalva cabe aqui.
- **Barros et al. (2026).** "Em trabalho anterior do autor" (`:283`): o autor é segundo autor. "do qual o autor é coautor" é mais preciso.
- **Repetição entre capítulos.** O 1º parágrafo de 1.2 (`1-introducao.tex:135-146`) descreve Liu, Kandogan e Zhu com as mesmas limitações que o Cap. 2 detalha. O par Vellaisamy/Ifath da Introdução (`:107-116`) é quase o mesmo texto de `trabalhos-relacionados.tex:258-267`. Agora que o capítulo existe, a Introdução pode resumir a lacuna em duas frases e remeter a ele.
- **Termos antes da definição.** Com o capítulo antes da Fundamentação, "táticas arquiteturais", "requisição agêntica" e "NVML" aparecem antes de serem definidos. A ordem segue a rubrica; basta uma definição curta na primeira ocorrência ou uma remissão.

## Resumo de pontos

| Parte | Máx. | Obtido | Perdido | Critérios com perda |
|---|---|---|---|---|
| Trabalhos Relacionados | 1,0 | 0,75 | 0,25 | 2.1 (lacuna sustentada por negativas lidas no resumo; protocolo fora do texto; diferenças omitidas em Mo et al.) |

Situação acumulada das revisões (versões diferentes do texto, só informativo): Introdução, Objetivos e Formatação 2,90 / 3,5 (v1, 21/10); Fundamentação 1,45 / 2,0 (v1, 21/10); Trabalhos Relacionados 0,75 / 1,0 (esta); Defesa 1,0 atribuída; Metodologia 0 / 2,5, não redigida. As duas primeiras notas são de versões anteriores às correções de 02/11 e precisam de nova revisão para valer.

## Coerência interna

**Apto, com ressalvas.** Três cruzamentos:

- **(a) Objetivos × trabalhos relacionados.** Cada objetivo específico tem um trabalho de que herda algo: (a) responsabilidades da camada ← Liu et al. (2025); (b) duas versões equivalentes ← Mo et al. (2023); (c) custo de substituição por métricas de código ← Mo et al. (2023); (d) energia por NVML ← Barros et al. (2026). O objetivo (e), decidir se a redução do custo de substituição "justifica o seu custo energético", só tem Xiao et al. (2025) como precedente de pergunta, e o capítulo não diz se eles propõem alguma forma de comparar as duas grandezas. Isso reforça a perda 4.1-(i) da revisão da Fundamentação: o critério de decisão continua sem base.
- **(b) Trabalhos relacionados × fronteira da medição de energia.** O próprio capítulo afirma que a sobrecarga do hospedeiro (CPU) é custo oculto da inferência (Vellaisamy et al., `:258-260`) e que o trabalho herda o protocolo de Barros et al., só de GPU (`:283-286`, `:389-390`). Os dois juntos reforçam a ressalva já apontada na Fundamentação: o instrumento herdado não alcança o custo direto da camada. É corrigível (decidir o item A11). Há também uma tensão de uso: o quadro marca Vellaisamy et al. como "Energia medida: Não (latência)", mas a Fundamentação os cita como precedente para decompor o custo energético (`2-fundamentacao-teorica.tex:485-488`). Diga que o precedente é de decomposição de tempo, transposta para energia.
- **(c) Problema × lacuna.** Coerentes: a lacuna da Introdução ("ausência de medição controlada", `1-introducao.tex:148-159`) é a mesma conjunção que a síntese demonstra (`:382-385`). A única divergência é a lista de bases (a Introdução omite OpenAlex e Crossref e não diz que a SBC foi buscada por evento).

## Verificação de referências (amostragem)

| Referência | Resultado |
|---|---|
| Liu et al. (2025) — autores observam que benefícios e desvantagens "still require quantification" | **Verificada** no texto integral (`context/full-papers/1-s2.0-S0164121224003224-main.txt`, l. 1850). |
| Mo et al. (2023) — 7 funções, AWS e Google Cloud, jclouds, métricas de código, estudo com estudantes | **Verificada** no PDF dos autores. **Erro no `.bib`:** o primeiro autor é **Di Mo** (PDF e Crossref), não "David" (`referencias.bib:142`). |
| Feitosa et al. (2017) — 169 métodos, State/Strategy e Template Method, 2 projetos, achado sobre métodos grandes | **Verificada** (resumo no Crossref). |
| Xiao et al. (2025) — 3 táticas e 3 padrões, Online Boutique, 3 cargas, redução de até 5,6%, efeito negativo na manutenibilidade | **Verificada** (arXiv 2501.14402 e página do ICSA 2025). A nuance "as que também melhoraram o desempenho tenderam a prejudicar a manutenibilidade" (`:239-241`) **não foi verificada**. |
| Tripathy et al. (2026) — 4 frameworks, 2 SLMs, 150 execuções, razão de 9,4× | **Verificada** (arXiv 2512.09543; DOI e autores no Crossref, AGENT '26). |
| Matinpour et al. (2026) — latência 3–15% menor e energia 2–4% maior do LlamaIndex | Metadados **verificados** no Crossref (ICPE '26, p. 406–418). Os números **não foram localizados**: o Crossref não traz resumo e a busca não achou o texto. |
| Morais et al. (2026) | Metadados **verificados** no Crossref (MAS-GAIN '26). Conteúdo **não localizado** na busca. |
| Lin et al. (2026) — auditoria de dez gateways | Título **verificado** (arXiv 2604.21083) e venue no Crossref (IMC '26). Número de gateways **não verificado**. |
| Demais (13) | Não verificadas nesta revisão; o cabeçalho declara metadados conferidos no Crossref em 02/11/2026. |

Observação de formatação do `.bib` (critério 7, sem nota aqui): prenomes abreviados em algumas entradas (Vellaisamy, `:47`; Ifath, `:59`; parte de Kandogan, `:94`) e por extenso nas demais. A ABNT aceita os dois, desde que de forma uniforme.

Fontes da verificação: [Mo et al., PDF dos autores](https://faculty.washington.edu/wlloyd/papers/MoCloudCom2023proof.pdf) · [Crossref, Mo et al.](https://api.crossref.org/works/10.1109/cloudcom59040.2023.00040) · [Crossref, Feitosa et al.](https://api.crossref.org/works/10.1002/smr.1851) · [Xiao et al., arXiv](https://arxiv.org/pdf/2501.14402) · [Xiao et al., ICSA 2025](https://conf.researchr.org/details/icsa-2025/icsa-2025-papers/23/On-the-Effectiveness-of-Microservices-Tactics-and-Patterns-to-Reduce-Energy-Consumpti) · [SWEnergy, arXiv](https://arxiv.org/pdf/2512.09543) · [Crossref, Matinpour et al.](https://api.crossref.org/works/10.1145/3777884.3797017) · [Lin et al., arXiv](https://arxiv.org/pdf/2604.21083)

## Justificativa e comentários sobre a nota

O capítulo cumpre o que a rubrica pede: os trabalhos são acadêmicos e recentes, organizados pelas partes da pergunta de pesquisa, quase sempre com relação, semelhança e diferença concretas. Fecha com um quadro em que a proposta é linha e com um parágrafo que diz o que herda de cada trabalho. A perda está no que sustenta a lacuna. Ela é definida pelo que os outros trabalhos *não* fazem, e essas negativas vêm de resumos, inclusive para Morais et al. (2026), o trabalho mais próximo quanto ao objetivo. A busca que a Introdução cita como prova também não aparece no texto compilado. A terceira perda é o tratamento de Mo et al. (2023), o precedente de que o trabalho mais herda: o capítulo omite que lá o esforço foi medido com 42 desenvolvedores e com uma biblioteca pronta. Correções prioritárias: (1) ler na íntegra os trabalhos que sustentam a lacuna ou suavizar as negativas; (2) levar o protocolo da busca para o texto ou para um apêndice; (3) explicitar as diferenças em relação a Mo et al. e corrigir o prenome no `.bib`.

Premissas: avaliação restrita à Parte 2 da rubrica (1,0 ponto, critério único); atualidade de até 5 anos como referência; perda arredondada a múltiplo de 0,05; nota apresentada como estimativa. Referências verificadas: 8 por amostragem (tabela acima).
