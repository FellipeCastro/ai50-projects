# Degrees

Determina quantos **graus de separação** existem entre dois atores, com base nos filmes em que atuaram juntos — inspirado no jogo *Six Degrees of Kevin Bacon*.

## Ideia

O problema é modelado como uma **busca em grafo**:

- **nós** → pessoas (atores);
- **arestas** → um filme em que duas pessoas atuaram juntas;
- **objetivo** → o caminho mais curto entre a pessoa de origem e a de destino.

A solução usa **busca em largura (BFS)** com uma fronteira de fila (`QueueFrontier`), o que garante o menor número de conexões, já que todas as arestas têm o mesmo custo. Um conjunto de estados já explorados evita ciclos e retrabalho.

## Como executar

```bash
cd search/degrees
python degrees.py large      # base completa
python degrees.py small      # base reduzida, útil para testes
```

Se nenhum diretório for informado, `large` é usado por padrão. O programa pede o nome de dois atores e imprime a cadeia de filmes que os conecta, ou `Not connected.` se não houver caminho.

## Dados

Cada diretório (`large/`, `small/`) contém três CSVs:

| Arquivo | Conteúdo |
|---------|----------|
| `people.csv` | `id`, `name`, `birth` |
| `movies.csv` | `id`, `title`, `year` |
| `stars.csv` | `person_id`, `movie_id` (relaciona pessoas e filmes) |

## Arquivos

- `degrees.py` — carregamento dos dados e função `shortest_path` (parte implementada no projeto).
- `util.py` — estruturas auxiliares: `Node`, `StackFrontier`, `QueueFrontier` (fornecidas).

## Requisitos

Python 3.10+ (somente biblioteca padrão).
