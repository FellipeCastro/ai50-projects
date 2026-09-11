# PageRank

Estima a **importância relativa** das páginas de um corpus de HTML pelo algoritmo **PageRank**, usado originalmente pelo Google para ordenar resultados de busca. Uma página é tão importante quanto as páginas que apontam para ela.

## Ideia

O modelo é o do **navegante aleatório**: alguém que começa numa página qualquer e segue clicando em links. A cada passo, com probabilidade `d` (fator de amortecimento, aqui `0.85`) ele segue um link da página atual; com probabilidade `1 - d` ele salta para qualquer página do corpus escolhida ao acaso. Se a página atual não tem links, ele salta para qualquer página com igual probabilidade.

O PageRank de uma página é a fração do tempo que o navegante passa nela no longo prazo. O projeto calcula esse valor de **duas formas independentes**:

1. **Amostragem** (`sample_pagerank`) — simula `SAMPLES = 10000` passos do navegante a partir de uma página aleatória, usando `transition_model` para escolher a próxima página, e conta as visitas.
2. **Iteração** (`iterate_pagerank`) — aplica repetidamente a fórmula do PageRank

   ```
   PR(p) = (1 - d) / N  +  d * Σ  PR(i) / NumLinks(i)
                              i→p
   ```

   partindo de uma distribuição uniforme, até que nenhum valor mude mais que `0.001` entre iterações. Páginas sem links são tratadas como se apontassem para todas as páginas.

Nos dois casos os valores somam 1.

## Como executar

```bash
cd uncertainly/pagerank
python pagerank.py corpus0      # ou corpus1, corpus2
```

Saída esperada:

```
PageRank Results from Sampling (n = 10000)
  1.html: 0.2202
  2.html: 0.4289
  3.html: 0.2202
  4.html: 0.1307
PageRank Results from Iteration
  1.html: 0.2198
  2.html: 0.4294
  3.html: 0.2198
  4.html: 0.1311
```

Os dois métodos devem produzir valores muito próximos.

## Dados

`corpus0/`, `corpus1/` e `corpus2/` são coleções de páginas HTML; os links `<a href="...">` entre elas definem o grafo. `crawl` lê o diretório e ignora links para páginas fora do corpus.

## Arquivos

- `pagerank.py` — `crawl` (fornecido) e as funções implementadas no projeto: `transition_model`, `sample_pagerank`, `iterate_pagerank`.

## Requisitos

Python 3.10+ (somente biblioteca padrão).
