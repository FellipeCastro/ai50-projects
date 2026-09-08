# Semana 1 — Knowledge

Projetos sobre **representação de conhecimento e inferência lógica**: como um agente representa fatos sobre o mundo em lógica proposicional e deriva novas conclusões a partir do que já sabe.

| Projeto | Conceitos aplicados |
|---------|---------------------|
| [`knights`](./knights) | Lógica proposicional, base de conhecimento, model checking |
| [`minesweeper`](./minesweeper) | Agente baseado em conhecimento, inferência com sentenças lógicas, subconjuntos |

## Conceitos da semana

- **Lógica proposicional**: símbolos e conectivos (`¬`, `∧`, `∨`, `→`, `↔`).
- **Entailment e model checking**: verificar se `KB ⊨ α` enumerando todos os modelos possíveis.
- **Agentes baseados em conhecimento**: manter uma base de sentenças e inferir células seguras / minas a partir dela.

## Requisitos

- Python 3.10+
- `knights` usa apenas a biblioteca padrão (`logic.py` fornecido).
- `minesweeper` precisa de `pygame` (`pip install -r minesweeper/requirements.txt`).

Cada subpasta tem seu próprio `README.md` com instruções de execução.
