# T09 — Plano de busca para a lacuna (para executar depois)

Salvo em 13/10/2026. **Status: não iniciado.** Depende de respostas do autor (seção 4). Esta busca também cobre a T20 (bibliotecas e gateways como comparadores diretos), então deve ser feita uma vez só.

## 1. Objetivo
Substituir, em [1-introducao.tex](../../../2-textuais/1-introducao.tex) (1.2, parágrafo "A lacuna, portanto..."), a frase "não foram encontrados estudos que comparem..." por uma afirmação com **bases, termos e período** que outra pessoa consiga repetir. Se a busca achar um estudo que se encaixe, a afirmação é restringida, como a T09 já prevê.

**Critério de aceite da T09:** a frase informa bases, termos e período, de modo que outra pessoa possa repetir a busca.

## 2. Passos
1. **Redigir as *strings* de busca** para três grupos: (a) camada intermediária ou de abstração de provedor de LLM (harness, middleware, gateway, abstraction layer, scaffold); (b) as duas dimensões medidas (custo de substituição ou *vendor lock-in*, e energia ou consumo energético); (c) comparadores diretos da T20 (LangChain, LiteLLM, Vercel AI SDK e similares).
2. **Rodar nas bases abertas** que o Claude consegue consultar: OpenAlex, Crossref, dblp e a API do arXiv. Registrar, para cada uma, a *string* exata, a data da consulta e o número de resultados.
3. **O autor roda as mesmas *strings*** em Scopus, IEEE Xplore e ACM DL (ou Web of Science), pelo portal CAPES/UFC, e devolve as contagens e os títulos que pareçam relevantes.
4. **Triar** pelo critério de inclusão (seção 3), reescrever a frase da Introdução e restringir a afirmação se algum estudo se encaixar.
5. **Registrar tudo** numa tabela (base, *string*, data, resultados, triados, incluídos), no mesmo estilo de [t14-verificacao-numeros-e-fontes.md](../revision/t14-verificacao-numeros-e-fontes.md).

## 3. Critério de inclusão (proposto, a confirmar pelo autor)
Estudo empírico que compare, sob condições controladas, uma integração com camada intermediária e uma integração direta ao provedor, medindo **substituibilidade** (custo de troca de provedor) **ou** **energia**. Estudos que medem só uma das duas dimensões entram na triagem e podem forçar a restrição da frase ("nenhum mede as duas ao mesmo tempo").

## 4. Decisões pendentes do autor
1. **Acesso:** consegue entrar em Scopus, IEEE Xplore e ACM DL (ou Web of Science)? Se não, a frase declara só as bases abertas.
2. **Período:** proposta de 2023 até outubro de 2026.
3. **Critério de inclusão:** confirmar ou ajustar a seção 3.
4. **Opcional:** histórico do Consensus com os *prompts* e as datas, para entrar como busca exploratória.
5. **Preprints na triagem (a confirmar):** a regra do projeto é só citar como fonte validada o que foi revisado por pares. Para *triar*, a sugestão é incluir preprints, porque um preprint que meça a lacuna a enfraquece mesmo sem revisão. A citação no texto continua seguindo a regra.

## 5. O que já se sabe
- O histórico atual são 5 buscas no Consensus (20 resultados cada), sobre arquitetura/harness, lock-in, energia, retry e observabilidade ([consolidated_references.md](../../../context/planning/consolidated_references.md), "Histórico das buscas"). Foram exploratórias, para achar referências. Não registram datas nem os *prompts* exatos e não servem de base para a lacuna.
- **Candidato à triagem:** *Watts and Debts of Agentic Frameworks: An Empirical Study (Registered Report)*, arXiv 2606.10702. Planeja medir a energia de frameworks agênticos, mas é um plano sem resultados. Não foi verificado se foi aceito em algum venue.
- Gateways e frameworks têm medições de latência só em material de fornecedores e blogs. Na pesquisa da T10 não apareceu estudo revisado por pares que isole o overhead (de energia ou latência) de gateway ou framework.

## 6. Estado das tarefas em 13/10/2026
- **Feitas na sessão de 12–13/10:** T08, T10, T11, T12, T13, T14, T15, T16, T18, T19.
- **Pendentes:** T09 (este plano); T17 (precisa do PDF compilado no Overleaf); T20–T26 (seções ainda não escritas).
- **Não conferidas nessa sessão:** T01–T07.
