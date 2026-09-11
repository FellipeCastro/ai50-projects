# Shopping

Treina um classificador **k-vizinhos mais próximos** (k-NN) para prever, a partir do comportamento de navegação de um usuário numa loja online, se aquela sessão vai **terminar em compra** (`Revenue`).

## Ideia

O dataset `shopping.csv` tem cerca de 12.000 sessões, cada uma com 17 atributos (páginas visitadas e tempo em cada tipo, taxas de rejeição e saída, valor das páginas, proximidade de data especial, mês, sistema operacional, navegador, região, tipo de tráfego, tipo de visitante e se foi fim de semana) e um rótulo booleano `Revenue`.

O fluxo é:

1. **`load_data`** lê o CSV e converte cada linha em uma lista de números (`evidence`) mais o rótulo `0/1` (`labels`). As conversões não triviais:
   - `Month` → índice `0` (Jan) a `11` (Dec);
   - `VisitorType` → `1` para `Returning_Visitor`, `0` para o resto;
   - `Weekend` e `Revenue` → `1`/`0` a partir de `TRUE`/`FALSE`.
2. **`train_test_split`** separa 60% dos dados para treino e 40% para teste (`TEST_SIZE = 0.4`).
3. **`train_model`** ajusta um `KNeighborsClassifier` com `n_neighbors = k`.
4. **`evaluate`** compara previsões com os rótulos reais e devolve:
   - **sensibilidade** (taxa de verdadeiros positivos) — proporção de compras reais que o modelo acertou;
   - **especificidade** (taxa de verdadeiros negativos) — proporção de não-compras que o modelo acertou.

As duas métricas são reportadas separadamente porque o dataset é desbalanceado (a maioria das sessões não gera compra), então só a acurácia esconderia o desempenho.

## Como executar

```bash
cd learning/shopping
python shopping.py shopping.csv        # k = 1 (padrão)
python shopping.py shopping.csv 5      # k = 5
```

Saída esperada (os números variam a cada execução por causa da divisão aleatória):

```
Loading Data from csv file...
Data loaded successfully from csv file! Total lines:  12330
Fitting Model using k-Nearest Neighbours Classifier, with k =  1
Correct: 4088
Incorrect: 844
True Positive Rate: 41.02%
True Negative Rate: 90.55%
```

## Dados

`shopping.csv` — colunas na ordem `Administrative`, `Administrative_Duration`, `Informational`, `Informational_Duration`, `ProductRelated`, `ProductRelated_Duration`, `BounceRates`, `ExitRates`, `PageValues`, `SpecialDay`, `Month`, `OperatingSystems`, `Browser`, `Region`, `TrafficType`, `VisitorType`, `Weekend`, `Revenue` (o rótulo).

## Arquivos

- `shopping.py` — `main` (fornecido, com a opção extra de passar `k` pela linha de comando); `load_data`, `train_model` e `evaluate` implementados no projeto.
- `shopping.csv` — base de dados.

## Requisitos

Python 3.10+ e [scikit-learn](https://scikit-learn.org/):

```bash
pip install scikit-learn
```
