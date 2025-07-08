#🧠 Metric Learning para Reconhecimento Facial
Este projeto explora o uso de Metric Learning como alternativa eficiente ao problema de reconhecimento facial em contextos onde a base de dados de pessoas está em constante crescimento, como por exemplo em portarias de prédios residenciais.

##🧩 O Problema
Em sistemas tradicionais de reconhecimento facial, como classificadores baseados em redes neurais, cada pessoa é tratada como uma classe diferente. Isso gera um problema de escalabilidade:

Cada vez que uma nova pessoa entra no prédio, seria necessário re-treinar todo o modelo para adicionar essa nova classe.

Além disso, esse tipo de abordagem não lida bem com novas identidades ou com classes desconhecidas.

Esse tipo de retrabalho torna o sistema inviável na prática.

##🎯 A Solução: Metric Learning
Para resolver esse problema, aplicamos Metric Learning, uma abordagem que não aprende a classificar diretamente, mas sim a medir a similaridade entre rostos.

A ideia é treinar a rede para gerar um vetor de características (embedding) que represente cada rosto.

A rede é treinada usando o formato de triplets (âncora, positivo e negativo), buscando minimizar a distância entre exemplos da mesma pessoa (âncora e positivo) e maximizar a distância para exemplos de pessoas diferentes (âncora e negativo).

##🧠 Arquitetura do Modelo
Foi utilizada a VGG16 com pesos pré-treinados no ImageNet como base para extração de características.

Camadas finais foram adaptadas para gerar embeddings vetoriais.

O treinamento é feito com triplet loss, ajustando o espaço vetorial para manter pessoas diferentes distantes e pessoas iguais próximas.

##📏 Métrica de Similaridade
Após o treinamento:

O modelo é capaz de transformar qualquer imagem de rosto em um vetor (embedding).

Para realizar o reconhecimento, utilizamos a distância euclidiana (L2) entre o vetor da imagem de entrada e os vetores de um banco de dados simulado.

O rosto mais próximo (menor distância) é retornado como o correspondente.

##🧪 Exemplo de Aplicação
Imagine a entrada de um novo morador. Ao invés de re-treinar o modelo, basta calcular e armazenar o embedding da foto do novo morador.
Na próxima vez que ele aparecer, o sistema só precisa comparar os vetores — sem precisar alterar o modelo.

##📚 Tecnologias e Ferramentas
TensorFlow / Keras
VGG16 (ImageNet)
NumPy / Scikit-learn
