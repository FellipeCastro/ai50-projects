# Heredity

Calcula, para cada pessoa de uma família, a **probabilidade** de ela ter 0, 1 ou 2 cópias de um gene e de manifestar (ou não) a característica associada — no exemplo do curso, uma versão do gene GJB2 ligada à surdez.

## Ideia

O problema é modelado como uma **rede bayesiana**:

- o número de cópias do gene de cada pessoa (`0`, `1` ou `2`) é uma variável aleatória;
- para quem **não** tem pais no dataset, usa-se a distribuição incondicional `PROBS["gene"]`;
- para quem **tem** pais, o número de cópias depende do que cada pai passa adiante: um pai com 2 cópias passa o gene com probabilidade `1 - mutação`, com 1 cópia passa com `0.5`, e com 0 cópias passa apenas por `mutação` (`0.01`);
- a característica é uma variável que depende só do número de cópias, via `PROBS["trait"]`.

A inferência é feita **por enumeração**. O programa percorre todas as combinações de:

- conjunto `have_trait` — quem manifesta a característica (descartando combinações que contradizem os dados conhecidos);
- conjuntos `one_gene` e `two_genes` — quem tem 1 e quem tem 2 cópias.

Para cada cenário, `joint_probability` calcula a probabilidade conjunta multiplicando as contribuições de cada pessoa. `update` soma essa probabilidade às distribuições de cada pessoa e, no fim, `normalize` reescala cada distribuição para somar 1.

## Como executar

```bash
cd uncertainly/heredity
python heredity.py data/family0.csv      # ou family1.csv, family2.csv
```

Saída esperada (`family0.csv`):

```
Harry:
  Gene:
    2: 0.0092
    1: 0.4557
    0: 0.5351
  Trait:
    True: 0.2665
    False: 0.7335
James:
  Gene:
    2: 0.1976
    1: 0.5106
    0: 0.2918
  Trait:
    True: 1.0000
    False: 0.0000
Lily:
  ...
```

## Dados

Cada CSV em `data/` tem as colunas `name`, `mother`, `father`, `trait`:

- `mother` e `father` ficam em branco ou ambos apontam para nomes válidos do arquivo;
- `trait` é `1` ou `0` quando conhecido, ou em branco quando é justamente o que se quer inferir.

## Arquivos

- `heredity.py` — `PROBS`, `load_data`, `powerset` e `main` (fornecidos); `joint_probability`, `update` e `normalize` implementados no projeto, com as funções auxiliares `check_how_many_copies`, `probs_no_parents` e `probs_has_parents`.

## Requisitos

Python 3.10+ (somente biblioteca padrão).
