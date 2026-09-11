# Semana 4 — Learning

Projetos sobre **aprendizado de máquina**: em vez de programar as regras à mão, o sistema descobre padrões a partir de dados (aprendizado supervisionado) ou da própria experiência (aprendizado por reforço).

| Projeto | Conceitos aplicados |
|---------|---------------------|
| [`shopping`](./shopping) | Aprendizado supervisionado, classificação, k-vizinhos mais próximos (k-NN), divisão treino/teste, sensibilidade e especificidade |
| [`nim`](./nim) | Aprendizado por reforço, Q-learning, estimativa de valor de ação, exploração vs. exploração (epsilon-greedy) |

## Conceitos da semana

- **Aprendizado supervisionado**: aprender uma função a partir de pares entrada–rótulo. Tarefas de **classificação** (rótulo discreto) e **regressão** (valor contínuo).
- **k-vizinhos mais próximos**: classifica um ponto pela classe mais comum entre os `k` exemplos de treino mais próximos.
- **Avaliação de modelos**: separar dados de treino e de teste; além da acurácia, medir **sensibilidade** (taxa de verdadeiros positivos) e **especificidade** (taxa de verdadeiros negativos), essenciais em bases desbalanceadas.
- **Overfitting e regularização**: equilibrar ajuste aos dados de treino e capacidade de generalizar.
- **Aprendizado por reforço**: um agente age no ambiente, recebe recompensas e ajusta sua política. No **Q-learning**, aprende `Q(estado, ação)` — a recompensa esperada de tomar uma ação num estado — pela regra de atualização temporal.
- **Exploração vs. exploração**: a estratégia **epsilon-greedy** joga aleatoriamente com probabilidade `epsilon` para descobrir estados novos e, no restante das vezes, escolhe a melhor ação conhecida.

## Requisitos

- Python 3.10+
- `shopping` usa **scikit-learn** (`pip install scikit-learn`); `nim` roda apenas com a biblioteca padrão.

Cada subpasta tem seu próprio `README.md` com instruções de execução.
