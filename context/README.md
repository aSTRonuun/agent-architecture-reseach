# TCC — Harness arquitetural para integração de IA em aplicações web

Repositório de planejamento e redação do TCC (Engenharia de Software).

## Estrutura

```
agent-architecture-reseach/
├── context/                 ← planejamento e histórico de decisões (Markdown)
│   ├── action_log.md            ← ponto de entrada: backlog de pendências e decisões
│   └── planning/                 ← o que decide o trabalho
├── documento.tex             ← monografia (template ufctex/abntex2), só a ordem do documento
├── 1-pre-textuais/           ← capa, resumo, abstract, listas
├── 2-textuais/               ← introdução … conclusão
├── 3-pos-textuais/           ← referências, apêndices, anexos
├── figuras/, lib/            ← ativos e macros do template UFC
└── Makefile                  ← compilação (pdflatex + bibtex)
```

**Regra de fluxo:** `context/` → decide; os capítulos em `1/2/3-*` → só redigem e consomem essa decisão.

## Planejamento

| Caminho | O que é | Mutável? |
| :--- | :--- | :--- |
| **`action_log.md`** | **Ponto de entrada.** Backlog vivo de pendências e decisões (A01–A29), com prazo, prioridade e gate da introdução | Sim — atualizar a cada sessão |
| `planning/TCC_minimal_v5.md` | Plano vigente (v5-Minimal: recorte B1+B2) | Congelado; muda via fechamento de itens ou nova versão |
| `planning/Full-Research_v5.md` | Plano completo de origem (4 benchmarks) | Congelado (referência histórica) |
| `planning/TCC_minimal_v5_critical_review.md` | Análise crítica do plano vigente (26/09/2026) | Não — registro datado |
| `planning/consolidated_references.md` | 21 referências verificadas (CrossRef) — fonte de verdade dos metadados do `.bib` | Sim |
| `planning/5w2h.md` | Formulário PPCT (5W2H) | Atualizar quando o plano mudar |

## Compilar a monografia

Ver [README.md](../README.md) e [Makefile](../Makefile) na raiz do repositório (template ufctex, `pdflatex` + `bibtex` + `makeglossaries` + `makeindex`).

Marcadores `\pendencia{...}` aparecem em vermelho no PDF; os comentários `%` no topo de cada capítulo (em `2-textuais/`) apontam a seção do plano e os itens do registro que alimentam o texto.

## Fluxo de trabalho por sessão

1. Abra `action_log.md`; confira o **Foco atual** e o **Painel**.
2. Escolha o item aberto de menor prazo; mude o status para `em análise`.
3. Trabalhe o item; registre a **Decisão** no próprio item (o quê, por quê, onde aplicado).
4. Aplique a decisão no documento-alvo (plano, protocolo, capítulo em `2-textuais/`).
5. Status → `fechado`; atualize o **Foco atual**; commite.
