# Modelos híbridos com a PennyLane

Neste repositório o **Classificador Variacional Quântico** (conhecido como VQC, do inglês **Variational Quantum Classifier**) é apresentado, e um modelo híbrido clássico-quântico é treinado utilizando a biblioteca [PennyLane](https://pennylane.ai/), através de sua interface com o [Keras](https://keras.io/).

### VQC: algoritmo em camadas

O circuito quântico do VQC pode ser esquematicamente visualizado em 3 componentes, ou camadas:

- **Feature map**: parte do circuito responsável por codificar os dados clássicos em estados quânticos que serão processados no circuito quântico pelo algoritmo. Ou seja, é nesse passo que a informação clássica é representada na forma de informação quântica;

- **Variational layer**: parte do circuito parametrizada. Esses são os parâmetros ajustados no processo de treinamento;

- **Medida**: último passo do circuito, que consiste em medidas dos qubits, o que produz informação clássica.

### Um método híbrido

O VQC é um **algoritmo híbrido**, isto é, a rotina completa é **parte clássica** e **parte quântica**.

Podemos imaginar desta maneira:

- O "**forward propagation**" é quântico;

- Com a medida, recuperamos informação clássica, e construímos a função de perda/custo classicamente;

- Os parâmetros são atualizados de modo a otimizar classicamente a função de custo;

- Neste sentido, o "**backpropagation**" é clássico.

Para além disso, construiremos arquiteturas em que o forward propagation também será híbrido (isto é, uma rede neural com camadas clássicas e camadas quânticas, em uma única estrutura sequencial).

### Variacional?!

O "variacional" que nomeia o VQC tem origem nos [métodos variacionais](https://arxiv.org/abs/1812.08767) da mecânica quântica.

Historicamente, estes princípios variacionais têm sido utilizados como métodos aproximativos, notoriamente em problemas de [simulação quântica](https://arxiv.org/abs/1308.6253).

Alguns algoritmos quânticos foram propostos com base nestes métodos, em particular:

- [VQE](https://arxiv.org/abs/2111.05176), que foi introduzido no contexto de simulação quântica;

- [QAOA](https://arxiv.org/abs/1411.4028), que foi introduzido para endereçar problemas de otimização combinatória.

Ambos estes algoritmos são **rotinas híbridas**. Por este motivo, cunhou-se o termo **"algoritmos variacionais"** para designar esta abordagem híbrida, que envolve **circuitos quânticos parametrizados** cujos parâmetros são otimizados classicamente.

___________________________________________

Este repositório contém os seguintes arquivos:

- variational_quantum_classifier_pennylane.ipynb: Notebook com a apresentação e implementação do modelo híbrido em Python, utilizando a PennyLane. O algoritmo é treinado no dataset iris.

- iris.csv: arquivo csv com o dataset iris.

- figuras: pasta com figuras que são utilizadas no markdown do notebook.
