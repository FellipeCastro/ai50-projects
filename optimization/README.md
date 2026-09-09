# Semana 3 — Optimization

Projetos sobre **otimização**: escolher a melhor opção dentro de um espaço de possibilidades, seja minimizando um custo, maximizando um valor ou satisfazendo um conjunto de restrições.

| Projeto | Conceitos aplicados |
|---------|---------------------|
| [`crossword`](./crossword) | Problema de satisfação de restrições (CSP), consistência de nó e de arco (AC-3), busca com retrocesso, heurísticas MRV, grau e LCV |

## Conceitos da semana

- **Busca local**: hill climbing, hill climbing estocástico e com reinícios aleatórios, simulated annealing.
- **Programação linear**: função objetivo e restrições lineares; minimização sujeita a limites.
- **Problemas de satisfação de restrições (CSP)**: variáveis, domínios e restrições unárias/binárias.
- **Consistência**: consistência de nó (restrições unárias) e de arco via **AC-3** (restrições binárias).
- **Busca com retrocesso**: atribuição incremental com verificação de consistência, acelerada por inferência (manter consistência de arco) e pelas heurísticas de escolha de variável (**mínimos valores restantes**, **grau**) e de valor (**valor menos restritivo**).

## Requisitos

- Python 3.10+
- `crossword` roda com a biblioteca padrão; a saída opcional em imagem usa **Pillow**.

Cada subpasta tem seu próprio `README.md` com instruções de execução.
