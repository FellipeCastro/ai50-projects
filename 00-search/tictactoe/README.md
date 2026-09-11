# Tic-Tac-Toe

Jogo da velha com uma IA que joga de forma **ótima** usando o algoritmo **Minimax**. A IA nunca perde: sempre vence ou empata.

## Ideia

É um problema de **busca adversária** num jogo de soma zero e informação perfeita:

- `X` é o jogador maximizador, `O` é o minimizador;
- a cada jogada, o Minimax explora recursivamente toda a árvore de estados até um terminal (vitória, derrota ou empate);
- cada estado terminal vale `+1` (vitória de `X`), `-1` (vitória de `O`) ou `0` (empate);
- a IA escolhe a ação que leva ao melhor valor garantido, assumindo jogo ótimo do oponente.

Como o tabuleiro 3×3 é pequeno, a árvore inteira cabe na busca sem necessidade de poda.

## Como executar

```bash
cd search/tictactoe
pip install -r requirements.txt
python runner.py
```

`runner.py` fornece a interface gráfica em Pygame e deixa o usuário escolher se joga como `X` ou `O`.

## Arquivos

- `tictactoe.py` — regras do jogo e lógica da IA: `player`, `actions`, `result`, `winner`, `terminal`, `utility`, `minimax` (implementados no projeto).
- `runner.py` — interface gráfica (fornecida).
- `OpenSans-Regular.ttf` — fonte usada pela interface.

## Requisitos

- Python 3.10+
- `pygame`
