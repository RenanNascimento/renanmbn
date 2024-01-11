---
date: 2021-08-16
categories:
  - notes
---

# Anotação: O que é Machine Learning?

Este artigo são as anotações que fiz lendo a seção *O que é Machine Learning?* do livro [Deep Learning for Coders with fastai & PyTorch](https://www.oreilly.com/library/view/deep-learning-for/9781492045519/).

<!-- more -->

*Machine Learning* é uma forma de fazer com que os computadores executem tarefas. A maneira 
tradicional de se fazer isto é simplesmente criando um programa que recebe *inputs*, faz 
algum processamento e traz um resultado.

Mas em 1949, Arthur Samuel, um pesquisador da IBM, começou a trabalhar em
uma nova forma de fazer os computadores completarem tarefas, que ele veio
a chamar de *Machine Learning*.

Segundo Arthur, ao invés de escrever o passo a passo que os programas
deveriam seguir para executar uma tarefa, deveria-se mostrar exemplos do problema
que se quer resolver e deixar o próprio computador descobrir a melhor forma 
de resolvê-lo.

Então, sua ideia segue o processo de passar *inputs* e pesos (*weights*)
para o programa (*model*), gerar um resultado e a partir dele avaliar
a performance do modelo. Com tal avaliação e realizando várias interações,
os pesos são ajustados de forma
a maximizar a performance para obter resultados satisfatórios.
A figura abaixo ilustra esse processo.

<p align="center"><img src="https://i.imgur.com/SIYACiU.png" /></p>

Mais detalhes podem ser encontrados no [livro](https://www.oreilly.com/library/view/deep-learning-for/9781492045519/) e [videoaula](https://www.youtube.com/watch?v=_QUEXsHfsA0) criados pelos autores.