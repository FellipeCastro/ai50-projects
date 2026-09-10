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
| [`uncertainly/pagerank`](./uncertainly/pagerank) | 2 — Uncertainty | Cadeias de Markov, navegante aleatório, amostragem vs. iteração |
| [`uncertainly/heredity`](./uncertainly/heredity) | 2 — Uncertainty | Rede bayesiana, probabilidade conjunta, inferência por enumeração |
| [`optimization/crossword`](./optimization/crossword) | 3 — Optimization | CSP, consistência de arco (AC-3), busca com retrocesso, heurísticas MRV / grau / LCV |
| [`learning/shopping`](./learning/shopping) | 4 — Learning | Aprendizado supervisionado, classificação k-NN, divisão treino/teste, sensibilidade e especificidade |
| [`learning/nim`](./learning/nim) | 4 — Learning | Aprendizado por reforço, Q-learning, epsilon-greedy |

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

### `uncertainly/pagerank`

Estima a **importância relativa** de páginas web pelo algoritmo **PageRank**. Modela um *navegante aleatório* que segue links com probabilidade `0.85` e salta para uma página qualquer com probabilidade `0.15`, e calcula o ranking de duas formas: por **amostragem** (simulação de 10 000 passos) e por **iteração** da fórmula do PageRank até convergir.

```bash
cd uncertainly/pagerank
python pagerank.py corpus0      # ou corpus1, corpus2
```

### `uncertainly/heredity`

Uma **rede bayesiana** que calcula, para cada membro de uma família, a probabilidade de ter 0, 1 ou 2 cópias de um gene e de manifestar a característica associada. Faz **inferência por enumeração**: percorre todas as combinações de genes e características, calcula a probabilidade conjunta de cada cenário e normaliza o resultado.

```bash
cd uncertainly/heredity
python heredity.py data/family0.csv      # ou family1.csv, family2.csv
```

### `optimization/crossword`

Gera **palavras cruzadas**: dada a estrutura de uma grade e um vocabulário, preenche todos os espaços de modo que cada palavra caiba no seu lugar e as letras nas interseções coincidam. Modela o problema como um **CSP** — cada sequência de células é uma variável, o domínio é a lista de palavras — e resolve com **consistência de nó**, **AC-3** e **busca com retrocesso**, guiada pelas heurísticas de mínimos valores restantes, grau e valor menos restritivo.

```bash
cd optimization/crossword
python generate.py data/structure1.txt data/words1.txt              # imprime no terminal
python generate.py data/structure1.txt data/words1.txt output.png   # salva imagem (requer Pillow)
```

### `learning/shopping`

Treina um classificador **k-vizinhos mais próximos** (k-NN) para prever, a partir do comportamento de navegação numa loja online, se a sessão vai **terminar em compra**. Lê ~12 000 sessões de `shopping.csv`, converte cada linha em vetor de atributos, separa 60% para treino e 40% para teste e reporta **sensibilidade** (verdadeiros positivos) e **especificidade** (verdadeiros negativos) — em vez de só a acurácia, que enganaria numa base desbalanceada.

```bash
cd learning/shopping
python shopping.py shopping.csv        # k = 1 (padrão)
python shopping.py shopping.csv 5      # k = 5
```

Requer **scikit-learn** (`pip install scikit-learn`).

### `learning/nim`

Ensina uma IA a jogar **Nim** por **aprendizado por reforço** (Q-learning). A IA treina jogando 10 000 partidas contra si mesma, atualizando `Q(estado, ação)` a cada jogada, e depois enfrenta um humano usando a estratégia **epsilon-greedy** (sem exploração ao jogar de verdade).

```bash
cd learning/nim
python play.py
```

Roda apenas com a biblioteca padrão.

## Requisitos

- Python 3.10+
- `pip` para instalar dependências específicas de cada projeto (ver o `requirements.txt` de cada pasta quando houver)

## Estrutura

```
ai50/
├── search/            # Semana 0 — Search
│   ├── degrees/       # Busca em largura
│   └── tictactoe/     # Minimax
├── knowledge/         # Semana 1 — Knowledge
│   ├── knights/       # Lógica proposicional / model checking
│   └── minesweeper/   # Agente baseado em conhecimento
├── uncertainly/       # Semana 2 — Uncertainty
│   ├── pagerank/      # Cadeias de Markov / navegante aleatório
│   └── heredity/      # Rede bayesiana / inferência por enumeração
├── optimization/      # Semana 3 — Optimization
│   └── crossword/     # CSP / AC-3 / busca com retrocesso
└── learning/          # Semana 4 — Learning
    ├── shopping/      # Classificação k-NN / aprendizado supervisionado
    └── nim/           # Q-learning / aprendizado por reforço
```

Cada pasta e cada projeto tem um `README.md` próprio com detalhes e instruções de execução.

## Licença

Código desenvolvido para fins de estudo, seguindo as especificações do CS50 AI. O material distribuído do curso pertence à Harvard University e está sob a licença Creative Commons BY-NC-SA.
