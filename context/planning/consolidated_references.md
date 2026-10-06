---
name: referencias_tcc_consolidado
description: Documento único de referências do TCC (harness / Green AI) — 21 referências validadas com link oficial reverificado, uso mapeado por capítulo/seção do TCC, lista de backups e lista de rejeitadas. Substitui as versões anteriores.
---
 
# Referências do TCC — Harness / Green AI (documento consolidado)
 
**Título do TCC:** "Projeto e avaliação experimental de uma camada arquitetural desacoplada agêntica (harness) para integração de modelos de IA em aplicações web".
 
**Critério de inclusão:** publicação revisada por pares confirmada, ou livro de editora acadêmica. arXiv isolado não conta como validado.
 
**Verificação:** metadados reverificados individualmente em 09–10/09/2026 contra o registro CrossRef de cada DOI e/ou a página oficial da editora. Todos os links deste documento apontam para a **fonte oficial** (DOI resolvido, editora ou biblioteca digital) — os links de agregadores (consensus.app) das versões anteriores foram substituídos.
 
**Situação:** 21 referências validadas (meta era 15). As quatro dimensões avaliadas no TCC (substituibilidade, eficiência energética, recuperação de falhas, auditabilidade) têm cobertura própria. Duas pendências abertas — ver §6.
 
---
 
## 1. Índice rápido — 21 referências validadas
 
| # | Referência | Veículo (tipo) | Uso principal no TCC |
|---|---|---|---|
| R1 | Wohlin et al. (2024) | Springer (livro) | Cap. 4 — desenho experimental e §6.3 Ameaças à validade |
| R2 | Luccioni, Jernite & Strubell (2024) | ACM FAccT (conf.) | Cap. 2 e 3 — Green AI; §6.2 B2 |
| R3 | Fernandez et al. (2025) | ACL (conf.) | Cap. 2/3 — justifica medição real (NVML) vs. estimativa |
| R4 | Wilkins, Keshav & Mortier (2024) | ACM SIGEnergy EIR (periódico) | Cap. 3 — modelos de energia por carga |
| R5 | Vellaisamy et al. (2026) — TaxBreak | IEEE ISPASS (conf.) | §6.2 B2 / §6.4 — overhead extensional vs. intensivo |
| R6 | Ifath & Haque (2026) | ACM SIGMETRICS (abstract) | §6.2 B2 — energia em workflows agênticos multi-requisição |
| R7 | Barros et al. (2026) — SEMISH | SBC / CSBC (conf.) | §6.4 — base metodológica reaproveitada ⚠️ |
| R8 | Sapkota, Roumeliotis & Karkee (2026) | Information Fusion, Q1 | Cap. 2 §2.1 — terminologia "agente" vs. "agêntico" |
| R9 | Chang & Geng (2025) — SagaLLM | PVLDB, Q1 | Cap. 2/3 — estado e recuperação; complementa B3 |
| R10 | Kandogan et al. (2025) — Blueprint | IEEE ICDEW (workshop) | Cap. 3 — arquitetura concorrente sem avaliação empírica |
| R11 | Zhu et al. (2026) | Future Internet, Q2 | Cap. 3 — tabela comparativa de frameworks |
| R12 | Issarny, Caporuscio & Georgantas (2007) | FOSE @ ICSE (survey convidado) | Cap. 2 — harness como middleware |
| R13 | Kaur, Sharma & Kahlon (2017) | ACM CSUR, Q1 | Cap. 3 — lock-in via camada intermediária (fora de IA) |
| R14 | Mo et al. (2023) | IEEE CloudCom (conf.) | §6.2 B1 — precedente empírico mais próximo |
| R15 | Mendonça et al. (2020) | IEEE ICSA (conf.) | §6.2 B3 — fundamenta Retry/Circuit Breaker |
| R16 | Sedghpour, Klein & Tordsson (2022) | ACM/SPEC ICPE (conf.) | §6.2 B3 — desenho experimental e parâmetros |
| R17 | Aderaldo et al. (2024) | Softw. Pract. Exper., Q2 | §6.2 B3 — precedente metodológico direto |
| R18 | Mace, Roelke & Fonseca (2018) — Pivot Tracing | ACM TOCS (periódico) | Cap. 2/3 e B4 — reconstrução causal cross-tier |
| R19 | Hassan et al. (2020) — OmegaLog | NDSS (conf. top-tier) | Cap. 2/3 e B4 — proveniência multicamada |
| R20 | Phiri (2025) | ACM proceedings (venue modesto) | Cap. 2 — definição operacional de auditabilidade ⚠️ |
| R21 | Liu et al. (2025) — Agent Design Pattern Catalogue | J. Systems and Software, Q1 | Cap. 2 §2.1 e Cap. 3 — responsabilidades e padrões da camada agêntica |
 
*(R7 e R20 carregam ressalva; ver §6.)*
 
**Nota de contagem:** a lista nominal tem **21 entradas**. As versões anteriores deste arquivo afirmavam "19 referências validadas" enquanto a lista já trazia 20 nomes — discrepância herdada, agora corrigida. R7 e R20 permanecem validadas mas com ressalva.
 
---
 
## 2. Referências por bloco temático
 
### 2.1 Metodologia experimental
 
**R1 — WOHLIN, C.; RUNESON, P.; HÖST, M.; OHLSSON, M. C.; REGNELL, B.; WESSLÉN, A. *Experimentation in Software Engineering*. Springer Berlin Heidelberg, 2024.**
- DOI / link oficial: https://doi.org/10.1007/978-3-662-69306-3
- **Conteúdo:** livro-texto de referência sobre experimentos controlados em Engenharia de Software; origem da classificação clássica de ameaças à validade (interna, externa, de construto, de conclusão).
- **Onde usar:** Cap. 4 (Metodologia) — justifica o formato "estudo de caso controlado" e estrutura literalmente a seção §6.3 do planejamento, cujos quatro blocos seguem essa taxonomia.
- **Verificação (09/09/2026):** CrossRef confirma tipo *book*, Springer Berlin Heidelberg, 2024, seis autores na ordem acima.
### 2.2 Eficiência energética / Green AI (Benchmark 2)
 
**R2 — LUCCIONI, S.; JERNITE, Y.; STRUBELL, E. Power Hungry Processing: Watts Driving the Cost of AI Deployment? In: *ACM Conference on Fairness, Accountability, and Transparency (FAccT '24)*, 2024.**
- DOI / link oficial: https://doi.org/10.1145/3630106.3658542 — página ACM: https://dl.acm.org/doi/10.1145/3630106.3658542 (preprint: arXiv:2311.16863)
- **Conteúdo:** mede e compara consumo energético entre modelos e tarefas de IA, incluindo inferência de LLM, propondo metodologia de benchmarking de potência/energia por tarefa.
- **Onde usar:** Cap. 2 (fundamentação de Green AI: potência instantânea vs. energia total) e Cap. 3 (medição energética); ancora a escolha das métricas primárias do Benchmark 2 (J/requisição, J/token).
- **Verificação:** CrossRef confirma título, três autores, FAccT '24, ACM, 2024, *proceedings-article*.
**R3 — FERNANDEZ, J.; NA, C.; TIWARI, V.; BISK, Y.; LUCCIONI, S.; STRUBELL, E. Energy Considerations of Large Language Model Inference and Efficiency Optimizations. In: *Proceedings of the 63rd Annual Meeting of the ACL (Volume 1: Long Papers)*, 2025.**
- DOI / link oficial: https://doi.org/10.18653/v1/2025.acl-long.1563 — ACL Anthology: https://aclanthology.org/2025.acl-long.1563/
- **Conteúdo:** analisa sistematicamente o efeito energético de otimizações de inferência (frameworks, estratégias de decodificação, arquitetura de GPU, paralelismo); mostra que estimativas ingênuas baseadas em FLOPs subestimam significativamente o consumo real, e que otimizações adequadas reduzem energia em até 73%.
- **Onde usar:** Cap. 2/3 e §6.2 (B2) — é o argumento direto para o TCC medir energia real via NVML em vez de estimar por FLOPs; também sustenta o gating de corretude (§6.4), já que ganho energético sem controle de qualidade é artefato de otimização.
- **Verificação:** CrossRef confirma ACL 2025, seis autores. **Correção mantida:** o CSV do Consensus classificava como arXiv puro — é publicação formal revisada por pares.
**R4 — WILKINS, G.; KESHAV, S.; MORTIER, R. Offline Energy-Optimal LLM Serving: Workload-Based Energy Models for LLM Inference on Heterogeneous Systems. *ACM SIGEnergy Energy Informatics Review*, 2024.**
- DOI / link oficial: https://doi.org/10.1145/3727200.3727217
- **Conteúdo:** modelos de energia por carga de trabalho para servir LLMs em sistemas heterogêneos, com medição empírica de energia por requisição/token.
- **Onde usar:** Cap. 3 (trabalhos relacionados de medição energética) e, opcionalmente, §6.4 como referência complementar ao protocolo de telemetria.
- **Verificação:** CrossRef registra como *journal article* no ACM SIGEnergy Energy Informatics Review (o trabalho foi apresentado no HotCarbon 2024; o DOI aponta para a versão de periódico — citar como periódico).
**R5 — VELLAISAMY, P.; TRIPATHI, S.; NATARAJAN, V.; THENARASU, S. S.; BLANTON, S.; SHEN, J. P. TaxBreak: Unmasking the Hidden Costs of LLM Inference Through Overhead Decomposition. In: *2026 IEEE International Symposium on Performance Analysis of Systems and Software (ISPASS)*, 2026.**
- DOI / link oficial: https://doi.org/10.1109/ispass69572.2026.00014
- **Conteúdo:** decompõe o overhead de orquestração visível no host (tradução de framework, tradução de biblioteca CUDA, tempo de lançamento de kernel) separando-o do trabalho executado no device; validado em H100/H200.
- **Onde usar:** §6.2 (B2) e §6.3 (validade de construto) — é o lastro externo direto da decomposição "extensional vs. intensivo" que o planejamento já adota em §6.4. Referência mais precisa para justificar por que reportar potência média separada de duração.
- **Verificação:** CrossRef confirma título, seis autores, IEEE ISPASS 2026.
**R6 — IFATH, M. M. A.; HAQUE, I. Characterizing Performance–Energy Trade-offs of Large Language Models in Multi-Request Workflows. In: *Abstracts of the 2026 ACM SIGMETRICS International Conference on Measurement and Modeling of Computer Systems*, 2026.**
- DOI / link oficial: https://doi.org/10.1145/3801489.3806907
- **Conteúdo:** caracterização sistemática de trade-offs performance-energia em workflows multi-requisição (sequencial, interativo, agêntico, composto), em testbed A100 real.
- **Onde usar:** §6.2 (B2) — única referência do conjunto que mede energia especificamente em padrões *agênticos* de múltiplas requisições, isto é, o mesmo padrão do tool calling do MVP. Use para justificar por que a unidade de medida do B2 é a requisição completa (incluindo o loop de ferramentas), não a chamada isolada ao modelo.
- **Verificação:** CrossRef confirma dois autores e o veículo. **Ressalva de peso:** o registro é de um volume de *abstracts* do SIGMETRICS — trata-se de resumo estendido, não artigo completo. Citável, mas não deve sustentar sozinho uma afirmação central.
### 2.3 Trabalho prévio do autor
 
**R7 — BARROS, L. A. M.; DA SILVA, V. M. A.; DOS SANTOS, T. A.; VIANA, G. M. R.; GOMES DE B. FILHO, B. Single Prompt vs. Debate Multiagente: Uma Análise de Telemetria de Hardware em Tarefas de Contexto Longo com Llama 3.2 2B. In: *Anais do LIII Seminário Integrado de Software e Hardware (SEMISH 2026)*, CSBC 2026, Gramado/RS. SBC, 2026.**
- DOI / link oficial: https://doi.org/10.5753/semish.2026.23941 — SBC OpenLib: https://sol.sbc.org.br/index.php/semish/article/view/43591
- **Conteúdo:** compara prompt único vs. debate multiagente em 100 tarefas de domínio financeiro, verificando se a redução de carga de contexto por agente compensa o custo energético da coordenação, via telemetria NVML.
- **Onde usar:** §6.4 — origem declarada de quatro elementos reaproveitados no Benchmark 2: critério de gating de corretude, pacote estatístico (Shapiro-Wilk → Mann-Whitney U → Cliff's delta → Holm-Bonferroni), protocolo NVML (100 ms, baseline de ociosidade, estabilização térmica) e a decomposição extensional vs. intensivo. Também usado em §11 (pitch) e §13 como evidência de domínio metodológico prévio.
- **Verificação (09/09/2026), com atualização relevante:** o CrossRef retorna a lista de autores completa: **Luiz Alexandre M. Barros; Vitor Manoel A. da Silva; Thiago Angelino dos Santos; Guilherme Maia R. Viana; Bruno Gomes de B. Filho.** A nota anterior — "a lista não inclui Alves" — era literalmente verdadeira quanto ao sobrenome, mas o **segundo autor é "Vitor Manoel A. da Silva"**, cuja inicial "A." pode corresponder a "Alves". ⚠️ **Ação necessária:** confirmar se esse é o seu registro de autor no CSBC; se for, o nome de citação a usar no TCC é "DA SILVA, V. M. A.", não "ALVES, V." — e a bibliografia deve ser consistente com o nome como está publicado.
### 2.4 Terminologia e fundamentação arquitetural (Cap. 2)
 
**R8 — SAPKOTA, R.; ROUMELIOTIS, K. I.; KARKEE, M. AI Agents vs. Agentic AI: A Conceptual Taxonomy, Applications and Challenges. *Information Fusion*, v. 126, 103599, 2026.**
- DOI / link oficial: https://doi.org/10.1016/j.inffus.2025.103599
- **Conteúdo:** taxonomia conceitual que separa formalmente "AI Agents" (automação reativa de tarefa específica) de "Agentic AI" (sistemas multiagente com objetivos, planejamento e coordenação autônoma), mapeando aplicações e desafios de cada paradigma. Revisão de literatura; a mais citada do conjunto (~525 citações reportadas).
- **Onde usar:** Cap. 2, imediatamente antes da §2.1 do planejamento (definição operacional de harness) — fundamenta a terminologia "agêntico" / "execução autônoma de ferramentas" usada desde o título, e permite posicionar o harness deste TCC no lado "AI Agents" (execução controlada de ferramentas) e não no lado "Agentic AI" (multiagente), coerente com o que está fora do escopo em §5.
- **Verificação:** CrossRef confirma *Information Fusion* (Elsevier), v. 126, art. 103599; **online em 22/08/2025, edição impressa em fev/2026**. Cite como 2026 (ou 2025 online) — as versões anteriores deste arquivo traziam "2025" sem essa distinção.
**R12 — ISSARNY, V.; CAPORUSCIO, M.; GEORGANTAS, N. A Perspective on the Future of Middleware-based Software Engineering. In: *Future of Software Engineering (FOSE '07)*, IEEE, 2007.**
- DOI / link oficial: https://doi.org/10.1109/fose.2007.2
- **Conteúdo:** define middleware como camada de software que oferece soluções reutilizáveis para heterogeneidade, interoperabilidade, segurança e confiabilidade. ~171 citações. Track de survey convidado do ICSE.
- **Onde usar:** Cap. 2 — âncora teórica consolidada para tratar o harness como middleware, exatamente a manobra que o planejamento precisa para não depender de literatura de "harness" (ainda contaminada por preprint, ver §5 deste documento). Também sustenta o Benchmark 1 conceitualmente.
- **Verificação:** CrossRef confirma título, três autores, FOSE '07, IEEE, 2007.
### 2.5 Arquitetura e orquestração de agentes (Cap. 3)
 
**R9 — CHANG, E. Y.; GENG, L. SagaLLM: Context Management, Validation, and Transaction Guarantees for Multi-Agent LLM Planning. *Proceedings of the VLDB Endowment*, 2025.**
- DOI / link oficial: https://doi.org/10.14778/3750601.3750611
- **Conteúdo:** arquitetura multiagente que integra o padrão transacional Saga com memória persistente, compensação automática e agentes de validação independentes, endereçando perda de contexto, ausência de rollback e coordenação insuficiente. PVLDB (Q1), ~71 citações.
- **Onde usar:** Cap. 2 (responsabilidades de estado e recuperação atribuíveis a um harness) e Cap. 3; complemento conceitual ao Benchmark 3 — mostra que "recuperação" em sistemas com LLM exige compensação semântica, não apenas retry de transporte, o que ajuda a delimitar honestamente o que o B3 mede (falhas de transporte/protocolo) e o que ele não mede.
- **Verificação:** CrossRef confirma dois autores (Edward Y. Chang, Longling Geng), PVLDB, ACM, 2025.
**R10 — KANDOGAN, E.; BHUTANI, N.; ZHANG, D.; CHEN, R. L.; GURAJADA, S.; HRUSCHKA, E. Orchestrating Agents and Data for Enterprise: A Blueprint Architecture for Compound AI. In: *2025 IEEE 41st International Conference on Data Engineering Workshops (ICDEW)*, 2025.**
- DOI / link oficial: https://doi.org/10.1109/icdew67478.2025.00007
- **Conteúdo:** arquitetura de referência ("blueprint") para IA composta, com registro de agentes e registro de dados para abstrair provedores/APIs proprietárias e orquestrar fluxo via "streams"; validada em caso de uso de RH.
- **Onde usar:** Cap. 3 e na **tabela comparativa** prevista para o Cap. 3 — é a proposta publicada mais próxima da sua, e serve para o argumento de lacuna: propõe a abstração, mas **não mede experimentalmente** os trade-offs dela.
- **Verificação:** CrossRef confirma seis autores e o veículo IEEE ICDEW 2025.
**R11 — ZHU, Y.; LIU, L.; YU, J.; ZHANG, D. LLM-Based Multi-Agent Orchestration: A Survey of Frameworks, Communication Protocols, and Emerging Patterns. *Future Internet*, v. 18, n. 6, art. 326, 2026.**
- DOI / link oficial: https://doi.org/10.3390/fi18060326 — MDPI: https://www.mdpi.com/1999-5903/18/6/326
- **Conteúdo:** survey de sistemas multiagente baseados em LLM (2023–início de 2026), com taxonomia por topologia de coordenação e adaptatividade em runtime; compara seis frameworks (LangGraph, CrewAI, AutoGen/Microsoft Agent Framework, OpenAI Agents SDK, MetaGPT, DSPy) e os protocolos MCP (agente-ferramenta) e A2A (agente-agente); discute gerenciamento de estado, tratamento de erro e segurança. Notavelmente, marca com † os achados reportados por fornecedores para distingui-los de evidência revisada por pares.
- **Onde usar:** Cap. 3 — base pronta para a tabela comparativa de frameworks (atributos sugeridos no planejamento: nível de abstração, múltiplos provedores, recuperação de falha, observabilidade nativa, acoplamento). O próprio critério †/peer-reviewed do survey é um argumento citável em Cap. 3 e §6.3 sobre a qualidade desigual da evidência nesse ecossistema.
- **Verificação:** MDPI confirma quatro autores (Yiwen Zhu, Lihe Liu, Jiaqian Yu, Di Zhang), v. 18, n. 6, art. 326, publicado em 15/06/2026.
**R21 — LIU, Y.; LO, S. K.; LU, Q.; ZHU, L.; ZHAO, D.; XU, X.; HARRER, S.; WHITTLE, J. Agent design pattern catalogue: A collection of architectural patterns for foundation model based agents. *Journal of Systems and Software*, v. 220, art. 112278, fev. 2025.**
- DOI / link oficial: https://doi.org/10.1016/j.jss.2024.112278 — ScienceDirect: https://www.sciencedirect.com/science/article/pii/S0164121224003224 (preprint: arXiv:2405.10467)
- **Conteúdo:** catálogo de padrões arquiteturais para agentes baseados em foundation models, derivado de revisão sistemática de literatura combinada com literatura cinzenta. Cada padrão é apresentado no formato clássico de *pattern* (contexto, problema, solução, forças e trade-offs, usos conhecidos), organizado por categoria de responsabilidade — criação e refinamento de objetivo, otimização de prompt/resposta, cooperação entre agentes, e mecanismos transversais como guardrails e registro de execução. Autores do grupo de arquitetura de software para IA responsável do CSIRO Data61 (Lu, Zhu). *Journal of Systems and Software* (Elsevier, Q1); o trabalho também foi apresentado no **Journal-First track do ICSA 2025**, o que confirma o reconhecimento pela comunidade de arquitetura de software.
- **Onde usar — este é o ganho principal:**
  - **Cap. 2 §2.1 (definição operacional de harness):** é hoje a melhor referência revisada por pares para nomear as responsabilidades da camada agêntica. Permite escrever "as responsabilidades atribuídas ao harness neste trabalho — orquestração de tool calling, gerenciamento de contexto, tratamento de falhas, registro para auditoria — correspondem aos padrões X, Y e Z do catálogo de Liu et al. (2025)", em vez de defini-las por conta própria. Reduz a acusação previsível de que a definição de harness do TCC é *ad hoc*.
  - **Cap. 3 e §2.2 do planejamento — substituição de preprints:** o planejamento cita nominalmente cinco arXiv puros (2606.20683, 2603.25723, 2605.18747, 2605.23950, 2607.08028) para sustentar o estado da arte de harness. R21 cobre boa parte desse mesmo terreno com publicação Q1, e deve assumir o papel central, com os preprints rebaixados a citações rotuladas.
  - **Cap. 3 — tabela comparativa:** entra ao lado de R10 (Blueprint) e R11 (survey de frameworks) como proposta arquitetural sem avaliação experimental controlada.
  - **§6.1 e §9 — legitimação metodológica:** o próprio catálogo foi construído incorporando literatura cinzenta de forma declarada. É precedente Q1 citável para a decisão do TCC (§2.2, §9) de declarar abertamente o histórico de *gray literature* do termo "harness" em vez de mascará-lo.
  - **§6.2 B4 (auditabilidade) — verificar:** o catálogo inclui padrões transversais de guardrail e registro de execução. Vale abrir o artigo e checar se algum deles serve para ancorar externamente o checklist do B4. Se servir, resolve a circularidade apontada pelo Model Council **sem** depender de R20 (Phiri), cujo venue é frágil.
- **Ressalvas críticas:**
  1. É catálogo derivado de literatura, **não** avaliação empírica. Não pode ser citado como evidência de que os padrões funcionam ou de que seus trade-offs foram medidos.
  2. **Cuidado ao formular a lacuna do TCC.** O catálogo já discute trade-offs de cada padrão — qualitativamente, a partir da literatura. Afirmar "a literatura não discute trade-offs da camada" é falso e a banca derruba abrindo o artigo. A formulação defensável é: *o catálogo documenta trade-offs qualitativamente a partir de literatura; este trabalho os mede quantitativamente em estudo controlado com e sem a camada*.
  3. A revisão foi conduzida até 2024. MCP e A2A amadureceram depois — R11 (Zhu et al., 2026) é o complemento temporal, não substituto: R21 cataloga padrões, R11 compara frameworks concretos.
- **Verificação (10/09/2026):** CrossRef confirma oito autores na ordem acima, *Journal of Systems and Software* v. 220, art. 112278, fascículo fev/2025 (Elsevier). Publicação Journal-First confirmada na programação do ICSA 2025.
### 2.6 Vendor lock-in e substitutabilidade (Benchmark 1)
 
**R13 — KAUR, K.; SHARMA, S.; KAHLON, K. S. Interoperability and Portability Approaches in Inter-Connected Clouds: A Review. *ACM Computing Surveys*, v. 50, n. 4, 2017.**
- DOI / link oficial: https://doi.org/10.1145/3092698
- **Conteúdo:** revisão sistemática de mais de 120 artigos sobre interoperabilidade e portabilidade para evitar vendor lock-in em nuvens interconectadas. ACM CSUR (Q1).
- **Onde usar:** Cap. 3 — demonstra que "mitigar lock-in por camada intermediária" é problema de arquitetura consolidado fora de IA, o que legitima o Benchmark 1 sem depender da literatura recente de harness.
- **Verificação:** CrossRef confirma ACM CSUR v. 50, n. 4, 2017; **o título oficial inclui o subtítulo ": A Review"** (ausente nas versões anteriores deste arquivo).
**R14 — MO, D.; CORDINGLY, R.; CHINN, D.; LLOYD, W. Addressing Serverless Computing Vendor Lock-In through Cloud Service Abstraction. In: *2023 IEEE International Conference on Cloud Computing Technology and Science (CloudCom)*, 2023.**
- DOI / link oficial: https://doi.org/10.1109/cloudcom59040.2023.00040
- **Conteúdo:** compara empiricamente funções serverless escritas com biblioteca de abstração vs. APIs nativas do provedor, medindo portabilidade e métricas de estrutura/qualidade de código.
- **Onde usar:** §6.2 (B1) — precedente empírico mais próximo do desenho do Benchmark 1, incluindo o uso de métricas estruturais de código como variável dependente primária. Cite-o ao justificar por que "arquivos/linhas/referências diretas ao SDK" são proxies aceitos na literatura, e discuta em §6.3 a limitação de construto que ele também tem.
- **Verificação:** CrossRef confirma quatro autores e o veículo IEEE CloudCom 2023.
### 2.7 Recuperação de falhas (Benchmark 3)
 
**R15 — MENDONÇA, N. C.; ADERALDO, C. M.; CÁMARA, J.; GARLAN, D. Model-Based Analysis of Microservice Resiliency Patterns. In: *2020 IEEE International Conference on Software Architecture (ICSA)*, 2020.**
- DOI / link oficial: https://doi.org/10.1109/icsa47634.2020.00019
- **Conteúdo:** modela Retry e Circuit Breaker como cadeias de Markov de tempo contínuo (CTMC) e usa o model checker probabilístico PRISM para quantificar o impacto de cada padrão sobre atributos de qualidade e determinar como ajustar seus parâmetros sob diferentes condições de disponibilidade. ~35 citações.
- **Onde usar:** Cap. 2/3 e §6.2 (B3) — fundamenta formalmente por que Retry e Circuit Breaker são os padrões escolhidos como objeto do Benchmark 3, e não uma escolha ad hoc.
- **Verificação:** CrossRef confirma quatro autores e o veículo IEEE ICSA 2020.
**R16 — SEDGHPOUR, M. R. S.; KLEIN, C.; TORDSSON, J. An Empirical Study of Service Mesh Traffic Management Policies for Microservices. In: *Proceedings of the 2022 ACM/SPEC International Conference on Performance Engineering (ICPE '22)*, 2022.**
- DOI / link oficial: https://doi.org/10.1145/3489525.3511686
- **Conteúdo:** estudo empírico em testbed Kubernetes com service mesh Istio, medindo o efeito de diferentes configurações de Circuit Breaker e Retry sobre desempenho e robustez. ~44 citações.
- **Onde usar:** §6.2 (B3) — precedente empírico mais próximo do desenho do benchmark e fonte para justificar os **parâmetros concretos** de retry/backoff/circuit breaker do MVP (hoje sem ancoragem no planejamento).
- **Verificação:** CrossRef confirma três autores e o veículo ACM/SPEC ICPE 2022.
**R17 — ADERALDO, C. M.; COSTA, T. M.; VASCONCELOS, D. M.; MENDONÇA, N. C.; CÁMARA, J.; GARLAN, D. A declarative approach and benchmark tool for controlled evaluation of microservice resiliency patterns. *Software: Practice and Experience*, Wiley, 2024.**
- DOI / link oficial: https://doi.org/10.1002/spe.3368
- **Conteúdo:** ferramenta de benchmark que permite especificar declarativamente e gerar automaticamente cenários de teste com diferentes padrões de resiliência; avalia experimentalmente o impacto de desempenho de Retry e Circuit Breaker em C# e Java. SJR Q2.
- **Onde usar:** §6.2 (B3) — precedente metodológico mais direto: é literalmente "ferramenta de injeção controlada + medição de padrões de resiliência", o desenho do seu B3. Use também para justificar o n ≈ 20–30 por tipo de falha ou para argumentar por um n maior.
- **Verificação:** CrossRef confirma seis autores e o veículo Wiley SPE 2024.
> **Nota de triangulação (mantida da análise anterior, e confirmada nos metadados):** R15, R16 e R17 vêm de dois grupos parcialmente distintos — Mendonça/Aderaldo (UNIFOR/PUC-Rio) com Cámara e Garlan (CMU), e Sedghpour/Klein/Tordsson (Umeå). Há sobreposição de coautoria (Garlan) entre R15 e R17, o que reduz a independência entre essas duas; R16 é o contraponto independente.
 
### 2.8 Auditabilidade e observabilidade (Benchmark 4)
 
**R18 — MACE, J.; ROELKE, R.; FONSECA, R. Pivot Tracing: Dynamic Causal Monitoring for Distributed Systems. *ACM Transactions on Computer Systems*, v. 35, n. 4, 2018.**
- DOI / link oficial: https://doi.org/10.1145/3208104 — página ACM: https://dl.acm.org/doi/10.1145/3208104
- **Conteúdo:** framework de monitoramento que combina instrumentação dinâmica com um operador relacional novo — o *happened-before join* — para correlacionar eventos entre componentes e máquinas em tempo de execução; identifica causas-raiz de bugs, má configuração e falhas de hardware em cluster Hadoop heterogêneo. ~159 citações.
- **Onde usar:** Cap. 2/3 e §6.2 (B4) — referência canônica do mecanismo (correlação causal cross-tier) que OpenTelemetry operacionaliza hoje; é o que dá base técnica à métrica "taxa de reconstrução causal" do B4 e ao campo "correlação entre eventos" da lista de elementos esperados no log.
- **Verificação:** CrossRef registra ACM TOCS v. 35 (registro online datado de 2017); a página oficial da ACM lista o artigo em **TOCS v. 35, n. 4**. Título completo inclui o subtítulo "Dynamic Causal Monitoring for Distributed Systems" (as versões anteriores traziam só "Pivot Tracing"). Confira a data exata no registro ACM antes de fechar a bibliografia — 2017 (online) vs. 2018 (fascículo).
**R19 — HASSAN, W. U.; NOUREDDINE, M. A.; DATTA, P.; BATES, A. OmegaLog: High-Fidelity Attack Investigation via Transparent Multi-layer Log Analysis. In: *Proceedings 2020 Network and Distributed System Security Symposium (NDSS)*, Internet Society, 2020.**
- DOI / link oficial: https://doi.org/10.14722/ndss.2020.24270 — página NDSS: https://www.ndss-symposium.org/ndss-paper/omegalog-high-fidelity-attack-investigation-via-transparent-multi-layer-log-analysis/
- **Conteúdo:** introduz "proveniência universal": une logs de sistema (syscalls) a logs de aplicação para reconstruir a cadeia causal completa de um incidente, eliminando a lacuna semântica entre camadas; overhead médio de ~4%. ~160 citações. NDSS é um dos quatro venues top-tier de segurança.
- **Onde usar:** Cap. 2/3 e §6.2 (B4) — é a referência mais próxima do enunciado exato do B4 ("reconstrução causal de erros"). Dois usos concretos: (a) justificar por que reconstrução causal exige correlacionar camadas, e não uma única trace de requisição; (b) o overhead de ~4% relatado é um ponto de comparação externo para o custo de observabilidade do seu harness, ligando B4 a B2.
- **Verificação:** CrossRef confirma quatro autores (Wajih Ul Hassan, Mohammad A. Noureddine, Pubali Datta, Adam Bates), NDSS 2020, Internet Society. Confirmado também na página oficial do NDSS Symposium.
**R20 — PHIRI, C. C. Creating Characteristically Auditable Agentic AI Systems. In: *Proceedings of the Intelligent Robotics FAIR 2025*, ACM, 2025.**
- DOI / link oficial: https://doi.org/10.1145/3759355.3759356
- **Conteúdo:** formaliza "auditabilidade" para sistemas multiagente de IA em 8 axiomas (Integridade, Cobertura, Coerência Temporal, Verificabilidade, Acessibilidade, Proporcionalidade de Recurso, Compatibilidade com Privacidade, Alinhamento de Governança), com extensões de liveness e resiliência adversarial.
- **Onde usar:** Cap. 2 — única referência do conjunto com definição operacional de auditabilidade para IA agêntica; papel análogo ao de R8 para "agêntico". Serve para ancorar externamente o checklist do B4 (recomendação do Model Council de evitar circularidade: hoje o checklist é definido pelo próprio autor e verificado pelo próprio autor).
- **Verificação:** CrossRef confirma autor único (Charles Chimwemwe Phiri), ACM, 2025. ⚠️ **Ressalva de venue:** o registro ACM é real, mas não há histórico consolidado do evento "Intelligent Robotics FAIR" como conferência estabelecida. Trate como publicação legítima de prestígio não verificável — aceitável para ancorar uma definição conceitual, **não** para sustentar sozinha uma alegação empírica. Alternativa de ancoragem externa sem esse risco: a especificação aberta do OpenTelemetry (documento técnico, não peer-reviewed) usada em conjunto com R18/R19.
---
 
## 3. Mapa de uso por seção do TCC
 
| Seção do planejamento / capítulo | Referências a citar |
|---|---|
| Cap. 1 — Introdução (motivação, lacuna) | R21, R8, R10, R11 |
| Cap. 2 §2.1 — Definição operacional de harness | R21 (padrões/responsabilidades), R12 (middleware), R8 (agêntico), R9 (estado/transação) |
| Cap. 2 — Green AI (potência vs. energia; extensional vs. intensivo) | R2, R3, R5 |
| Cap. 2 — Auditabilidade e reconstrução causal | R20 (definição), R18, R19 (mecanismo) |
| Cap. 2 — Resiliência (Retry, Circuit Breaker) | R15 |
| Cap. 3 — Tabela comparativa de frameworks | R11 (base), R21, R10, R9 |
| Cap. 3 / §2.2 — Estado da arte de harness (substituindo preprints) | R21 (central), R11, R10 |
| Cap. 3 — Lock-in / abstração fora de IA | R13, R12, R14 |
| Cap. 3 — Medição energética de LLM | R2, R3, R4, R5, R6 |
| Cap. 4 / §6.1 — Desenho geral e congelamento de versões | R1 |
| §6.2 B1 — Substituibilidade | R14 (precedente empírico), R13, R12 |
| §6.2 B2 — Eficiência energética | R2, R3, R5, R6, R4 |
| §6.2 B3 — Recuperação de falhas | R16 (parâmetros), R17 (ferramenta/protocolo), R15 (fundamento), R9 (limite semântico) |
| §6.2 B4 — Auditabilidade | R19, R18, R20, R21 (verificar padrões de guardrail/registro) |
| §6.3 — Ameaças à validade | R1 (taxonomia), R5 (construto: potência vs. duração), R14 (construto: proxies estruturais), R11 (qualidade desigual da evidência) |
| §6.4 — Base metodológica reaproveitada | R7, R3, R5 |
| §6.1 / §9 — Uso declarado de gray literature | R21 (precedente metodológico Q1) |
| §9 / §13 — Riscos e relevância | R11, R8, R21 |
 
---
 
## 4. Backups validados, não escolhidos
 
Publicações verificadas e legítimas, mantidas como reserva caso alguma escolha caia ou uma seção precise de reforço.
 
| Referência | Veículo | Link oficial | Por que ficou de fora |
|---|---|---|---|
| Stojkovic et al. (2025) — DynamoLLM: Designing LLM Inference Clusters for Performance and Energy Efficiency | IEEE HPCA 2025 | DOI não confirmado nesta verificação — preprint arXiv:2408.00741 | A mais citada da busca energética (~187); foco em escalonamento de cluster, não em overhead de camada |
| Argerich & Patiño-Martínez | IEEE Access (Q1) | DOI não registrado no arquivo original | Q1, ~99 citações; escopo mais amplo que o do B2 |
| Oviedo et al. | *Joule* (Cell Press, Q1) | DOI não registrado no arquivo original | Mostra que estimativas de energia de IA amplamente citadas são superestimadas 4–20× — útil como contraponto crítico no Cap. 2 |
| Gül (2026) | J. King Saud Univ. CIS (Q1, PRISMA) | https://doi.org/10.1007/s44443-026-00900-6 | Tema é hardware (GPU/TPU/NPU), não middleware |
| Cavagna et al. (2026) — SweetSpot | ACM/SPEC ICPE | https://doi.org/10.1145/3777884.3797011 | Válida, redundante com R5/R6 |
| Husom et al. (2025) | ACM ToIoT (Q2) | https://doi.org/10.1145/3767742 | Foco em edge (Raspberry Pi) |
| Fu et al. (2024) — ServerlessLLM | USENIX OSDI 2024 | URL exata não confirmada nesta verificação (buscar em usenix.org/conference/osdi24) | Venue de elite, mas trata de latência de checkpoint, não energia |
| Opara-Martins, Sahandi & Tian (2016) | J. Cloud Computing (Q1), ~242 cit. | https://doi.org/10.1186/s13677-016-0054-z | Perspectiva de negócio, não arquitetura técnica |
| Belchior et al. (2021) — Hermes | Future Gener. Comput. Syst. (Q1) | https://doi.org/10.1016/j.future.2021.11.004 | Tangencial (blockchain). **DOI corrigido** — o CSV trazia DOI de preprint |
| Sedghpour et al. (2023) | IEEE IC2E | https://doi.org/10.1109/ic2e59103.2023.00012 | Redundante com R16 |
| Mohammad (2025) | IEEE ICICyTA | https://doi.org/10.1109/icicyta68677.2025.11362635 | Revisão sistemática PRISMA; reserva para Cap. 3 |
| Aderaldo & Mendonça (2023) | SBES/ACM | https://doi.org/10.1145/3613372.3613409 | Redundante com R17 |
| Palliwar & Pinisetty (2022) | IEEE ICSA | https://doi.org/10.1109/icsa53651.2022.00010 | Reserva |
| Costa et al. (2022) | SBRC/SBC (português) | https://doi.org/10.5753/sbrc.2022.222363 | Reserva; útil se quiser referência nacional |
| Wu et al. (2026) — AutoScope | ACM TOSEM (Q1) | https://doi.org/10.1145/3830907 | Venue forte, mas o tema é eficiência de amostragem de traces, não auditabilidade. Confirmado como versão final do preprint arXiv:2509.13852 |
| Nedelkoski et al. (2020) | Springer (workshops ICSOC) | https://doi.org/10.1007/978-3-030-44769-4_13 | Dataset multi-fonte para AIOps (~69 cit.); reserva para B4 |
| Wang & Tseng (2024) | IEEE Int. Computer Symposium | https://doi.org/10.1109/ics64339.2024.00022 | Implementação direta de OpenTelemetry; reserva |
| Hlybovets & Paprotskyi (2024) | Cybernetics and Systems Analysis (Springer, Q3) | DOI não registrado no arquivo original | Escopo estreito |
| Sivakumar et al. (2024) | IEEE OCIT | DOI não registrado no arquivo original | Conferência regional pequena |
| Mina Carabalí & Mondragon (2025) | IEEE COLCOM | DOI não registrado no arquivo original | 0 citações, validação apenas demonstrativa |
 
**AGENT 2026** (workshop co-localizado com o ICSE 2026): o volume é validado — ACM, DOI de proceedings https://doi.org/10.1145/3786167, indexado no dblp. **Pendente:** escolher um artigo específico dentro do volume, já que o planejamento (§2.2 e §12) promete citar esses proceedings nominalmente.
 
---
 
## 5. Verificadas e rejeitadas
 
Não citar como fonte validada. Preprints podem ser citados **como preprints**, explicitamente rotulados — o planejamento (§2.2, §9) já prevê declarar o histórico de *gray literature* do termo "harness", e citar estes preprints nessa condição é coerente, desde que nenhuma afirmação central se apoie neles.
 
### 5.1 Preprints arXiv puros (sem publicação formal confirmada)
 
Tema harness/agentes: Guo et al. (2606.20683, survey de harness design); Pan/Zou/Guo/Ni et al. (2603.25723); "Stop Comparing LLM Agents Without Disclosing the Harness" (2605.23950); Ning et al. (2605.18747); "From Prompts to Contracts: Harness Engineering for Auditable Enterprise LLM Agents" (2607.08028); Wei & Hu (2604.18071); Lin et al. — SafeHarness (2604.13630); Kim et al. (2606.25447); Qi et al. (2606.15874); Roman & Roman (2601.02577); Xia et al. (2606.20631); Huang & Zhou (2605.13850); Kandasamy (2505.06817); Sarker et al. — AAFLOW (2605.02162); Milosevic & Rabhi (2601.03624); Dennis et al. (2605.22502).
 
Tema energia: Jegham & Abdelatti et al. — "How Hungry is AI?" (2505.09598, dblp lista como `journals/corr`); Caravaca, Cuevas & Rumín (2511.05597); Niu et al. — TokenPowerBench (2512.03024); Stojkovic et al. — "Towards Greener LLMs" (2403.20306, precursor do DynamoLLM já publicado); Ozcan et al. (2507.11417); Xu et al. — Camel (2508.09173); Zhen et al. (2504.19720); Kakolyris et al. (2408.05235, duplicata arXiv do throttLL'eM publicado no IEEE HPCA 2025).
 
Tema auditabilidade: AlSayyad, Huang & Pal — AgentTrace (2602.10133); Zhao Wang — AgentTrace, trabalho distinto de título quase idêntico (2603.14688); Mishra & Sharad (2606.09692); Yiqi Wang et al. — survey de proveniência em agentes (2606.04990; reavaliar se for publicada formalmente).
 
⚠️ **Atenção ao planejamento:** o §2.2, o Cap. 3 e o §12 citam nominalmente arXiv:2606.20683, 2603.25723, 2605.18747, 2605.23950 e 2607.08028. Todos são preprints puros. Se permanecerem, precisam estar rotulados como preprint no texto e não podem sustentar a alegação de ineditismo — que é justamente o que o Model Council apontou como pendência aberta (v3 → changelog).
 
### 5.2 Metadado corrompido
 
- Shaw et al. — "English Version", DOI 10.1007/bf02273518: o DOI resolve para a revista *Synthese* (filosofia), sem relação com o resumo. **Não usar.**
### 5.3 Veículos sem indexação Scopus/Scimago, predatórios ou com sinais de citação inflada
 
IJIRMPS (Nutakki, 2026); IntechOpen (Opara-Martins, 2018 — reputação mista, sem SJR); Kohler Jens (2025, DOI 10.1145/3759023.3759096 — 0 citações, venue pouco conhecida); IJISRT (Bansal, 2024 — 703 citações reportadas para artigo de 1 página classificado como "other": assinatura de citação inflada); IJRAI (Ganesan, 2026, prefixo DOI 10.15662); Indian Journal of Science and Technology e The Scientific Temper (Punithavathy & Priya, 2024); "Artificial Intelligence and Machine Learning Review" (Hu & Hao, 2026, prefixo 10.69987); Innovative Journal of Applied Science (Bansal, Sharma & Dasani, 2025, prefixo 10.70844); IJEETR (Ghanta, 2023, mesmo prefixo 10.15662); IJSDR (Deshmukh et al., 2025); IJSRSET (Vankayala, 2023); "Scientific Journal of AI and Blockchain Technologies" (Jaiswal, 2024); IJETCSIT (Devineni, 2024 — alegações muito específicas sobre SOC 2 e seis bancos, sem afiliação institucional verificável); WJARR (Guntupalli, 2025).
 
Backups de tier menor, válidos porém não usados: Jaidi (2026, IJCESEN Q3); Bogdanović et al. (2026, Sinteza, conferência regional); Pashko et al. (2026, Bulletin of Taras Shevchenko Nat. Univ. Kyiv); Fedoryshyn (2025, Bulletin of Cherkasy State Tech. Univ.); Gairola (2025, IJCESEN Q3); Paramjeet (2026, JISEM Q3); Nellutla (2026, IEEE ICSFT).
 
**Padrão recorrente digno de citação no próprio TCC:** os veículos rejeitados concentram alegações de melhoria muito específicas e não auditáveis ("redução de 84,2% no MTTR", "83% de redução no MTTRC"). Esse é literalmente o tipo de afirmação que o Benchmark 4 deveria conseguir auditar, e é um argumento pronto para a motivação do Cap. 1 e para §6.3.
 
---
 
## 6. Cobertura, pendências e histórico das buscas
 
### Cobertura por dimensão
 
| Dimensão | Referências | Situação |
|---|---|---|
| Fundamentação (arquitetura, middleware, terminologia) | R12, R8, R21, R1 | Boa — reforçada por R21 |
| Estado da arte de harness / padrões agênticos | R21, R11, R10, R9 | Boa — deixou de depender de preprint |
| B1 — Substitutabilidade | R14, R13, R12 | Boa (3) |
| B2 — Eficiência energética | R2, R3, R4, R5, R6 | Muito boa (5) |
| B3 — Recuperação de falhas | R15, R16, R17 (+ R9 complementar) | Boa (3+1) |
| B4 — Auditabilidade | R18, R19, R20 | Fechada (3), com R20 de venue frágil |
| Metodologia experimental | R1 | Suficiente |
 
### Pendências abertas
 
1. **Autoria do artigo SEMISH (R7).** A lista oficial é Barros; **da Silva, V. M. A.**; dos Santos; Viana; Gomes de B. Filho. Confirme se "Vitor Manoel A. da Silva" é o seu registro de autor e ajuste a forma de citação no TCC de acordo. Isso afeta §6.4, §11 e §13 do planejamento.
2. **AGENT 2026:** escolher um artigo específico do volume (https://doi.org/10.1145/3786167), já que o planejamento promete citar os proceedings nominalmente.
3. **R20 (Phiri):** venue de prestígio não verificável. Se o Cap. 2 for apoiar-se fortemente na definição de auditabilidade, considere reforçar com a especificação do OpenTelemetry (rotulada como documento técnico) ao lado de R18/R19.
4. **Preprints citados nominalmente no planejamento** (§2.2, Cap. 3, §12): rotular como preprint ou substituir. **Com R21 na base, a substituição passou a ser viável** — ver §5.1 e a entrada de R21.
7. **Reformular a alegação de lacuna** à luz de R21: o catálogo já discute trade-offs qualitativamente. A lacuna do TCC é a **medição quantitativa controlada**, não a ausência de discussão. Isso afeta o Cap. 1, o Cap. 3 e o §10 do planejamento, e era exatamente a pendência que o Model Council havia levantado ("possível reposicionamento da alegação de ineditismo").
8. **Abrir R21 e mapear os padrões** contra as responsabilidades listadas em §2.1 do planejamento e contra os elementos esperados no log do B4. Tarefa concreta pendente — o mapeamento não foi feito, apenas identificado como possível.
5. **Data de R18 (Pivot Tracing):** 2017 (online, CrossRef) vs. v. 35 n. 4 (fascículo ACM). Fixar uma forma e manter consistente.
6. **Opcional — busca 6, não executada.** Reforçaria a Fundamentação com base acadêmica formal para ADRs, C4 e ISO/IEC 25010, hoje ancorados apenas na prática (§6.1 e Cap. 2 dependem deles). Prompt sugerido: *"What is the role of architecture decision records (ADRs), the C4 model, and ISO/IEC 25010 quality attributes in documenting and evaluating software architecture?"*
### Histórico das buscas (Consensus, 20 resultados cada)
 
| # | Tema | Escolhidas | Taxa de validação |
|---|---|---|---|
| 1 | Arquitetura/harness | 3 (R9, R10, R11) | ~35% |
| 2 | Vendor lock-in / substituibilidade | 3 (R12, R13, R14) | ~45% |
| 3 | Overhead energético em inferência | 3 (R5, R6, R3) | ~50–55% |
| 4 | Retry / backoff / circuit breaker | 3 (R15, R16, R17) | 70% (melhor) |
| 5 | Auditabilidade / observabilidade | 3 (R18, R19, R20) | 50% |
 
**Padrão consistente nas cinco iterações:** terminologia madura de engenharia de software (middleware, vendor lock-in, medição de potência em GPU, retry/circuit breaker, distributed tracing) rende 45–70% de literatura revisada por pares; a terminologia "harness/scaffolding" rende ~35%, por ser recente e dominada por preprint. Isso é um achado citável no próprio TCC: reforça a decisão metodológica (§2.2 do planejamento) de fundamentar o trabalho em conceitos consolidados de arquitetura e tratar "harness" como objeto de estudo aplicado, não como teoria pronta.
 
### Correções de metadado aplicadas nesta consolidação
 
- **R8 (Sapkota):** ano corrigido — online em 2025, fascículo *Information Fusion* v. 126, fev/2026.
- **R13 (Kaur):** título completo inclui ": A Review".
- **R18 (Pivot Tracing):** título completo inclui ": Dynamic Causal Monitoring for Distributed Systems"; discrepância de ano registrada.
- **R4 (Wilkins):** o DOI corresponde à versão em periódico (ACM SIGEnergy EIR), não aos proceedings do workshop HotCarbon.
- **R6 (Ifath & Haque):** identificado como volume de *abstracts* do SIGMETRICS — resumo estendido, não artigo completo.
- **R7 (SEMISH):** lista de autores completa obtida; pendência de autoria reformulada com dado concreto.
- **R3 (Fernandez):** mantida a correção anterior (ACL 2025, não arXiv puro).
- **Hermes (Belchior et al.):** DOI de preprint substituído pelo DOI da versão em periódico.
- **Todos os links de consensus.app** substituídos por DOI oficial / página da editora.