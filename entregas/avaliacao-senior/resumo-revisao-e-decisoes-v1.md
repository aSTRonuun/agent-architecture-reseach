# Resumo da Avaliação Independente, Decisões e Alterações Aplicadas (TCC I)

- **Data:** 23/11/2026
- **Escopo:** Projeto de TCC I — Engenharia de Software (UFC, Campus de Quixadá)
- **Base avaliada:** Fontes LaTeX atuais da entrega parcial (`documento.tex`, `2-textuais/1-introducao.tex`, `2-textuais/trabalhos-relacionados.tex`, `2-textuais/2-fundamentacao-teorica.tex`, `2-textuais/3-metodologia.tex`, `3-pos-textuais/apendices/apendice-busca.tex`, `3-pos-textuais/apendices/apendice-delimitacao.tex`, `3-pos-textuais/referencias.bib`, além de `1-pre-textuais/resumo.tex`, `1-pre-textuais/abstract.tex` e notas comentadas em `2-textuais/5-conclusao.tex`).

---

## 1. Síntese do parecer independente inicial

### Veredito original (antes das correções)
A proposta possuía boa organização narrativa, recorte honesto das dimensões avaliadas e dados de contexto bem conferidos, mas apresentava uma **falha estrutural na metade energética (*Benchmark* 2)**: media exclusivamente a GPU do servidor sob paridade estrita de chamadas e desconto da potência ociosa (fazendo o sinal na GPU tender a zero por construção), enquanto deixava o custo direto da camada na CPU apenas estimado por um limite superior grosseiro — contradizendo o verbo *"mensurar"* do quarto objetivo específico (OE4). Somavam-se a isso lacunas estatísticas, o adiamento de todos os limiares de decisão, um plano B que abandonava a pergunta energética, viés do experimentador e cenário brando no *Benchmark* 1, além de dois erros factuais em citações.

### Quadro de notas da avaliação inicial

| Critério | Nota (0–10) | Confiança | Síntese do diagnóstico original |
| :--- | :---: | :---: | :--- |
| **C1. Inovação** | 6 | Alta | Contribuição empírica incremental plausível para TCC, mas fragilizada por trabalhos-chave lidos apenas pelo resumo (`morais2026`, `matinpour2026`), triagem sem contagens registradas e risco de efeito energético desprezível. |
| **C2. Impacto** | 5 | Alta | Decisão arquitetural real e escopo bem delimitado, mas energia é o contrapeso menos acionável para o público-alvo e há assimetria entre provedores comerciais (B1) e modelo auto-hospedado (B2). |
| **C3. Viabilidade técnica** | 4 | Alta | Falha estrutural no B2 (fronteira GPU/CPU + paridade de chamadas + estatística i.i.d. sem teste formal de não inferioridade), viés/trivialidade no B1, ausência de seção de ameaças no Cap. 4 e plano B que descarta a pergunta. |
| **C4. Coesão** | 7 | Alta | Narrativa macro encadeada e nomenclatura estável entre texto, fluxograma e cronograma, porém com conceitos órfãos no Cap. 3 (ameaças, MCP, *Circuit Breaker*, efeito de duração/potência) e testes no Cap. 4 não introduzidos antes. |
| **C5. Coerência** | 5 | Alta | Contradição entre OE4 ("mensurar") e estimativa por limite superior na CPU, plano B violando o recorte de duas dimensões, cruzamento assimétrico na Atividade 13 e erros verificados em Liu et al. (2025) e Vellaisamy et al. (2026). |

### Achados factuais verificados diretamente contra fontes
- **Confirmados:** Stack Overflow (2025: 76% → 84% e ~31%); Menlo Ventures (2025: ~150 líderes, US\$ 3,5 bi → US\$ 8,4 bi, OpenAI 50% → 25%, Anthropic 32%, Google 20%, 11% troca / 66% atualização); IEA (2025: 415 TWh / 1,5% → 945 TWh); Luccioni et al. (2024: 0,047 vs. 0,002 kWh/1.000 inferências ≈ 170 J/req); Fernandez et al. (2025: até 73%); Xiao et al. (2025: até 5,6%); Tripathy et al. (2026: razão 9,4×); existência dos modelos (Claude Haiku 5.5, GPT-6 Luna, Qwen3.6 27B) e artigos recentes de 2026.
- **Erros encontrados e corrigidos:**
  1. **Liu et al. (2025) (`context/full-papers/1-s2.0-S0164121224003224-main.txt`, Seção 3.3):** O texto afirmava *"14 dos 18 padrões listam overhead e um 15º lista maintenance overhead"*. Na conferência direta sob *Drawbacks* (seções 4.1–4.18), são **11** com `Overhead` e **3** com `Maintenance overhead` (entre eles `4.17 Agent adapter`, o mais próximo da camada), totalizando **14** — não 15 (a contagem anterior somara 3 ocorrências de `Overhead` da seção *Forces*).
  2. **Vellaisamy et al. (2026) (Atividade 12):** Estava citado para justificar a separação entre potência média e duração da GPU, mas *TaxBreak* decompõe **latência** entre *host CPU* (PyTorch/CUDA) e GPU, não potência × duração energética.
  3. **Divergências entre resumo do prompt e documentos:** Não há telemetria `CPU/RAPL` (a CPU cliente é estimada por limite superior), e o modelo aberto executa em servidor institucional remoto pela rede (não localmente na máquina da aplicação).

### Respostas consolidadas aos cinco pontos de julgamento do autor
1. **Critério de "compensa":** Não era refutável no TCC I porque todos os limiares e regras estavam adiados para a Atividade 4.
2. **Fronteira GPU/CPU:** A NVML mede apenas o efeito sobre a inferência na GPU; a cota de CPU serve apenas como argumento de pior caso/desprezibilidade, não como mensuração pontual.
3. **Paridade de chamadas + desconto da potência ociosa:** Faz a diferença na GPU tender a zero por construção, exigindo enquadramento formal de **não inferioridade** em vez de teste bilateral comum de diferença.
4. **Um único recurso específico (*prompt caching*, Anthropic → OpenAI):** Era brando demais por não alterar comportamento funcional e migrar do explícito para o automático.
5. **Experimento vs. argumento de projeto:** Exige controles que produzam evidência não trivial (teste formal de não inferioridade + recurso que altere contrato + contabilização do custo inicial do *harness*).

---

## 2. Decisões tomadas para a revisão

Priorizando **simplicidade e viabilidade técnica** (execução solo até junho/2027 em janelas exclusivas limitadas de GPU) sem sacrificar coesão ou impacto, foram fechadas as seguintes decisões:

1. **Ação 1 — Opção B (`B-não-inferioridade`) no *Benchmark* 2:**
   - Mantém a medição via NVML na GPU do servidor institucional + cota superior de CPU na máquina cliente (sem exigir RAPL/wattímetro).
   - Reformula o OE4 e a hipótese para **avaliar o efeito energético da interposição da camada**, medindo a inferência na GPU (via teste formal de **não inferioridade** contra $\Delta_0 = 5\%$) e limitando por cima a CPU local.
   - Substitui a integração de potência a 100 ms pelo contador acumulado de energia (`nvmlDeviceGetTotalEnergyConsumption`) como métrica primária de energia, reservando `nvmlDeviceGetPowerUsage` e latência como métricas secundárias/diagnósticas (separando **efeito de duração** e **efeito de potência**).
   - Substitui `Shapiro-Wilk → Mann-Whitney U (i.i.d.)` por **análise pareada por bloco de sessão** (teste unilateral dos postos sinalizados de Wilcoxon + intervalo de confiança unilateral de 95% de Hodges-Lehmann / *bootstrap* pareado por bloco), com delta de Cliff, deslocamento relativo mediano e correção de Holm-Bonferroni cobrindo as **4 comparações primárias** (2 métricas primárias × 2 níveis).
   - Ajusta a Atividade 6 para paridade funcional/de tarefa (sem impor artificialmente paridade byte-a-byte de *payload*), torna simétrica a verificação de equivalência na Atividade 12 e exige registro da taxa de descarte por versão nas requisições agênticas.

2. **Ação 2 — Critério de decisão refutável fixado no TCC I + Plano B energético:**
   - Fixa-se o critério de decisão já no projeto (Seção 3.6.3 e Atividade 4): a camada compensa pelo desacoplamento em um par *(nível × cenário)* se e somente se atender simultaneamente a:
     - **Condição 1 (Substituição — B1):** 100% dos casos de uso preservados na suíte de equivalência (incluindo conformidade ao esquema JSON estrito) **e** redução $\ge 50\%$ tanto nos arquivos alterados quanto nos pontos de dependência direta no código de negócio frente à versão D.
     - **Condição 2 (Energia — B2):** aprovação no teste unilateral de não inferioridade na GPU ($\alpha = 0{,}05$) **e** soma do limite superior do IC unilateral de 95% na GPU com a cota superior de CPU $\le 5\%$ da energia média de D ($\mathrm{IC}_{95\%,\mathrm{sup}}(\Delta E_{\mathrm{GPU}}/E_D) + \mathrm{cota\_CPU}/E_D \le 5\%$). A margem de 5% ancora-se nos efeitos arquiteturais de 2%–5,6% da literatura (Xiao et al., 2025; Matinpour et al., 2026) e na tolerância típica dos sensores NVML em H100.
   - Remove-se o plano B de recuperação de falhas (que descartava o OE4 e violava o recorte de duas dimensões) e o protocolo do 3º *benchmark*, substituindo-o na Atividade 10 por uma **contingência energética em duas etapas**: (i) modelo aberto menor com chamada de ferramentas no mesmo servidor (a começar pelo `gpt-oss 20B` ou faixa 7B–14B); (ii) teto mais enxuto de `max_tokens` no protocolo congelado.

3. **Ação 3 — Opção 3A no *Benchmark* 1 + manutenção das Ameaças à Validade na Conclusão:**
   - **Sem nova seção de Ameaças à Validade no Cap. 4** (por escolha do orientador): as ameaças ampliadas ficam registradas nas notas de [2-textuais/5-conclusao.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/2-textuais/5-conclusao.tex) e a Seção 3.6 recebe ponte explícita indicando que as categorias de Wohlin et al. orientam os controles embutidos no Cap. 4 e serão consolidadas na Conclusão.
   - **Recurso específico de provedor (Opção 3A):** *prompt caching* foi substituído por **saídas estruturadas com esquema estrito (*structured outputs*)** (Anthropic `output_config.format` vs. OpenAI `response_format` com `json_schema`, `strict: true`, `additionalProperties: false`, obrigatoriedade de campos e tratamento explícito de `refusal`), mantendo 4 trocas totais mas testando vazamento real de contrato.
   - **Controles adicionados ao B1:** registro do **custo inicial de construção** (arquivos, linhas e componentes de H + *harness* vs. D) nas Atividades 5–6 e Quadro 4.1, analisado ao lado do custo marginal de troca nas Atividades 8 e 13; e **revisão independente do código da versão D** (por orientador ou par técnico) antes do B1 para mitigar viés do experimentador.

4. **Ações 4 e 5 — Correções factuais, bibliográficas e de coesão:**
   - Corrigidas as citações de Liu et al. (2025) e Vellaisamy et al. (2026) e a frase sem fonte na Atividade 1.
   - Posicionados `lin2026` e `jarvenpaa2024` no Cap. 2, qualificado `matinpour2026` como leitura por resumo no texto e no Quadro 2.1, e detalhada no Apêndice A a exclusão dos 9 trabalhos entre os 21 selecionados e os 12 mantidos no quadro.
   - Introduzidos no Cap. 3 todos os instrumentos usados no Cap. 4 (Wilcoxon pareado, Hodges-Lehmann, teste de não inferioridade, delta de Cliff, Holm-Bonferroni e gCO$_2$e); reconectados/delimitados MCP/A2A, *Circuit Breaker*, *SagaLLM* e *efeito de duração/potência*; uniformizado *"modelo local"* → *"modelo auto-hospedado"*; e adicionadas a Seção 1.5 (*Estrutura do trabalho*) e o parágrafo de transição ao final do Cap. 2.

---

## 3. Mapa das alterações aplicadas por arquivo

| Arquivo | Onde | Resumo das alterações aplicadas |
| :--- | :--- | :--- |
| [2-textuais/1-introducao.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/2-textuais/1-introducao.tex) | Seções 1.1–1.5 | Explicitação precoce da fronteira GPU + limite superior de CPU; hipótese reescrita para não inferioridade energética; OE1, OE3, OE4 e OE5 alinhados ao que é efetivamente medido/estimado e ao custo inicial; criação da Seção 1.5 (*Estrutura do trabalho*). |
| [1-pre-textuais/resumo.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/1-pre-textuais/resumo.tex) e [abstract.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/1-pre-textuais/abstract.tex) | Corpo | Sincronização do rascunho provisório com saídas estruturadas, fronteira GPU + limite superior de CPU e critério pré-registrado. |
| [2-textuais/trabalhos-relacionados.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/2-textuais/trabalhos-relacionados.tex) | Seções 2.1–2.2 e Quadro 2.1 | Inclusão de posicionamento breve de `lin2026` e `jarvenpaa2024`; qualificação de `matinpour2026` (*"segundo o resumo"*, `"Não (resumo)"` no quadro); parágrafo de fechamento e transição para o Cap. 3. |
| [2-textuais/2-fundamentacao-teorica.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/2-textuais/2-fundamentacao-teorica.tex) | Seções 3.1, 3.3, 3.4, 3.5 e 3.6 | Delimitação de MCP/A2A, *Circuit Breaker* e *SagaLLM* frente ao produto mínimo; correção da contagem de Liu et al. (2025) (11 + 3 = 14); diferenciação de `nvmlDeviceGetTotalEnergyConsumption` vs. `nvmlDeviceGetPowerUsage` e introdução de gCO$_2$e; ponte explícita das ameaças para a Conclusão; fundamentação de Wilcoxon pareado, Hodges-Lehmann, não inferioridade, delta de Cliff, Holm-Bonferroni e critério de dois limiares. |
| [2-textuais/3-metodologia.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/2-textuais/3-metodologia.tex) | Atividades 1–13, Quadros 4.1 e 4.2 | Substituição de *prompt caching* por **saídas estruturadas**; remoção da simulação/3º *benchmark* de falhas; fixação do critério de decisão (50% + 5%) na Atividade 4; custo inicial (H vs. D) no Quadro 4.1 e Atividades 5, 6, 8 e 13; revisão independente de D (Atividade 6); paridade funcional/de tarefa (Atividade 6); NVML por contador acumulado + latência/potência como secundárias (Quadro 4.2); plano B energético (Atividade 10); pareamento por sessão, verificação simétrica de equivalência/descarte e remoção da citação indevida a `vellaisamy2026` (Atividades 9, 11 e 12); troca de *"modelo local"* por *"modelo auto-hospedado"*. |
| [2-textuais/5-conclusao.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/2-textuais/5-conclusao.tex) | Notas comentadas | Atualização das notas de ameaças à validade (interna, externa, construto e conclusão) com os novos riscos identificados (descarte diferencial, desvio de relógios, tolerância/suavização da NVML, custo inicial, assimetria comercial × auto-hospedado e poder/margem de 5%). |
| [3-pos-textuais/apendices/apendice-busca.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/3-pos-textuais/apendices/apendice-busca.tex) | Triagem | Registro explícito dos motivos de exclusão dos 9 trabalhos (21 → 12 no quadro) e declaração transparente das pendências (contagens pré-21 não registradas e leitura integral pendente de `morais2026` e `matinpour2026`). |
| [3-pos-textuais/apendices/apendice-delimitacao.tex](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/3-pos-textuais/apendices/apendice-delimitacao.tex) | Resp. 3 e 4 | Alinhamento com o produto mínimo da Atividade 3 (histórico de mensagens na Resp. 3; apenas *Retry* na Resp. 4). |
| [3-pos-textuais/referencias.bib](file:///Users/vitoralves/Documents/repositories/agent-architecture-reseach/3-pos-textuais/referencias.bib) | Entradas técnicas | Substituição de `anthropiccache`/`openaicache` por `anthropicstructured` e `openaistructured` (URLs oficiais verificadas em 23/11/2026); zero entradas não citadas no texto. |

---

## 4. Pendências abertas para revisão com o orientador e execução (TCC II)

1. **Validação com o orientador:** confirmar as mudanças substantivas introduzidas no TCC I — em especial (a) a substituição de *prompt caching* por **saídas estruturadas**, (b) a remoção do 3º *benchmark* de recuperação de falhas em favor do **plano B energético**, (c) os **limiares pré-registrados** ($\ge 50\%$ no código de negócio e $\le 5\%$ energético combinado) e (d) a **revisão independente da versão D**.
2. **Leitura integral de dois trabalhos relacionados:** acessar via Portal CAPES o texto completo de **Morais et al. (2026)** e **Matinpour et al. (2026)** para substituir as marcações `"Não (resumo)"` do Quadro 2.1 e confirmar que não há ameaça oculta à lacuna.
3. **Checagem antecipada da infraestrutura de GPU:** confirmar junto ao laboratório/servidor institucional, ainda antes de março/2027, a disponibilidade prevista de janelas exclusivas na H100 e quais modelos menores com *tool calling* (`gpt-oss 20B` ou faixa 7B–14B) já estão hospedados para eventual uso na contingência da Atividade 10.
4. **Revisão visual do PDF compilado:** `documento.pdf` já foi recompilado sem erros via `tectonic` (412 KiB, zero referências/citações indefinidas e zero entradas não citadas no `.bib`); resta apenas a conferência visual das quebras de página, quadros e referências antes da submissão.
