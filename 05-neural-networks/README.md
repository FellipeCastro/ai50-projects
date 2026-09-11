# Semana 5 — Neural Networks

Projeto sobre **redes neurais artificiais**: em vez de extrair características à mão, camadas de neurônios aprendem diretamente a partir dos dados brutos (no caso, pixels de imagens) quais padrões importam para a tarefa.

| Projeto | Conceitos aplicados |
|---------|---------------------|
| [`traffic`](./traffic) | Rede neural convolucional (CNN), TensorFlow/Keras, classificação de imagens |

## Conceitos da semana

- **Rede neural**: camadas de unidades (neurônios) conectadas por pesos; cada camada aplica uma combinação linear dos dados de entrada seguida de uma **função de ativação** (ReLU, softmax) para introduzir não-linearidade.
- **Rede neural convolucional (CNN)**: usa camadas `Conv2D` com **filtros/kernels** que percorrem a imagem detectando padrões locais (bordas, texturas, formas), e camadas `MaxPooling2D` que reduzem a dimensão espacial mantendo as características mais relevantes.
- **Flatten e camadas densas**: depois das convoluções, o volume de características é achatado em um vetor e passado por camadas totalmente conectadas (`Dense`) para combinar as características extraídas e chegar à classificação final.
- **Dropout**: desativa aleatoriamente uma fração dos neurônios durante o treino para reduzir **overfitting** e melhorar a generalização.
- **Treino e avaliação**: os dados são divididos em treino e teste; o modelo é otimizado por várias **épocas** (`epochs`) minimizando uma função de perda (`categorical_crossentropy`), e a acurácia final é medida no conjunto de teste, nunca visto durante o treino.

## Requisitos

- Python 3.10+
- `traffic` usa **OpenCV**, **scikit-learn** e **TensorFlow** (`pip install -r traffic/requirements.txt`)

Cada subpasta tem seu próprio `README.md` com instruções de execução.
