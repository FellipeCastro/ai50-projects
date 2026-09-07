# CS50's Introduction to Artificial Intelligence with Python

Repositório com os projetos desenvolvidos ao longo do curso **[CS50's Introduction to Artificial Intelligence with Python](https://cs50.harvard.edu/ai/)**, oferecido pela Harvard University.

O curso explora os conceitos e algoritmos que fundamentam a inteligência artificial moderna: busca, conhecimento, incerteza, otimização, aprendizado de máquina, redes neurais e processamento de linguagem natural.

## Projetos

| Projeto | Semana / Tema | Conceitos aplicados |
|---------|---------------|---------------------|
| [`search/degrees`](./search/degrees) | 0 — Search | Busca em largura (BFS), fronteira de fila, problema do menor caminho |
| [`search/tictactoe`](./search/tictactoe) | 0 — Search | Adversarial search, algoritmo Minimax, jogos de soma zero |

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

## Requisitos

- Python 3.10+
- `pip` para instalar dependências específicas de cada projeto (ver o `requirements.txt` de cada pasta quando houver)

## Estrutura

```
ai50/
└── search/            # Semana 0 — Search
    ├── degrees/       # Busca em largura
    └── tictactoe/     # Minimax
```

## Licença

Código desenvolvido para fins de estudo, seguindo as especificações do CS50 AI. O material distribuído do curso pertence à Harvard University e está sob a licença Creative Commons BY-NC-SA.
