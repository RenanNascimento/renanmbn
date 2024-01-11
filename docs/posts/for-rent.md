---
date: 2021-07-25
categories:
  - project
---

For Rent é um projeto *end-to-end* sobre predizer valores de aluguel no Brasil.

<!-- more -->

Foi feita uma análise de uma base de dados com 10.692 registros de aluguéis
de casas e apartamentos em 5 cidades. Comparando modelos de regressão,
o *Random Forest* obteve R<sup>2</sup> de 0,98 e foi eleito o mais satisfatório.
O modelo foi salvo em um *bucket S3* e exposto por meio de um *endpoint* 
criado usando Flask e publicado no Heroku.

Por fim, criou-se uma aplicação em React
com um formulário em que os campos são os atributos com que o modelo foi 
treinado, e a partir daí é possível interagir com o modelo através do
*endpoint* e visualizar os valores de aluguel preditos.

Para acessar a aplicação basta entrar [aqui](https://renannascimento.github.io/for-rent/).

Mais informações podem ser encontradas no repositório do
[projeto](https://github.com/renannascimento/for-rent).