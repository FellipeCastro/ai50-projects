# Knights & Knaves

Resolve quebra-cabeças clássicos de **cavaleiros e servos** (*Knights and Knaves*) de Raymond Smullyan usando **lógica proposicional**.

Nesses puzzles:

- um **cavaleiro** (*knight*) sempre fala a verdade;
- um **servo** (*knave*) sempre mente.

A partir das frases ditas por cada personagem, o programa deduz quem é cavaleiro e quem é servo.

## Ideia

Cada personagem `A`, `B`, `C` recebe dois símbolos proposicionais (`AKnight`, `AKnave`, ...). A base de conhecimento comum codifica que cada um é exatamente um dos dois tipos:

```
Or(AKnight, AKnave)          # é cavaleiro ou servo
Not(And(AKnight, AKnave))    # não pode ser os dois
```

Cada afirmação vira um par de implicações: *se o personagem é cavaleiro, a frase é verdadeira*; *se é servo, a frase é falsa*.

```python
Implication(AKnight, frase)
Implication(AKnave, Not(frase))
```

O `model_check` de `logic.py` então enumera todos os modelos possíveis e determina quais símbolos são necessariamente verdadeiros dada a base de conhecimento.

## Como executar

```bash
cd knowledge/knights
python puzzle.py
```

Saída esperada — para cada puzzle, os fatos que a base de conhecimento garante:

```
Puzzle 0
    A is a Knave
Puzzle 1
    A is a Knave
    B is a Knight
...
```

## Arquivos

- `puzzle.py` — definição dos quatro puzzles e das bases de conhecimento (implementado no projeto).
- `logic.py` — motor de lógica proposicional: `Symbol`, `And`, `Or`, `Not`, `Implication`, `Biconditional` e `model_check` (fornecido).

## Requisitos

Python 3.10+ (somente biblioteca padrão).
