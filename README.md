<h1 align="center" style="font-weight: bold;">Metric Learning para Reconhecimento Facial 🧠</h1>

<p align="center">
    <img src="https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54" alt="Python"/>
    <img src="https://img.shields.io/badge/Keras-%23D00000.svg?style=for-the-badge&logo=Keras&logoColor=white" alt="Keras"/>
    <img src="https://img.shields.io/badge/TensorFlow-%23FF6F00.svg?style=for-the-badge&logo=TensorFlow&logoColor=white" alt="TensorFlow"/>
    <img src="https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white" alt="NumPy"/>
    <img src="https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="Scikit-Learn"/>
</p>

<p align="center">
  <a href="#projeto">Projeto</a> •
  <a href="#problema">Problema</a> • 
  <a href="#solucao">Solução</a> •
</p>

<h2 id="projeto">📫 Projeto</h2>

Este projeto tem como objetivo desenvolver um sistema de reconhecimento facial utilizando **Metric Learning**, especialmente para situações onde novas identidades são constantemente adicionadas, como em **portarias de prédios residenciais ou comerciais**.

<h2 id="problema">🧩 O Problema</h2>

Em sistemas convencionais de reconhecimento facial, cada pessoa é tratada como uma **classe distinta** em classificadores. Isso gera um grande problema:

- Sempre que uma nova pessoa entra no sistema, seria necessário **re-treinar o modelo inteiro** para incluir essa nova identidade.
- Isso torna o processo **pouco escalável e inviável** para sistemas dinâmicos como os de portarias.

Além disso, sistemas com classes fixas **não conseguem lidar com indivíduos desconhecidos**, o que limita sua aplicação no mundo real.

<h2 id="solucao">🔍 A Solução: Metric Learning</h2>

Para contornar esses problemas, foi adotada uma abordagem de **Metric Learning**, onde o foco não é classificar rostos diretamente, mas sim **aprender um espaço vetorial em que rostos parecidos fiquem próximos** e diferentes fiquem distantes.

- Utiliza-se a rede **VGG16 pré-treinada no ImageNet** como base para extrair **vetores de características (embeddings)** dos rostos.
- O modelo é treinado usando o formato de **triplets** (âncora, positivo e negativo), com a **Triplet Loss** como função de perda.
- Ao fim, cada rosto é representado por um vetor, e o reconhecimento é feito comparando esses vetores.

### 📏 Distância Euclidiana L2

Após o treinamento, para identificar uma pessoa:
- A imagem de entrada é convertida em embedding.
- Esse vetor é comparado com todos os vetores do **banco de dados simulado**, usando **distância Euclidiana (L2)**.
- A menor distância determina a pessoa mais parecida.

Essa abordagem permite **adicionar novas pessoas ao sistema sem precisar re-treinar o modelo**, bastando apenas gerar e armazenar seus vetores.
