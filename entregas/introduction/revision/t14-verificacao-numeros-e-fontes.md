# T14 — Registro de verificação de números e fontes (Introdução)

Verificado em 13/10/2026. Método: páginas e resumos das fontes (WebFetch), metadados no Crossref (todos os DOIs do `.bib`) e resumos no OpenAlex/arXiv. Onde só o resumo foi lido, a coluna "Nível" diz "resumo".

## 1. Números atribuídos a fontes de mercado

| Afirmação no texto | Fonte | Onde conferido | Resultado |
|---|---|---|---|
| Uso ou intenção de uso de IA: 76% (2024) → 84% (2025) | Stack Overflow 2025 | Seção 3.1 "Sentiment and usage" | Confere |
| 31% já usam agentes de IA | Stack Overflow 2025 | Seção 3.3 "AI agents" | **Discrepância corrigida.** A página não traz esse número. Ele é a soma das respostas afirmativas (14,1% diariamente + 9% semanalmente + 7,8% mensal ou infrequente ≈ 30,9%). Texto agora diz "cerca de 31% ... ao menos de forma eventual". |
| Gasto com APIs de LLM: US$ 3,5 bi (nov/2024) → US$ 8,4 bi (meados de 2025), "mais que dobrou em seis meses" | Menlo Ventures | Key Findings; nota 1 | Confere (a página diz "more than doubled in just six months"). Nota 1: o valor exclui receita de produtos de consumo e aplicações empresariais dos laboratórios. |
| OpenAI 50% (fim de 2023) → 25% (meados de 2025); Anthropic 32%; Google 20% | Menlo Ventures | Seção "Anthropic Surpasses OpenAI in Enterprise Usage"; nota 3 | Confere. As participações medem **uso em produção**, não gasto, e o texto fala em "uso corporativo". |
| 11% trocaram de provedor no último ano; 66% só atualizaram o modelo no mesmo provedor | Menlo Ventures | Key Findings; seção "Enterprises Switch Models for Performance, Not Price" | Confere. Os 23% restantes não trocaram de modelo. |
| Amostra e natureza da fonte | Menlo Ventures | Nota 2 do relatório; marcação na seção de participação | Cerca de 150 decisores técnicos (o corpo diz "over 150", a nota diz "150"), de 30/06 a 10/07/2025; empresas com 5.000+ funcionários e startups com ao menos US$ 5 mi captados. Relatório de firma de capital de risco, publicado em 31/07/2025. **A Anthropic é marcada no próprio relatório como "Menlo Ventures portfolio company".** Natureza agora declarada no texto. |
| Centros de dados: ~415 TWh em 2024 (~1,5% da eletricidade mundial); ~945 TWh em 2030, "mais que dobra" | IEA, *Energy and AI* | Resumo executivo, seções "Os data centers representam uma pequena parcela..." e "A demanda por eletricidade por data centers mais que dobra até 2030" (cópia em Markdown fornecida pelo autor; o site bloqueou a consulta direta) | Confere nos três números. |
| "com a IA como principal vetor de crescimento" | IEA, *Energy and AI* | Resumo executivo, seção "A demanda ... mais que dobra até 2030" | Confere: "A IA é o motor mais importante desse crescimento, junto com a crescente demanda por outros serviços digitais". Ressalva de contexto: globalmente os data centers são cerca de um décimo do crescimento da demanda de eletricidade até 2030. O texto não afirma o contrário. |

## 2. Números atribuídos a artigos acadêmicos

| Afirmação no texto | Fonte | Onde conferido | Resultado |
|---|---|---|---|
| Geração de texto 0,047 kWh e classificação 0,002 kWh por mil inferências | Luccioni et al. (2024), FAccT '24 | Tabela 2 ("Mean and standard deviation of energy per 1,000 queries") | Confere (média; desvios 0,03 e 0,001). Hardware: nó de 8 GPUs A100 80 GB na AWS. A seção 4.1 dá a **mediana** da geração de texto como 0,042 kWh. |
| Estimativas por FLOPs subestimam o consumo; otimizações reduzem a energia em até 73% | Fernandez et al. (2025), ACL 2025 | Resumo | Confere. O resumo cita também "theoretical GPU utilization". Venue ACL 2025 confirmado pelo DOI no Crossref (ACL Anthology). |
| Sobrecarga de orquestração no processador hospedeiro | Vellaisamy et al. (2026), ISPASS | Resumo | Confere para **latência** (texto ajustado na T10). O resumo não trata de energia. |
| Agentes de IA vs. IA agêntica (multiagente) | Sapkota et al. (2026), *Information Fusion* | Resumo | Confere: a colaboração multiagente é traço da IA agêntica. |
| Comparação de funções *serverless* com biblioteca de abstração vs. APIs nativas | Mo et al. (2023), CloudCom | Resumo | Confere (Apache jclouds vs. APIs de plataforma, sete funções na AWS e no Google Cloud). |
| *Middleware* como camada reutilizável que absorve a heterogeneidade | Issarny et al. (2007), FOSE '07 | Resumo | Confere no essencial: camada com "reusable solutions to recurring problems such as heterogeneity, interoperability...". "Entre plataformas" é paráfrase do autor. |
| Abordagens de interoperabilidade e portabilidade "baseadas em camadas intermediárias" | Kaur et al. (2017), *ACM Computing Surveys* | Resumo | **Não sustentado pelo resumo** (revisão de mais de 120 artigos sobre interoperabilidade e portabilidade contra *lock-in*; *middleware* e padrões não aparecem). Corrigido: "propostas para reduzir essa dependência". O corpo do artigo não foi lido. |

## 3. Existência e dados bibliográficos (Crossref)

Todos os DOIs do `.bib` resolvem, e título, autores, venue, volume e ano conferem. Dados que faltam no `.bib` e que o Crossref fornece (insumo da T18):

| Chave | Páginas no Crossref |
|---|---|
| vellaisamy2026 | 28–38 (IEEE ISPASS 2026, 26/04/2026) |
| ifath2026 | 91–93 (volume de *abstracts* do SIGMETRICS 2026) |
| kandogan2025 | 18–27 (IEEE ICDEW 2025) |
| mo2023 | 193–199 (IEEE CloudCom 2023) |
| barros2026 | 1028–1033 (SEMISH 2026) |

Venues confirmados (insumo da T16): Liu et al. = *Journal of Systems and Software* v. 220, art. 112278; Vellaisamy = ISPASS 2026; Ifath = SIGMETRICS 2026 (resumo estendido); Mo = CloudCom 2023. Zhu et al. (T15): o DOI `10.3390/fi18060326` resolve para *Future Internet* v. 18, n. 6, art. 326, com os autores e o título do `.bib`; a limitação atribuída a esse artigo ainda não foi conferida no texto.

## 3.1 T15, T16 e T18 (13/10/2026)

**T15 — Zhu et al. (2026).** DOI `10.3390/fi18060326` resolve (Crossref e OpenAlex): *Future Internet* v. 18, n. 6, art. 326, 15/06/2026, autores Zhu, Liu, Yu, Zhang, acesso aberto (CC-BY). O resumo confere com o uso na Introdução: compara frameworks de orquestração de agentes (LangGraph, CrewAI, AutoGen, OpenAI Agents SDK) em gerenciamento de estado, custo de tokens e recuperação de falhas. **Não consegui abrir o texto** (MDPI e Preprints.org devolvem HTTP 403), então a passagem sobre fornecedores não foi conferida na fonte. O que o registro do projeto sustenta ([consolidated_references.md](../../../context/planning/consolidated_references.md), R11) é que o artigo marca com † os achados reportados por fornecedores para distingui-los de evidência revisada por pares. A frase da Introdução foi ajustada a isso ("distinguem os achados reportados pelos próprios fornecedores dos sustentados por avaliação revisada por pares"); antes ela dizia que "parte relevante das alegações ... provém dos fornecedores", o que é inferência além do †. **Número de frameworks (resolvido):** o R11 diz seis e o resumo no OpenAlex diz quatro. O trecho do corpo do artigo fornecido pelo autor resolve: "We compare six leading frameworks (LangGraph, CrewAI, AutoGen/Microsoft Agent Framework, OpenAI Agents SDK, MetaGPT, and DSPy) along axes directly relevant to practitioners: state-management granularity, token-cost structure, failure-recovery options, and design philosophy." Valem os seis; a contagem do resumo parece ser uma inconsistência do próprio artigo. Esse trecho não menciona a marcação †, então a passagem sobre fornecedores continua sem conferência direta.

**T16 — venues.** Os quatro estão confirmados por DOI no Crossref, e nenhum precisa ser marcado como preprint: Liu et al. = *Journal of Systems and Software* v. 220, art. 112278 (fev/2025); Vellaisamy et al. = IEEE ISPASS 2026 (arXiv traz "Accepted at IEEE ISPASS 2026"); Ifath e Haque = volume de *abstracts* do ACM SIGMETRICS 2026 (resumo estendido, como já anotado no `.bib`); Mo et al. = IEEE CloudCom 2023. O `.bib` já indicava esses venues; não houve mudança de versão.

**T18 — páginas e URL.** Páginas incluídas no `.bib`: Vellaisamy 28–38; Ifath 91–93; Kandogan 18–27; Mo 193–199; e também Barros 1028–1033 (conferidas no Crossref). A URL do Stack Overflow no `.bib` (`https://survey.stackoverflow.co/2025/ai`) está íntegra e abre; a quebra "<https: //survey…" aparecia só na conversão do PDF para Markdown. Falta conferir no PDF compilado se a linha não quebra no meio da URL.

## 4. Não reconferido nesta rodada

- **Sem DOI:** Bass et al. (livro, 4ª ed., 2021) e Sculley et al. (NeurIPS 2015, pp. 2503–2511). Dados bibliográficos mantidos como estão. O conteúdo atribuído (modificabilidade como atributo de qualidade; *glue code*) não foi reaberto.
- **Existência confirmada, conteúdo não reaberto:** Parnas (1972), Schwartz et al. (2020), Strubell et al. (2019), Wohlin et al. (2024), Kandogan et al. (2025), Liu et al. (2025).
- **Barros et al. (2026):** trabalho do próprio autor. Existência e páginas confirmadas, e o protocolo de telemetria citado depende do conteúdo que só o autor conhece.
