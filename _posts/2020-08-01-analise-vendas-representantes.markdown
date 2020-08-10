---
layout: post
title: Análise de Vendas
date: 2020-08-01 13:32:20 +0300
description: Visualizações utilizando o Tableau. # Add post description (optional)
img: maquiagem.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Data Science, Visualização, Tableau, Inteligência de Mercado]
---


Inserir texto do projeto aqui

# Titulo do Projeto

## 1. Introdução

Escrever descrição


#### 1.1 Objetivos

Descrever objetivos do projeto

#### 1.2 O Conjunto de dados

A figura abaixo mostra uma parte do conjunto de dados utilizado neste projeto. 

<p align="center">
  <img src="/DiegoAndradeDS/diegoandradeds.github.io/tree/master/assets/img/analise_vendas_representantes/dados.png" >
</p>

<center><img src="https://diegoandradeds.github.io/assets/img/analise_vendas_representantes/dados.png"></center>

![Dados]({{site.baseurl}}/assets/img/analise_vendas_representantes/dados.png)

![Macbook]({{site.baseurl}}/assets/img/mac.jpg)

Descrição das colunas:
* **Representantes:** informa o nome dos representantes de vendas responsável por aquela venda. 
* **Produto:** informa o produto vendido 
* **Quantidade:** Unidades do produto vendido
* **Receita:** Valor em Rúpias Indianas (INR) obtidos na venda
* **Região:** Zona na qual ocorreu a venda

O conjunto de dados completo possui 10 mil linhas, onde temos 72 Representantes de Vendas (RVs), divididos em 4 regiões, para venderem 12 produtos distintos.

## 2. Análise Exploratória dos Dados

No gráfico abaixo podemos visualizar como estão distribuidos os RVs em cada região. As regiões Norte e Oeste são as que possuem mais representantes.

<p align="center">
  <img src="numrepresentantesporregiao.png" >
</p>

Também é importante identificarmos qual a contribuição de cada região para a receita total da empresa conforme mostra o gráfico abaixo.

<p align="center">
  <img src="receitaporregiao.png" >
</p>

Aqui é possível perceber que as regiões (Norte e Oeste) que possuem mais RVs são as que geram maior receita. Não necessariamente isso representa uma relação de causa e efeito, porém seria valida uma análise mais aprofundada para saber o impacto na receita de uma região com a variação do número de representantes que atuam nela. Para isso seria necessário que os dados disponíveis possuissem uma dimensão de tempo.

Para entendermos melhor o comportamento da receita precisamos identificar o impacto de cada produto na receita, conforme pode ser visto pelas barras verdes do gráfico a seguir. A linha laranja representa a quantidade vendida de determinado produto.

<p align="center">
  <img src="comparacaoreceitaeunidadesvendidas.png" >
</p>

O produto Alpen é o que gera mais receita para a empresa, além disso o seu volume de vendas é o mais alto também. Em contrapartida, o produto Halls é o produto menos vendido e também é o que gera menos receita para a empresa. Já os produtos Galaxy e Milka geram uma receita parecida entre 900 mil e 950 mil porém a quantidade de Milka vendida é um pouco mais que o dobro dos Galaxys, isso se deve ao fato dos produtos possuirem preços diferentes conforme pode ser visto no gráfico abaixo que exibe o preço médio de cada produto.  

<p align="center">
  <img src="precomediodosprodutos.png" >
</p>


<p align="center">
  <img src="classificandoprodutos.png" >
</p>
