# Traffic

Treina uma **rede neural convolucional (CNN)** para reconhecer **sinais de trânsito** a partir de imagens, usando o dataset **GTSRB** (German Traffic Sign Recognition Benchmark) — 43 categorias de sinais.

## Ideia

O fluxo é:

1. **`load_data`** percorre `data_dir`, que tem uma subpasta por categoria (`0` a `42`), lê cada imagem com **OpenCV**, redimensiona para `IMG_WIDTH x IMG_HEIGHT` (30x30) e monta duas listas: `images` (arrays `30x30x3`) e `labels` (o número da categoria, tirado do nome da pasta).
2. Os rótulos viram **one-hot** (`tf.keras.utils.to_categorical`) e os dados são divididos em 60% treino / 40% teste (`TEST_SIZE = 0.4`).
3. **`get_model`** monta e compila a CNN com **Keras**:
   - 3 blocos de `Conv2D` (32 → 64 → 128 filtros, kernel 3x3, ReLU) cada um seguido de `MaxPooling2D` (2x2), para extrair características das imagens e reduzir sua dimensão progressivamente;
   - `Flatten` para achatar o volume resultante em um vetor;
   - camada densa (`Dense`) de 128 unidades com ReLU;
   - `Dropout(0.5)` para reduzir overfitting;
   - camada de saída `Dense(NUM_CATEGORIES, activation="softmax")`, uma unidade por categoria de sinal.
4. O modelo é treinado por `EPOCHS = 10` (`model.fit`) e avaliado no conjunto de teste (`model.evaluate`).
5. Se um segundo argumento for passado na linha de comando, o modelo treinado é salvo em disco (`model.save`) no formato `.h5`, podendo ser recarregado depois sem re-treinar.

## Como executar

```bash
cd neural-networks/traffic
pip install -r requirements.txt
python traffic.py gtsrb                # treina e avalia, sem salvar
python traffic.py gtsrb modelo.h5       # treina, avalia e salva o modelo
```

Saída esperada (os números variam a cada execução por causa da divisão aleatória):

```
loaded: gtsrb/0
loaded: gtsrb/1
...
Epoch 1/10
500/500 [==============================] - 5s 9ms/step - loss: 2.7301 - accuracy: 0.2984
...
Epoch 10/10
500/500 [==============================] - 4s 8ms/step - loss: 0.1234 - accuracy: 0.9612
333/333 - 1s - loss: 0.1567 - accuracy: 0.9543
Model saved to modelo.h5.
```

## Dados

`gtsrb/` — 43 subpastas (`0` a `42`), uma por categoria de sinal de trânsito, totalizando cerca de 26.600 imagens `.ppm` de tamanhos variados (redimensionadas para 30x30 no carregamento).

## Arquivos

- `traffic.py` — `main` (fornecido); `load_data` e `get_model` implementados no projeto.
- `gtsrb/` — base de imagens do GTSRB, organizada por categoria.

## Requisitos

Python 3.10+ e as bibliotecas em `requirements.txt`:

```bash
pip install -r requirements.txt
```

- [OpenCV](https://opencv.org/) (`opencv-python`) — leitura e redimensionamento das imagens;
- [scikit-learn](https://scikit-learn.org/) — divisão treino/teste;
- [TensorFlow](https://www.tensorflow.org/) — construção e treino da rede neural.
