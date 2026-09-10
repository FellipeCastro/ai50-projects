# Nim

Ensina uma IA a jogar **Nim** por **aprendizado por reforço** (Q-learning). Depois de treinar jogando milhares de partidas contra si mesma, a IA joga contra um humano.

## O jogo

Começa-se com algumas pilhas de objetos (por padrão `[1, 3, 5, 7]`). Na sua vez, o jogador escolhe **uma** pilha e remove **quantos objetos quiser** dela (pelo menos um). Quem for obrigado a tirar o último objeto **perde**.

## Ideia

O estado do jogo é a tupla de objetos restantes em cada pilha, e uma ação é o par `(i, j)` — remover `j` objetos da pilha `i`. A IA mantém um dicionário `self.q` que mapeia pares `(estado, ação)` para um valor Q (quão boa é aquela jogada).

A cada jogada da partida de treino, o valor Q é atualizado pela fórmula:

```
Q(s, a) <- Q(s, a) + alpha * ((recompensa + recompensa_futura) - Q(s, a))
```

- `alpha` (0.5) — taxa de aprendizado, o quanto uma nova experiência sobrescreve a estimativa antiga;
- `recompensa` — `1` para a jogada que fez o oponente perder, `-1` para a jogada que perdeu o jogo, `0` para as demais;
- `recompensa_futura` — o melhor valor Q disponível no estado resultante.

Na hora de jogar, `choose_action` usa a estratégia **epsilon-greedy**: com probabilidade `epsilon` (0.1) faz uma jogada aleatória (para explorar), senão escolhe a ação de maior valor Q. Contra o humano, `epsilon=False` — a IA sempre joga o que considera melhor.

Funções implementadas no projeto: `get_q_value`, `update_q_value`, `best_future_reward` e `choose_action`.

## Como executar

```bash
cd learning/nim
python play.py
```

`play.py` treina a IA com 10.000 partidas e em seguida abre uma partida interativa:

```
Playing training game 1
Playing training game 2
...
Done training

Piles:
Pile 0: 1
Pile 1: 3
Pile 2: 5
Pile 3: 7

AI's Turn
AI chose to take 1 from pile 2.

Piles:
Pile 0: 1
Pile 1: 3
Pile 2: 4
Pile 3: 7

Your Turn
Choose Pile: 3
Choose Count: 7
...
GAME OVER
Winner is AI
```

Quem começa (humano ou IA) é sorteado a cada execução.

## Arquivos

- `nim.py` — classe `Nim` (regras do jogo) e função `train` (fornecidas); classe `NimAI` com os métodos de Q-learning implementados no projeto; função `play` para a partida humano vs. IA.
- `play.py` — script que treina a IA e inicia uma partida.

## Requisitos

Python 3.10+ (somente biblioteca padrão).
