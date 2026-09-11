# Semana 0 — Search

Projetos sobre **algoritmos de busca**: como um agente encontra uma sequência de ações que leva de um estado inicial a um objetivo, explorando o espaço de estados de forma sistemática.

| Projeto | Conceitos aplicados |
|---------|---------------------|
| [`degrees`](./degrees) | Busca em largura (BFS), fronteira de fila, menor caminho em grafo |
| [`tictactoe`](./tictactoe) | Adversarial search, algoritmo Minimax, jogos de soma zero |

## Conceitos da semana

- **Formulação de problemas de busca**: estado inicial, ações, função de transição, teste de objetivo e custo de caminho.
- **Busca não informada**: DFS (fronteira de pilha) e BFS (fronteira de fila); BFS garante o caminho mais curto quando o custo das arestas é uniforme.
- **Busca adversária**: Minimax para ambientes com dois jogadores competindo, com poda alpha-beta como otimização.

## Requisitos

- Python 3.10+
- `degrees` usa apenas a biblioteca padrão.
- `tictactoe` precisa de `pygame` (`pip install -r tictactoe/requirements.txt`).

Cada subpasta tem seu próprio `README.md` com instruções de execução.
