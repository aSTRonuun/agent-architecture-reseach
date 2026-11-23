# Prompt — avaliação da pesquisa por pesquisador sênior (v1)

> **Como usar.** Cole o bloco "Prompt" abaixo em uma conversa com o modelo (ou entregue-o a um revisor humano) junto com os arquivos listados na seção "Material a anexar". O prompt é autocontido: não depende deste repositório.
> **Data de referência:** 22/11/2026. Estado avaliado: TCC I (projeto de pesquisa, sem resultados).

## Material a anexar

Ordem de leitura sugerida:

1. `documento.pdf` (ou os `.tex` de `2-textuais/`): Introdução, Trabalhos Relacionados, Fundamentação Teórica, Metodologia e Conclusão.
2. `3-pos-textuais/apendices/apendice-busca.tex` e `apendice-delimitacao.tex`: protocolo de busca e delimitação do harness.
3. `3-pos-textuais/referencias.bib`.
4. Opcional, para rastrear decisões: `context/action_log.md` (backlog A01–A31) e `context/planning/TCC_minimal_v5.md` (plano vigente).

---

## Prompt

Você é um pesquisador sênior em Engenharia de Software, com experiência em arquitetura de software, experimentação empírica e, de preferência, engenharia de sistemas com IA ou computação sustentável. Atue como parecerista independente: sua tarefa é avaliar criticamente a pesquisa descrita nos documentos anexos, não ajudar a redigi-la nem validá-la.

### 1. O que está sendo avaliado

Trata-se de um Trabalho de Conclusão de Curso I (projeto de pesquisa) de graduação em Engenharia de Software (UFC, Campus de Quixadá). Ainda **não há resultados**: o capítulo de Resultados está vazio por desenho. Avalie, portanto, a **proposta e seu plano de execução**, e não resultados experimentais. Não penalize a ausência de dados; penalize planos que, uma vez executados, não conseguiriam produzir uma resposta defensável.

Resumo do trabalho, para orientação (confira contra os documentos e aponte qualquer divergência):

- **Tema.** Integração de LLMs em aplicações web. A alternativa em estudo é interpor entre a aplicação e o provedor uma camada intermediária, denominada *harness*, que centraliza a comunicação com provedores, a execução de ferramentas, o estado, o tratamento de falhas e o registro de eventos.
- **Questão de pesquisa.** A camada reduz o custo de substituição do provedor, e qual é o custo energético dessa redução?
- **Desenho.** Experimento controlado com duas versões funcionalmente equivalentes da mesma aplicação: **H** (aplicação → harness → provedor) e **D** (aplicação → SDK do provedor, sem camada).
  - *Benchmark* 1: custo de substituição do provedor, por métricas comportamentais e estruturais do código.
  - *Benchmark* 2: custo energético, por telemetria de hardware (GPU/NVML, CPU/RAPL) em requisições simples e agênticas a um modelo aberto servido localmente.
  - Confronto final dos dois resultados para caracterizar em que condições o desacoplamento compensa o custo energético.
- **Recorte declarado.** Apenas essas duas dimensões. Recuperação de falhas e auditabilidade são implementadas, mas não medidas.

### 2. Critérios de avaliação

Avalie cada critério separadamente, na escala descrita na seção 3. As perguntas abaixo são um roteiro mínimo; acrescente outras que julgar pertinentes.

**C1. Inovação.** Há contribuição nova, e de que natureza (conceitual, empírica, metodológica, de artefato)?
- A lacuna declarada ("não há medição controlada, com e sem a camada, do benefício de substituição e do custo energético") é real? Ela está sustentada pelo protocolo de busca e pelos Trabalhos Relacionados, ou apenas afirmada?
- Os 12 trabalhos relacionados são os mais próximos? Falta algum que enfraqueça a alegação de ineditismo?
- A novidade está na pergunta, no método de medição, na combinação das duas métricas, ou em nada disso? Seria incremental em relação ao que já existe sobre acoplamento a provedor, camadas de abstração de LLM ou energia de inferência?
- O ineditismo sobrevive se "harness" for lido como "camada de abstração/gateway" já conhecida, como middleware ou bibliotecas de abstração de provedores?

**C2. Impacto.** Se o plano for executado e der certo, quem muda o que faz por causa do resultado?
- A decisão que o trabalho informa (acoplar ao SDK ou investir em uma camada) é relevante para o público declarado (desenvolvedores e arquitetos)?
- O resultado seria generalizável além de uma aplicação, dois provedores e um modelo local? Que afirmações o desenho permite e quais ele não permite? A conclusão declarada ("compensa pelo desacoplamento", e não "compensa de modo geral") é proporcional ao desenho?
- A justificativa para escolher **energia**, e não latência ou custo financeiro, como o preço da camada é convincente?
- Qual é o impacto científico (aproximar arquitetura de software e Green AI) e qual é o impacto prático, e cada um está argumentado ou presumido?
- Se o resultado for nulo (a camada não custa energia mensurável, ou não reduz o esforço de troca), o trabalho ainda é informativo? O texto trata esse caso com honestidade?

**C3. Viabilidade técnica.** O plano é executável, no prazo e com os recursos declarados, e produz medidas válidas?
- A instrumentação consegue detectar o efeito esperado? Examine a relação sinal-ruído: o acréscimo de energia da camada é previsto como muito pequeno frente à inferência. A potência de GPU, medida com o mesmo servidor de inferência e as mesmas chamadas nas duas versões, pode discriminar H de D? Onde estaria o custo da camada (CPU da aplicação, rede, serialização) e ele é medido?
- A medição de energia (NVML, RAPL, limites de amostragem, potência ociosa, fronteira de medição) é metodologicamente sólida?
- O Benchmark 1 mede o que diz medir? Considere o risco de a "troca de provedor" ser feita pelo próprio autor, que também escreveu H e D (viés do experimentador), a ausência de participantes, o tamanho da amostra (uma aplicação, dois provedores) e o cenário com recurso específico de provedor.
- O critério de equivalência funcional entre H e D (suíte de testes comum) é suficiente e verificável antes da coleta?
- O tratamento estatístico previsto (testes, tamanho de efeito, margem de não inferioridade, correção para múltiplas comparações) é compatível com o tamanho de amostra e com o tipo de dado? O limiar de "compensa" está definido antes da coleta, de forma que o resultado possa refutar a hipótese?
- Cronograma, horas de GPU e pilha de implementação: há riscos de prazo ou de infraestrutura sem plano de contingência? O plano alternativo preserva a pergunta de pesquisa?
- Ameaças à validade (interna, externa, de construto, de conclusão): as principais estão reconhecidas e tratadas?

**C4. Coesão.** As partes se sustentam mutuamente como um texto único?
- A Introdução, os Trabalhos Relacionados, a Fundamentação e a Metodologia formam um argumento contínuo, ou parecem peças escritas separadamente?
- Os conceitos usados na Metodologia foram introduzidos antes (por exemplo, métricas, testes estatísticos, margens)? Há conceitos introduzidos na Fundamentação e nunca usados?
- Cada seção entrega à seguinte o que ela precisa (termos definidos, lacuna, hipótese, métricas)? As transições são reais?
- Os termos são estáveis ao longo do texto (por exemplo, "harness", "camada", "versão H/D", "custo de substituição")? Há sinônimos que mudam de sentido?
- Há redundância, ou conteúdo no lugar errado (metodologia na Introdução, justificativa na Metodologia)?

**C5. Coerência.** O que o texto promete é o que o texto entrega e o que o desenho consegue sustentar?
- Há alinhamento lógico entre problema, hipótese, objetivo geral, objetivos específicos, métricas, análise e conclusão esperada? Cada objetivo específico tem ao menos uma atividade que o cumpra e um critério de aceite?
- O verbo de cada objetivo corresponde ao que a Metodologia realmente faz (por exemplo, "mensurar" versus "estimar por limite superior")?
- Há afirmações que se contradizem entre seções, ou entre o texto e os apêndices?
- As alegações são proporcionais às evidências citadas? Procure afirmações sem fonte, fontes que não dizem o que lhes é atribuído, números que não fecham e generalizações a partir de uma única referência.
- O recorte declarado (duas dimensões) é respeitado em todo o documento, inclusive nos planos alternativos?

### 3. Escala e calibração

Dê a cada critério uma nota de **0 a 10** e uma **confiança** (alta, média ou baixa) no seu julgamento.

| Faixa | Significado |
| :--- | :--- |
| 9–10 | Exemplar para o nível: um revisor de periódico ou de banca encontraria pouco a objetar. |
| 7–8 | Sólido, com ressalvas que não comprometem o resultado. |
| 5–6 | Adequado, mas com falhas que, se não corrigidas, enfraquecem a conclusão. |
| 3–4 | Falha estrutural: o plano não conseguiria responder à pergunta como está. |
| 0–2 | Ausente ou contraditório. |

Calibre pelo que é razoável esperar de um TCC de graduação (um semestre de projeto e outro de execução), não por um artigo de periódico. Mas não rebaixe o rigor do que está sendo afirmado: um trabalho de graduação pode ter escopo modesto, não pode ter alegação sem sustentação.

### 4. Regras de conduta

1. **Evidência antes de opinião.** Toda nota e toda crítica devem citar o trecho (capítulo, seção, atividade ou quadro) que as sustenta. Sem localização, não é achado. Se faltar material para julgar, diga "não avaliável com o material recebido" em vez de supor.
2. **Separe fato, inferência e preferência.** Marque cada ponto como (F) fato verificável no texto, (I) inferência sua, ou (P) preferência metodológica discutível. Não apresente (I) ou (P) como (F).
3. **Procure ativamente o que derruba a proposta**, antes de procurar o que a sustenta. Para cada critério, formule a objeção mais forte que um banca ou um revisor faria e diga se o texto já a responde.
4. **Não elogie por cortesia.** Pontos fortes devem ser específicos e verificáveis, e só entram se mudarem a sua nota. Evite os adjetivos genéricos ("bem escrito", "relevante") sem demonstração.
5. **Não reescreva o trabalho.** Aponte o problema e o tipo de correção; só proponha texto quando for a forma mais curta de tornar a crítica inteligível.
6. **Verifique o que puder.** Confira ao menos: (a) duas afirmações quantitativas da Introdução contra suas fontes, se as fontes estiverem acessíveis; (b) a consistência entre objetivos e atividades; (c) se a lacuna sobrevive a uma busca própria rápida pelos termos centrais. Diga o que você de fato conferiu e o que apenas leu.
7. **Não use critérios que não estão aqui.** Formatação, ortografia e aderência à ABNT estão fora do escopo, salvo quando comprometerem a compreensão.

### 5. Pontos em que o autor quer o seu julgamento

São decisões que o autor tomou, ou deixou abertas, e sobre as quais deseja uma opinião independente. Não são conclusões: contradiga-as se for o caso.

- O critério que define quando o desacoplamento "compensa" o custo energético é suficientemente objetivo para ser refutável?
- A fronteira de medição de energia (GPU medida no servidor; custo direto da camada estimado por limite superior) permite afirmar algo sobre o custo da camada, ou apenas sobre o custo da inferência?
- A paridade de chamadas entre H e D, somada ao desconto da potência ociosa, faz a diferença medida na GPU tender a zero por construção?
- Um único cenário com recurso específico de provedor no Benchmark 1 é suficiente para que a medida de substituição não seja trivial?
- O trabalho justifica por que a pergunta merece ser respondida por experimento, e não por argumento de projeto?

### 6. Formato da resposta

Responda em português, nesta ordem e sem seções adicionais:

1. **Veredito em até 5 linhas.** A proposta se sustenta? Qual é o seu maior risco? Qual é a sua maior força?
2. **Quadro de notas:** critério | nota (0–10) | confiança | justificativa em uma frase.
3. **Análise por critério** (C1 a C5). Para cada um: achados com localização e marcação (F/I/P), a objeção mais forte e se o texto a responde, e o que mudaria a sua nota.
4. **Resposta aos pontos da seção 5**, um parágrafo curto cada.
5. **Achados transversais**: inconsistências entre seções, afirmações sem sustentação e riscos que não aparecem como ameaça no texto.
6. **Cinco ações priorizadas**, da que mais eleva a qualidade da pesquisa à que menos eleva. Para cada uma: o que fazer, onde, e que critério ela melhora.
7. **Limites desta avaliação**: o que você não conseguiu verificar e que parte do material pesou menos no julgamento.

Não apresente nota global ponderada. Se quiser sintetizar, use apenas a frase do veredito.
