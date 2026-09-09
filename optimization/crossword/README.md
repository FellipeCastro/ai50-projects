# Crossword

Gera **palavras cruzadas**: dada a estrutura de uma grade e uma lista de palavras, preenche todos os espaços de modo que cada palavra caiba no seu lugar e as letras nas interseções coincidam.

## Ideia

O problema é modelado como um **problema de satisfação de restrições (CSP)**:

- cada **variável** é uma sequência de células vazias na grade — uma posição inicial, uma direção (`across` ou `down`) e um comprimento;
- o **domínio** de cada variável é o conjunto de palavras do vocabulário;
- as **restrições** são:
  - *unária* — o comprimento da palavra tem que ser igual ao da variável;
  - *binária* — em cada interseção entre duas variáveis, a letra tem que ser a mesma nas duas palavras;
  - todas as palavras da solução são **distintas**.

A resolução em `generate.py` segue o roteiro clássico de CSP:

1. **Consistência de nó** (`enforce_node_consistency`) — remove do domínio de cada variável as palavras com comprimento errado.
2. **Consistência de arco / AC-3** (`revise`, `ac3`) — remove as palavras que não têm nenhuma correspondente possível numa variável vizinha, propagando a poda pela fila de arcos.
3. **Busca com retrocesso** (`backtrack`) — atribui uma palavra de cada vez, checando a consistência parcial (`consistent`) e voltando atrás quando trava.

A busca usa duas heurísticas:

- **MRV + grau** (`select_unassigned_variable`) — escolhe primeiro a variável com menos palavras restantes no domínio; em caso de empate, a de maior número de vizinhos.
- **Menos restritiva / LCV** (`order_domain_values`) — testa antes as palavras que eliminam menos opções dos vizinhos ainda não atribuídos.

## Como executar

```bash
cd optimization/crossword
python generate.py data/structure1.txt data/words1.txt

# opcional: salva a solução como imagem (requer Pillow)
python generate.py data/structure1.txt data/words1.txt output.png
```

Saída no terminal (blocos preenchidos com letras, `█` para células bloqueadas):

```
██████████████
███████M████R█
███████I████E█
█INTELLIGENCE█
█N█████N████S█
█F█████F████O█
█E███████████
```

Se não houver como preencher a grade, o programa imprime `No solution.`.

## Dados

`data/` traz três pares de arquivos de exemplo:

| Estrutura | Palavras | Observação |
|-----------|----------|------------|
| `structure0.txt` | `words0.txt` (10) | grade pequena, ótima para depurar |
| `structure1.txt` | `words1.txt` (51) | exemplo principal do curso |
| `structure2.txt` | `words2.txt` (3000) | vocabulário grande |

- **Estrutura**: arquivo de texto onde `_` marca uma célula a preencher e qualquer outro caractere (`#`) marca uma célula bloqueada. Todas as linhas juntas definem a grade.
- **Palavras**: uma palavra por linha; são lidas em maiúsculas.

## Arquivos

- `crossword.py` — classes `Variable` e `Crossword` (fornecidas): leem a estrutura e o vocabulário, derivam o conjunto de variáveis, calculam vizinhos e interseções (`overlaps`).
- `generate.py` — classe `CrosswordCreator`. Métodos `letter_grid`, `print`, `save`, `solve` e `main` são fornecidos; `enforce_node_consistency`, `revise`, `ac3`, `assignment_complete`, `consistent`, `order_domain_values`, `select_unassigned_variable` e `backtrack` são implementados no projeto.
- `data/` — pares estrutura/palavras de exemplo.
- `assets/fonts/OpenSans-Regular.ttf` — fonte usada por `save` para renderizar a imagem.

## Requisitos

- Python 3.10+
- Biblioteca padrão para rodar no terminal; **[Pillow](https://pypi.org/project/Pillow/)** apenas para a saída em imagem (`python -m pip install Pillow`).
