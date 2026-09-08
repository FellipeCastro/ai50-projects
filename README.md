# CS50's Introduction to Artificial Intelligence with Python

Repositório com os projetos desenvolvidos ao longo do curso **[CS50's Introduction to Artificial Intelligence with Python](https://cs50.harvard.edu/ai/)**, oferecido pela Harvard University.

O curso explora os conceitos e algoritmos que fundamentam a inteligência artificial moderna: busca, conhecimento, incerteza, otimização, aprendizado de máquina, redes neurais e processamento de linguagem natural.

## Projetos

| Projeto | Semana / Tema | Conceitos aplicados |
|---------|---------------|---------------------|
| [`search/degrees`](./search/degrees) | 0 — Search | Busca em largura (BFS), fronteira de fila, problema do menor caminho |
| [`search/tictactoe`](./search/tictactoe) | 0 — Search | Adversarial search, algoritmo Minimax, jogos de soma zero |
| [`knowledge/knights`](./knowledge/knights) | 1 — Knowledge | Lógica proposicional, base de conhecimento, model checking |
| [`knowledge/minesweeper`](./knowledge/minesweeper) | 1 — Knowledge | Agente baseado em conhecimento, inferência com sentenças lógicas |

### `search/degrees`

Determina quantos "graus de separação" existem entre dois atores, com base em filmes em que atuaram juntos (inspirado no jogo *Six Degrees of Kevin Bacon*). Modela o problema como uma busca em grafo — pessoas são nós, filmes são as arestas — e usa **busca em largura** para encontrar o caminho mais curto.

```bash
cd search/degrees
python degrees.py large      # ou: python degrees.py small
```

Os dados estão em `search/degrees/large` e `search/degrees/small` (arquivos `people.csv`, `movies.csv`, `stars.csv`).

### `search/tictactoe`

Implementa um jogo da velha com uma IA que joga de forma **ótima** usando o algoritmo **Minimax**. A IA nunca perde: sempre vence ou empata.

```bash
cd search/tictactoe
pip install -r requirements.txt
python runner.py
```

O `runner.py` fornece a interface gráfica em Pygame; toda a lógica de jogo e da IA está em `tictactoe.py`.

### `knowledge/knights`

Resolve quebra-cabeças de *cavaleiros e servos* (Knights and Knaves) com **lógica proposicional**. Cada afirmação vira um par de implicações e o `model_check` de `logic.py` enumera os modelos para deduzir quem fala a verdade e quem mente.

```bash
cd knowledge/knights
python puzzle.py
```

### `knowledge/minesweeper`

Um **agente baseado em conhecimento** que joga Campo Minado. Mantém sentenças lógicas do tipo "exatamente N destas células são minas" e infere células seguras e minas, inclusive pela regra do subconjunto.

```bash
cd knowledge/minesweeper
pip install -r requirements.txt
python runner.py
```

A lógica está em `minesweeper.py`; a interface gráfica em Pygame está em `runner.py`.

## Requisitos

- Python 3.10+
- `pip` para instalar dependências específicas de cada projeto (ver o `requirements.txt` de cada pasta quando houver)

## Estrutura

```
ai50/
├── search/            # Semana 0 — Search
│   ├── degrees/       # Busca em largura
│   └── tictactoe/     # Minimax
└── knowledge/         # Semana 1 — Knowledge
    ├── knights/       # Lógica proposicional / model checking
    └── minesweeper/   # Agente baseado em conhecimento
```

Cada pasta e cada projeto tem um `README.md` próprio com detalhes e instruções de execução.

## Licença

Código desenvolvido para fins de estudo, seguindo as especificações do CS50 AI. O material distribuído do curso pertence à Harvard University e está sob a licença Creative Commons BY-NC-SA.
