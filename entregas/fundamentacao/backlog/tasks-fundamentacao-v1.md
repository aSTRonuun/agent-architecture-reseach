# Tasks de correção — Projeto e avaliação experimental de uma camada arquitetural (harness) para integração de modelos de IA em aplicações web: custo de substituição de provedor e custo energético
Origem: `revision/revisao-fundamentacao-v1.md` (1ª revisão, somente Fundamentação Teórica), nota estimada 1,45/2,0 no escopo avaliado | Parecer: apto, com ressalva de coerência (T01)
Total: 9 tasks (0 críticas, 0 altas, 4 médias, 5 baixas) | Pontos recuperáveis: 0,55

## Visão geral

| ID | Título | Tipo | Severidade | Pontos | Esforço | Depende de |
|---|---|---|---|---|---|---|
| T01 | Fundamentar a fronteira da medição de energia (GPU × CPU) | Coerência interna | Média | −0,15 | G | — |
| T02 | Fundamentar o critério de decisão do trade-off | Conteúdo ausente | Média | −0,15 | G | — |
| T03 | Fundamentar a variabilidade e a análise estatística das medições | Conteúdo ausente | Média | −0,10 | M | T01 |
| T04 | Eliminar trechos repetidos da Introdução | Coesão/argumentação | Média | −0,10 | M | — |
| T05 | Reduzir ressalvas de processo e remissões soltas à Metodologia | Redação | Baixa | −0,05 | P | — |
| T06 | Rever o par "extensional/intensivo" | Clareza/precisão | Baixa | 0 | P | T01 |
| T07 | Incluir conceito de equivalência funcional por testes | Conteúdo insuficiente | Baixa | 0 | M | — |
| T08 | Citar a definição de camada de abstração (2.3, §1) | Referência | Baixa | 0 | P | — |
| T09 | Acrescentar a fonte primária do modelo C4 | Referência | Baixa | 0 | P | — |

Soma dos pontos: T01 (0,15) + T02 (0,15) + T03 (0,10) + T04 (0,10) + T05 (0,05) = **0,55**, igual ao total perdido na revisão.

## Detalhamento

### T01 — Fundamentar a fronteira da medição de energia (GPU × CPU)
**Tipo:** Coerência interna | **Severidade:** Média | **Critério:** 4.4 Escopo e uso; Coerência interna (objetivo × referencial) | **Pontos:** −0,15 | **Esforço:** G
**Localização:** Fundamentação 2.5, §3 ("Por isso o trabalho mede a energia da GPU…"); Introdução 1.1, último parágrafo; Metodologia, Benchmark 2 (pendência A11, RAPL)
**Evidência:** a revisão aponta que a Introdução estima o trabalho da camada na CPU ("por até 10 ms a cerca de 100 W"), enquanto a 2.5 só fundamenta a telemetria de GPU (NVML), e a medição de CPU segue pendente.
**Problema:** o objetivo (d) mede o custo que a camada acrescenta; medindo só a GPU, o experimento capta o efeito indireto (número de chamadas, tamanho do contexto), não o custo direto da camada.
**Como resolver:**
1. Fechar o A11: medir também a CPU (RAPL) ou restringir o construto ao efeito indireto.
2. Na 2.5, definir a fronteira do sistema medido e justificá-la, usando Vellaisamy et al. (2026), que já trata da sobrecarga no hospedeiro.
3. Se medir CPU, fundamentar o RAPL com fonte verificável; se não, declarar a limitação e alinhar a estimativa da Introdução.
**Critério de aceite:** a 2.5 diz explicitamente quais componentes (GPU e/ou CPU) compõem a energia da requisição e por quê, sem contradizer a estimativa da Seção 1.1.
**Depende de:** —

### T02 — Fundamentar o critério de decisão do trade-off
**Tipo:** Conteúdo ausente | **Severidade:** Média | **Critério:** 4.1 Conceitos-chave; Coerência interna (objetivo (e) × referencial) | **Pontos:** −0,15 | **Esforço:** G
**Localização:** Fundamentação 2.6, §2; Quadro `qua:conceitos-uso`, linha do objetivo (e)
**Evidência:** a revisão aponta que a 2.6 só menciona "critério de decisão final, definido antes da coleta", sem base para confrontar grandezas de natureza diferente (linhas alteradas × joules).
**Problema:** o objetivo (e), que fecha a questão de pesquisa, não tem fundamento conceitual.
**Como resolver:**
1. Buscar referencial de análise de trade-offs arquiteturais ou de decisão multicritério; Bass et al. (2021), já no `.bib`, é o ponto de partida.
2. Escrever uma subseção curta com a abordagem adotada.
3. Atualizar a linha (e) do quadro-síntese.
**Critério de aceite:** existe subseção que define, com fonte, como os dois custos serão confrontados; o quadro-síntese a referencia.
**Depende de:** —

### T03 — Fundamentar a variabilidade e a análise estatística das medições
**Tipo:** Conteúdo ausente | **Severidade:** Média | **Critério:** 4.1 Conceitos-chave | **Pontos:** −0,10 | **Esforço:** M
**Localização:** Fundamentação 2.6, §2 ("procedimentos estatísticos … na Metodologia"); Metodologia, Benchmark 2 (pendências A14–A18)
**Evidência:** a revisão aponta ausência de conceitos de repetição, unidade amostral e tamanho de efeito, embora o efeito esperado seja menor que 1% da energia da requisição.
**Problema:** um efeito tão pequeno exige justificar teoricamente como distingui-lo do ruído; hoje o capítulo só adia o tema.
**Como resolver:**
1. Usar o capítulo de análise de Wohlin et al. (2024) e uma fonte sobre metodologia de medição de energia.
2. Definir conceitualmente unidade amostral, repetições e magnitude de efeito considerada relevante.
**Critério de aceite:** a 2.5 ou a 2.6 define, com fonte, os conceitos estatísticos que a Metodologia vai usar.
**Depende de:** T01

### T04 — Eliminar trechos repetidos da Introdução
**Tipo:** Coesão/argumentação | **Severidade:** Média | **Critério:** 4.3 Texto | **Pontos:** −0,10 | **Esforço:** M
**Localização:** 2.2.1, §1 (Parnas/Bass, Sculley); 2.3, §2 (Kandogan); 2.4.1, §1 (Rafique e Bindschaedler); 2.5, §1, §3 e §4 (Schwartz/Strubell, Fernández, "Estendê-las … é uma analogia")
**Evidência:** a revisão identifica cerca de 7 frases quase idênticas às da Seção 1.1.
**Problema:** a banca lê as duas versões em sequência, e a Fundamentação perde voz própria. A perda de −0,15 do critério 4.3 está dividida entre esta task (−0,10) e T05 (−0,05).
**Como resolver:**
1. Na Introdução, manter só a menção curta.
2. No Cap. 2, aprofundar cada trecho (mecanismo, condições, limitações) em vez de repetir a frase.
**Critério de aceite:** nenhuma frase do Cap. 2 tem mais de ~60% de sobreposição com uma frase da Introdução.
**Depende de:** —

### T05 — Reduzir ressalvas de processo e remissões soltas à Metodologia
**Tipo:** Redação | **Severidade:** Baixa | **Critério:** 4.3 Texto | **Pontos:** −0,05 | **Esforço:** P
**Localização:** todo o Cap. 2 (7 ocorrências de "na Metodologia"; "do autor" ×5; "não revisado por pares" ×2)
**Evidência:** a revisão aponta que as ressalvas e remissões repetidas dão ao texto tom de registro de auditoria.
**Problema:** interrompem a argumentação, e as remissões apontam para um capítulo ainda em `\pendencia{}`.
**Como resolver:**
1. Declarar uma única vez, na abertura do capítulo, a política sobre documentos técnicos e definições operacionais.
2. Trocar as remissões por `\ref{}` quando a Metodologia compilar.
**Critério de aceite:** cada ressalva aparece no máximo uma vez; todas as remissões apontam para seções existentes.
**Depende de:** —

### T06 — Rever o par "extensional/intensivo"
**Tipo:** Clareza/precisão | **Severidade:** Baixa | **Critério:** 4.3 Texto | **Pontos:** 0 | **Esforço:** P
**Localização:** Fundamentação 2.5, §2
**Evidência:** a revisão aponta terminologia do autor, sem fonte; "intensivo" tem outro sentido em física e "extensional" não é a forma usual.
**Problema:** convida objeção terminológica da banca sem acrescentar nada a "duração × potência média".
**Como resolver:**
1. Usar "efeito de duração" e "efeito de potência", ou citar fonte que use o par.
**Critério de aceite:** os termos têm fonte ou são autoexplicativos.
**Depende de:** T01

### T07 — Incluir conceito de equivalência funcional por testes
**Tipo:** Conteúdo insuficiente | **Severidade:** Baixa | **Critério:** 4.1 Conceitos-chave | **Pontos:** 0 | **Esforço:** M
**Localização:** Fundamentação 2.6, §1
**Evidência:** a revisão aponta que a 2.6 diz que a equivalência funcional "é o que permite atribuir a diferença observada à camada", sem dizer como ela é estabelecida; o objetivo (b) cita testes comuns às duas versões.
**Problema:** a equivalência sustenta a validade interna e não tem base conceitual.
**Como resolver:**
1. Acrescentar um parágrafo, com fonte de teste de software, sobre testes de regressão/aceitação como critério de equivalência.
**Critério de aceite:** existe parágrafo com fonte que define como a equivalência é verificada.
**Depende de:** —

### T08 — Citar a definição de camada de abstração
**Tipo:** Referência | **Severidade:** Baixa | **Critério:** 4.2 Fontes (observação sem perda) | **Pontos:** 0 | **Esforço:** P
**Localização:** Fundamentação 2.3, §1, primeira frase
**Evidência:** a revisão aponta que "Uma camada de abstração interpõe…" não tem citação.
**Problema:** é a definição central da seção e uma afirmação não trivial.
**Como resolver:**
1. Ancorar em Bass et al. (2021) ou Parnas (1972), já no `.bib`, após conferir o trecho exato.
**Critério de aceite:** a frase tem citação verificada.
**Depende de:** —

### T09 — Acrescentar a fonte primária do modelo C4
**Tipo:** Referência | **Severidade:** Baixa | **Critério:** 4.2 Fontes (observação sem perda) | **Pontos:** 0 | **Esforço:** P
**Localização:** Fundamentação 2.2.2
**Evidência:** a revisão aponta que o C4 é definido só por Mavrogiorgou et al. (2025), guia secundário não lido na íntegra (comentário do `.tex`).
**Problema:** a definição se apoia em fonte secundária.
**Como resolver:**
1. Adicionar a fonte de Simon Brown, criador do modelo, e manter Mavrogiorgou et al. como apoio.
**Critério de aceite:** o C4 é definido com a fonte primária.
**Depende de:** —

## Fora da revisão (não convertido)
- Cap. 3 (Trabalhos Relacionados) em `\pendencia{}`: ao redigi-lo, não repetir a descrição de Kandogan et al. (2025), Zhu et al. (2026) e Mo et al. (2023) já feita no Cap. 2.
- Conferir se a GPU (H100 ou H200) e a versão do Qwen3.6 (27B ou 35B) citadas na Introdução batem com o servidor efetivamente usado.

Premissas: severidade derivada das regras da skill. A ressalva de coerência (T01) não foi classificada como Crítica porque a revisão concluiu "apto" (desvio corrigível, não estrutural). As observações sem perda do critério 4.2 (que atende) viraram tasks Baixa (T08, T09). Quando um critério gerou várias tasks, a perda foi dividida sem dupla contagem: 4.1 = T02 (−0,15) + T03 (−0,10) + T07 (0); 4.3 = T04 (−0,10) + T05 (−0,05) + T06 (0); essa divisão é estimativa a partir do peso de cada motivo na revisão. Esforço estimado. A nova nota depende de nova avaliação.
