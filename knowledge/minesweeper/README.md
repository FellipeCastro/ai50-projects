# Minesweeper

Um **agente baseado em conhecimento** que joga Campo Minado inferindo logicamente quais células são seguras e quais contêm minas.

## Ideia

O agente mantém uma lista de **sentenças** lógicas do tipo:

```
{A, B, C, D} = 2
```

que significa "exatamente 2 destas 4 células são minas". A partir de cada célula revelada (que informa quantas minas há ao redor), o agente:

1. cria uma nova sentença com as células vizinhas ainda desconhecidas e a contagem correspondente;
2. marca como **seguras** as sentenças com `count == 0`, e como **minas** as sentenças em que `count` é igual ao número de células;
3. deriva novas sentenças pela regra do **subconjunto**: se `A ⊆ B`, então `B - A = count(B) - count(A)`;
4. repete a inferência até não haver mais conclusões, escolhendo sempre uma jogada segura conhecida; se não houver, faz uma jogada aleatória entre as células ainda válidas.

## Como executar

```bash
cd knowledge/minesweeper
pip install -r requirements.txt
python runner.py
```

`runner.py` abre a interface em Pygame. O botão **AI Move** pede ao agente a próxima jogada; **Reset** reinicia o tabuleiro.

## Arquivos

- `minesweeper.py` — classes `Minesweeper` (o jogo), `Sentence` (sentença lógica) e `MinesweeperAI` (o agente); a lógica de inferência é implementada no projeto.
- `runner.py` — interface gráfica (fornecida).
- `assets/` — fonte e imagens (bandeira, mina) usadas pela interface.

## Requisitos

- Python 3.10+
- `pygame`
