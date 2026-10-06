# Análise crítica — `TCC_minimal_v5.md`

> **Objeto:** `context/planing/TCC_minimal_v5.md` (plano v5-Minimal), com leitura cruzada de `context/planing/Full-Research_v5.md` (versão de origem, 4 benchmarks) e `context/others/5w2h.md`.
> **Data:** 26/09/2026 · **Revisão assistida por IA** (Cline).
> **Caráter:** documento **congelado** — registro datado da revisão. Cada ponto acionável recebeu um ID (A01–A26) e é acompanhado no **`action_log.md`** (raiz do repositório): status, decisão e aplicação vivem lá, não aqui.

## Síntese

Documento acima do padrão típico de TCC — mais próximo de uma proposta de pesquisa que de um plano de trabalho. O recorte de escopo (4 → 2 benchmarks) é bem argumentado e defensável em banca; o gerenciamento de risco é maduro (gate formal no mês 8 com plano B; B1 antecipado por não depender de GPU); a postura epistêmica é correta ("hipótese, não pressuposto"). As fragilidades **não estão na estrutura do argumento**, e sim em detalhes de protocolo — alguns já sinalizados pelo próprio plano (§12), outros identificados nesta análise. Nenhuma pendência bloqueia o pitch ao orientador; três decisões metodológicas (política da versão D [A07], energia de CPU [A11], pacote estatístico [A15–A18]) precisam estar fechadas antes do congelamento do protocolo (mês 3).

## 1. Pontos fortes

**Argumentação e recorte de escopo.** B1 mede o **benefício** alegado da camada; B2, o **preço** que ela cobra — um trade-off fechado que desarma a pergunta "por que só duas dimensões?". A lacuna foi reformulada de forma defensável (a literatura discute trade-offs **qualitativamente**; este trabalho **mede quantitativamente**, em estudo controlado com e sem a camada) — a formulação anterior ("a literatura não discute") seria derrubável em banca. Postura falsificacionista explícita: resultado nulo ou contrário à hipótese é declarado válido e publicável.

**Desenho experimental (B2).** Matriz 2×2 com níveis justificados — nível 1 isola o overhead do invólucro; nível 2 mede o overhead do loop agêntico; a diferença entre níveis é achado por si só. Paridade funcional como pré-condição de validade; gating de corretude funcional ("economia por perda de funcionalidade não é eficiência"); intercalação de condições na mesma janela; baseline de ociosidade e estabilização térmica por sessão; medição real (NVML) ancorada contra estimativas por FLOPs (R3).

**Reaproveitamento metodológico (R7).** Gating, pacote estatístico, protocolo NVML e decomposição extensional/intensivo foram validados em artigo aceito (SEMISH/CSBC 2026) — reduz o risco do B2. A diferença crucial (janelas fragmentadas vs. H100 dedicada) está declarada como ameaça, com variância entre sessões a reportar separadamente.

**Gerência de risco.** B1 no mês 7 garante um resultado completo sem dependência de hardware; gate formal no mês 8 com plano B pré-redigido e referências já validadas (R15–R17, R9); orçamento de GPU **calculado no piloto**, não estimado; congelamento de versões/driver/modelo.

**Honestidade intelectual.** Hierarquia de evidência explícita (14 ativas revisadas por pares + 7 em reserva; preprints rotulados; R6 marcado como resumo estendido que não sustenta afirmação central); nova ameaça de validade externa declarada (modelo local único); limitação do recorte antecipada com a resposta pronta para a banca (§5.2).

## 2. Análise crítica

### 2.1 B1 — a justeza da versão D [A07–A10]

O resultado do B1 é parcialmente verdade **por construção**: o harness existe para facilitar a troca de provedor. O que separa um experimento de uma demonstração é a qualidade da versão D — e o plano não define política para isso. D mal escrita (chamadas de SDK espalhadas) fabrica um *strawman*; D bem escrita (acesso ao SDK centralizado num único módulo, por conta própria) dilui o resultado, porém o torna mais honesto. Mitigações recomendadas: declarar que **D segue a documentação oficial do provedor**, sem dispersão artificial e sem abstração própria [A07]; **pré-registrar** o checklist da troca antes de executá-la, para eliminar racionalização pós-hoc [A08]; decompor a métrica de alteração entre LOC modificados (primária) e LOC do novo adaptador (secundária) — em H a troca gera código novo, em D modifica o existente [A09]; definir fallback para a métrica de tempo, hoje "cronometrado por um colega, se possível" [A10]. Se o mock determinístico virar a segunda condição do B1, registrar na validade de construto que a métrica comportamental perde força [A04].

### 2.2 B2 — o que o NVML não vê e o que pode afogar o sinal [A11–A14, A22]

**Custo de CPU invisível.** NVML mede a GPU; o custo **direto** do harness é trabalho de CPU (normalização, serialização, orquestração do loop). Parte dele aparece indiretamente como duração maior da requisição, mas a energia da CPU do host não é medida — e o sinal de interesse (overhead H−D) vive exatamente na ordem de grandeza do termo não medido. Medir com RAPL/`powercap` como secundária/diagnóstica, ou declarar a limitação com o argumento de dominância do termo de GPU [A11].

**Efeito piso no nível 1.** O overhead do invólucro em single-shot pode ser menor que a banda de ruído do NVML a 100 ms; a comparação sairia não informativa. O piloto deve incluir teste de sensibilidade [A22] e o protocolo deve pré-especificar a alternativa de unidade amostral por **lote de M requisições**, com M calibrado no piloto [A14].

**Comprimento do loop no nível 2.** As ferramentas são determinísticas, mas o **número** de chamadas por requisição depende do modelo; se H e D gerarem loops de comprimentos diferentes, J/req mistura overhead por passo com comprimento do loop. Fixar parâmetros de amostragem (temperature 0, seed, prompts e schemas idênticos), registrar a contagem de tool calls por requisição e tratá-la como gate/diagnóstico [A13]. A "deterministicidade" exigida no §5.1 precisa de definição operacional.

**Escopo da interface.** O MVP prevê dois adaptadores (B1), mas o B2 exige que H converse com o modelo local — um terceiro ponto de integração, salvo se um dos provedores do B1 for o próprio modelo local. Não especificado; afeta o dimensionamento do mês 4 [A12].

### 2.3 Estatística — a pendência §12.1 é mais séria do que parece [A15–A18, A21]

Mann-Whitney U compara superioridade estocástica entre distribuições — **não compara percentis**. A pendência declarada no plano é legítima e está no caminho crítico do mês 3. Caminho sugerido: testes formais sobre as amostras brutas (J/req, J/token, potência média); p50/p95/p99 como descritivos com IC bootstrap; regressão quantílica apenas se um teste formal de cauda for indispensável [A15]. A contagem "2 comparações × 4 métricas = 8 testes" é ambígua (p50/p95/p99 são 1 família ou 3 testes? potência média/pico é 1 ou 2 métricas?) — e a resposta muda a carga do Holm-Bonferroni; pré-especificar a família de testes [A16]. O critério de aceitação contém dois termos vagos: "**ou comparável**" pede formalização como não-inferioridade com margem pré-definida [A17]; "**limiar adotado**" de Cliff's delta ainda não foi adotado — fixá-lo antes da coleta (referência usual: |δ| ≥ 0,33, efeito pequeno) [A18]. Para o cálculo de n do piloto, substituir "tamanho de efeito esperado" (sem fonte) por **efeito mínimo de interesse prático** e calcular n por simulação sobre a variância do piloto [A21].

### 2.4 Gate do mês 8 e o custo documental do plano B [A05, A20, A23]

O critério "horas obtidas ≥ 50% do orçamento" compara um **acumulado** (meses 6–8) com uma necessidade que se estende ao mês 10: obter 50% até o mês 8 não garante os 50% restantes. Gate mais robusto: **taxa de acesso projetada** — horas/semana obtidas vs. necessárias até o fim do mês 10 [A23]. O plano reconhece o custo técnico do pivô para B3 (injetor de falhas, 3–4 semanas) mas não o **custo documental**: título, problema, objetivos e pitch são construídos sobre desacoplamento × energia, e o TCC I (mês 6) já terá sido escrito com essa moldura — o pivô exige reescrita substantiva. Mitigação barata: memo de pivô de uma página (moldura B1+B3) redigido junto ao protocolo do B3, no mês 3 [A20]. Tensão sutil do corte de escopo: os critérios de escolha da aplicação (§5.1) **derrubaram** "permitir simular falhas", presente na v5 completa — mas o plano B depende de injeção de falhas. Reinstalar o critério antes da escolha do mês 1 [A05].

### 2.5 Paridade funcional — definição operacional em falta [A19]

A suíte de paridade é o pino de validade dos dois benchmarks, mas o plano não define o que "verde" significa operacionalmente: mesmas entradas → mesmas saídas? Sequência de tool calls idêntica? Que tolerância para campos normalizados? A definição precisa preceder a especificação da suíte (mês 4) e a implementação da versão D (mês 5).

### 2.6 Consistência e rastreabilidade [A01–A03]

| Verificação | Resultado |
| :--- | :--- |
| Contagem de referências (14 ativas + 7 em reserva = 21) | ✔ confere |
| Coerência cronograma × dependências (B1 sem GPU no mês 7; coleta 8–10; 11–12 livres) | ✔ coerente |
| `5w2h.md` alinhado à versão Minimal (título, 14 refs, gate mês 8) | ✔ alinhado |
| Fidelidade da derivação v5 → v5-Minimal (B3/B4 como ADRs; objetivos 5 → 3) | ✔ fiel |
| Nome do arquivo-fonte citado no cabeçalho vs. arquivo real | ✘ divergência → [A01] (fechado em 26/09/2026) |
| `consolidated_references.md` citado como fonte do §7 | ✘ ausente do repositório → [A02] |
| Orientador nomeado no 5w2h vs. §12.1 "confirmar orientador" | ○ inconsistência leve de estado → [A03] |

As 21 referências não puderam ser verificadas nesta revisão (o arquivo consolidado está fora do repositório); a análise assume as verificações CrossRef de 09–10/09/2026 declaradas no plano.

## 3. Mapa recomendações → registro de ações

| # | Recomendação | IDs |
| :--- | :--- | :--- |
| 1 | Política da versão D + pré-registro do checklist da troca | A07, A08 |
| 2 | Pacote estatístico definitivo (testes, família, margem, limiar) | A15–A18 |
| 3 | Energia de CPU: RAPL ou limitação declarada | A11 |
| 4 | Piloto robusto: sensibilidade, lote, tool calls, n | A13, A14, A21, A22 |
| 5 | Proteção do plano B: critério de falhas + memo de pivô | A05, A20 |
| 6 | Gate por taxa projetada de acesso | A23 |
| 7 | Decomposição da métrica de alteração de código | A09 |
| 8 | Escopo do adaptador do modelo local | A12 |
| 9 | Higiene e rastreabilidade (arquivo-fonte, base bibliográfica, orientador) | A01–A03 |

Itens de menor peso — fallback da métrica de tempo [A10], escolha de provedores/mock [A04], autoria de R7 [A06], base acadêmica para ADR/C4/ISO [A24], AGENT 2026 [A25] e a nota de redação [A26] — estão detalhados no `action_log.md`.

## 4. Conclusão

O plano está **pronto para o pitch**; nenhuma pendência o bloqueia. A evolução necessária não é estrutural: é fechar os detalhes de protocolo — a justeza da versão D (sem a qual o B1 nasce confirmatório por construção), a invisibilidade do custo de CPU no NVML e a resolução da pendência estatística — todos antes do congelamento do mês 3. **Insight de sequenciamento:** a introdução não depende de nenhum desses itens; depende apenas do gate A02–A03 (base bibliográfica no repositório e recorte endossado pelo orientador). Nota de forma: o estilo denso e autorreferente dos documentos de planejamento não deve ser herdado pelos capítulos do TCC [A26].