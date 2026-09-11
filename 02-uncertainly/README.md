# Semana 2 — Uncertainty

Projetos sobre **raciocínio sob incerteza**: como um agente representa e atualiza graus de crença quando não tem certeza sobre o estado do mundo, usando probabilidade.

| Projeto | Conceitos aplicados |
|---------|---------------------|
| [`pagerank`](./pagerank) | Cadeias de Markov, modelo de navegante aleatório, amostragem vs. iteração até convergência |
| [`heredity`](./heredity) | Rede bayesiana, probabilidade conjunta, inferência por enumeração, normalização |

## Conceitos da semana

- **Probabilidade**: eventos, distribuições, probabilidade condicional, regra de Bayes e regra da cadeia.
- **Cadeias de Markov**: o próximo estado depende apenas do estado atual; distribuição estacionária.
- **Redes bayesianas**: grafo acíclico dirigido em que cada nó é uma variável aleatória condicionada aos pais.
- **Inferência**: cálculo de `P(consulta | evidência)` por enumeração de todos os cenários compatíveis, seguido de normalização.

## Requisitos

- Python 3.10+
- Ambos os projetos usam apenas a biblioteca padrão.

Cada subpasta tem seu próprio `README.md` com instruções de execução.
