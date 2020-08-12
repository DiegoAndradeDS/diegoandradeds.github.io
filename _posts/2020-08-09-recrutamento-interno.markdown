---
layout: post
title: Machine Learning aplicada em processo de seleção interna (Recursos Humanos)
date: 2020-08-09 13:32:20 +0300
description: Neste projeto criei um modelo de Machine Learning para identificar qual funcionário deve ser promovido. # Add post description (optional)
img: recrutamento.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Data Science, Python, Machine Learning, Recursos Humanos, Recrutamento e Seleção, Recrutamento interno]
---
*Neste projeto é desenvolvido um modelo de Machine Learning para identificar qual colaborador deve ser promovido.* 


# Introdução

<p align=justify> O recrutamento interno é feito com funcionários da própria empresa. O primeiro passo na procura de pessoal é o recrutamento dentro da empresa, assim aproveitando e dando oportunidades aos funcionários já existentes na organização. O recrutamento interno exige uma série de dados e informações relacionadas, como: resultado dos testes de seleção, resultado das avaliações de desempenho, resultado dos programas de treinamento e aperfeiçoamento, exame das análises e discrições de cargos, exames dos planos de carreiras e verificação das condições de promoção e substituição. As grandes vantagens desse processo são a rapidez, os menores custos de recrutamento, seleção e treinamento do pessoal, já se conhece o desempenho anterior do funcionário, a criação de um clima sadio de progresso profissional, o aumento a moral e a motivação dos funcionários, desenvolvimento de uma positiva e sadia competição entre as pessoas. Após e etapa de recrutamento é necessário fazer o processo de seleção onde, a organização escolhe de uma lista de candidatos, a pessoa que melhor alcança os critérios de seleção, para a posição disponível, considerando as atuais condições de mercado. </p>

## O problema

O departamento de Recursos Humanos atualmente possui um processo de coleta, processamento e análise dos dados, que é em sua maior parte manual. Dessa forma o RH enfrenta um problema 


A Ciência de Dados está revolucionando o modo com que o setor de Recursos Humanos funciona, trazendo uma maior eficiência e melhores resultados. Recursos Humanos 


## Context
HR analytics is revolutionising the way human resources departments operate, leading to higher efficiency and better results overall. Human resources has been using analytics for years. However, the collection, processing and analysis of data has been largely manual, and given the nature of human resources dynamics and HR KPIs, the approach has been constraining HR. Therefore, it is surprising that HR departments woke up to the utility of machine learning so late in the game. Here is an opportunity to try predictive analytics in identifying the employees most likely to get promoted.

## Content
Your client is a large MNC and they have 9 broad verticals across the organisation. One of the problem your client is facing is around identifying the right people for promotion (only for manager position and below) and prepare them in time. Currently the process, they are following is:

They first identify a set of employees based on recommendations/ past performance
Selected employees go through the separate training and evaluation program for each vertical. These programs are based on the required skill of each vertical
At the end of the program, based on various factors such as training performance, KPI completion (only employees with KPIs completed greater than 60% are considered) etc., employee gets promotion.

For above mentioned process, the final promotions are only announced after the evaluation and this leads to delay in transition to their new roles. Hence, company needs your help in identifying the eligible candidates at a particular checkpoint so that they can expedite the entire promotion cycle.

They have provided multiple attributes around Employee's past and current performance along with demographics. Now, The task is to predict whether a potential promotee at checkpoint in the test set will be promoted or not after the evaluation process.

## Acknowledgements
This data set has been scraped from a contest held by https://www.analyticsvidhya.com/



## testando

```python
import numpy as np

def test_function(x, y):
   z = np.sum(x,y)
      return z
```

{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Introdução"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 4,
   "metadata": {},
   "outputs": [],
   "source": [
    "import pandas as pd"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 5,
   "metadata": {},
   "outputs": [],
   "source": [
    "df = pd.read_csv(\"dataset.csv\")"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Limpando os dados "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 6,
   "metadata": {},
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "<class 'pandas.core.frame.DataFrame'>\n",
      "RangeIndex: 54808 entries, 0 to 54807\n",
      "Data columns (total 14 columns):\n",
      " #   Column                Non-Null Count  Dtype  \n",
      "---  ------                --------------  -----  \n",
      " 0   employee_id           54808 non-null  int64  \n",
      " 1   department            54808 non-null  object \n",
      " 2   region                54808 non-null  object \n",
      " 3   education             52399 non-null  object \n",
      " 4   gender                54808 non-null  object \n",
      " 5   recruitment_channel   54808 non-null  object \n",
      " 6   no_of_trainings       54808 non-null  int64  \n",
      " 7   age                   54808 non-null  int64  \n",
      " 8   previous_year_rating  50684 non-null  float64\n",
      " 9   length_of_service     54808 non-null  int64  \n",
      " 10  KPIs_met >80%         54808 non-null  int64  \n",
      " 11  awards_won?           54808 non-null  int64  \n",
      " 12  avg_training_score    54808 non-null  int64  \n",
      " 13  is_promoted           54808 non-null  int64  \n",
      "dtypes: float64(1), int64(8), object(5)\n",
      "memory usage: 5.9+ MB\n"
     ]
    }
   ],
   "source": [
    "df.info()"
   ]
  },


