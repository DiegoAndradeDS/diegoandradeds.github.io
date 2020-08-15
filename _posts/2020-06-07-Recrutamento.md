---
layout: post
title: How I Rest From Work
date: 2017-09-12 13:32:20 +0300
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: i-rest.jpg # Add image post (optional)
fig-caption: # Add figcaption (optional)
tags: [Holidays, Hawaii]
---

testnado escrever antes alterado

## Introdução


```python

```


```python

```


```python

```


```python
import pandas as pd

df = pd.read_csv("dataset.csv")
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>employee_id</th>
      <th>department</th>
      <th>region</th>
      <th>education</th>
      <th>gender</th>
      <th>recruitment_channel</th>
      <th>no_of_trainings</th>
      <th>age</th>
      <th>previous_year_rating</th>
      <th>length_of_service</th>
      <th>KPIs_met &gt;80%</th>
      <th>awards_won?</th>
      <th>avg_training_score</th>
      <th>is_promoted</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>65438</td>
      <td>Sales &amp; Marketing</td>
      <td>region_7</td>
      <td>Master's &amp; above</td>
      <td>f</td>
      <td>sourcing</td>
      <td>1</td>
      <td>35</td>
      <td>5.0</td>
      <td>8</td>
      <td>1</td>
      <td>0</td>
      <td>49</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>65141</td>
      <td>Operations</td>
      <td>region_22</td>
      <td>Bachelor's</td>
      <td>m</td>
      <td>other</td>
      <td>1</td>
      <td>30</td>
      <td>5.0</td>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>60</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7513</td>
      <td>Sales &amp; Marketing</td>
      <td>region_19</td>
      <td>Bachelor's</td>
      <td>m</td>
      <td>sourcing</td>
      <td>1</td>
      <td>34</td>
      <td>3.0</td>
      <td>7</td>
      <td>0</td>
      <td>0</td>
      <td>50</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2542</td>
      <td>Sales &amp; Marketing</td>
      <td>region_23</td>
      <td>Bachelor's</td>
      <td>m</td>
      <td>other</td>
      <td>2</td>
      <td>39</td>
      <td>1.0</td>
      <td>10</td>
      <td>0</td>
      <td>0</td>
      <td>50</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>48945</td>
      <td>Technology</td>
      <td>region_26</td>
      <td>Bachelor's</td>
      <td>m</td>
      <td>other</td>
      <td>1</td>
      <td>45</td>
      <td>3.0</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>73</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```

### Limpando os dados 


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 54808 entries, 0 to 54807
    Data columns (total 14 columns):
     #   Column                Non-Null Count  Dtype  
    ---  ------                --------------  -----  
     0   employee_id           54808 non-null  int64  
     1   department            54808 non-null  object 
     2   region                54808 non-null  object 
     3   education             52399 non-null  object 
     4   gender                54808 non-null  object 
     5   recruitment_channel   54808 non-null  object 
     6   no_of_trainings       54808 non-null  int64  
     7   age                   54808 non-null  int64  
     8   previous_year_rating  50684 non-null  float64
     9   length_of_service     54808 non-null  int64  
     10  KPIs_met >80%         54808 non-null  int64  
     11  awards_won?           54808 non-null  int64  
     12  avg_training_score    54808 non-null  int64  
     13  is_promoted           54808 non-null  int64  
    dtypes: float64(1), int64(8), object(5)
    memory usage: 5.9+ MB
    


```python
df.isnull().sum()
```




    employee_id                0
    department                 0
    region                     0
    education               2409
    gender                     0
    recruitment_channel        0
    no_of_trainings            0
    age                        0
    previous_year_rating    4124
    length_of_service          0
    KPIs_met >80%              0
    awards_won?                0
    avg_training_score         0
    is_promoted                0
    dtype: int64




```python
df["previous_year_rating"].describe()
```




    count    50684.000000
    mean         3.329256
    std          1.259993
    min          1.000000
    25%          3.000000
    50%          3.000000
    75%          4.000000
    max          5.000000
    Name: previous_year_rating, dtype: float64




```python
df["education"].unique()
```




    array(["Master's & above", "Bachelor's", nan, 'Below Secondary'],
          dtype=object)




```python
# Colocando Below Secondary nos valores faltantes em education e 0 para previous_year_rating
```


```python
contarM = df["education"] == "Master's & above"
contarB = df["education"] == "Bachelor's"
contarS = df["education"] == "Below Secondary"


print(contarM.sum())
print(contarB.sum())
print(contarS.sum())
```

    14925
    36669
    805
    


```python
df["education"].fillna("Below Secondary", inplace = True)
df["previous_year_rating"].fillna(0, inplace = True)
df.isnull().sum()
```




    employee_id             0
    department              0
    region                  0
    education               0
    gender                  0
    recruitment_channel     0
    no_of_trainings         0
    age                     0
    previous_year_rating    0
    length_of_service       0
    KPIs_met >80%           0
    awards_won?             0
    avg_training_score      0
    is_promoted             0
    dtype: int64




```python

```

## Análise Exploratória dos Dados 


```python
df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>employee_id</th>
      <th>department</th>
      <th>region</th>
      <th>education</th>
      <th>gender</th>
      <th>recruitment_channel</th>
      <th>no_of_trainings</th>
      <th>age</th>
      <th>previous_year_rating</th>
      <th>length_of_service</th>
      <th>KPIs_met &gt;80%</th>
      <th>awards_won?</th>
      <th>avg_training_score</th>
      <th>is_promoted</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>65438</td>
      <td>Sales &amp; Marketing</td>
      <td>region_7</td>
      <td>Master's &amp; above</td>
      <td>f</td>
      <td>sourcing</td>
      <td>1</td>
      <td>35</td>
      <td>5.0</td>
      <td>8</td>
      <td>1</td>
      <td>0</td>
      <td>49</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>65141</td>
      <td>Operations</td>
      <td>region_22</td>
      <td>Bachelor's</td>
      <td>m</td>
      <td>other</td>
      <td>1</td>
      <td>30</td>
      <td>5.0</td>
      <td>4</td>
      <td>0</td>
      <td>0</td>
      <td>60</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7513</td>
      <td>Sales &amp; Marketing</td>
      <td>region_19</td>
      <td>Bachelor's</td>
      <td>m</td>
      <td>sourcing</td>
      <td>1</td>
      <td>34</td>
      <td>3.0</td>
      <td>7</td>
      <td>0</td>
      <td>0</td>
      <td>50</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2542</td>
      <td>Sales &amp; Marketing</td>
      <td>region_23</td>
      <td>Bachelor's</td>
      <td>m</td>
      <td>other</td>
      <td>2</td>
      <td>39</td>
      <td>1.0</td>
      <td>10</td>
      <td>0</td>
      <td>0</td>
      <td>50</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>48945</td>
      <td>Technology</td>
      <td>region_26</td>
      <td>Bachelor's</td>
      <td>m</td>
      <td>other</td>
      <td>1</td>
      <td>45</td>
      <td>3.0</td>
      <td>2</td>
      <td>0</td>
      <td>0</td>
      <td>73</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```


```python
import matplotlib.pyplot as plt

plotCorrelationMatrix(df, 8)
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-19-c4db77a74c48> in <module>
          1 import matplotlib.pyplot as plt
          2 
    ----> 3 plotCorrelationMatrix(df, 8)
    

    NameError: name 'plotCorrelationMatrix' is not defined



```python

```


```python

```


```python
df.columns

```




    Index(['employee_id', 'department', 'region', 'education', 'gender',
           'recruitment_channel', 'no_of_trainings', 'age', 'previous_year_rating',
           'length_of_service', 'KPIs_met >80%', 'awards_won?',
           'avg_training_score', 'is_promoted'],
          dtype='object')




```python
df.head()
```

## Modelo 


```python
from sklearn.model_selection import train_test_split
```


```python
varind = ["no_of_trainings" , "age" , "previous_year_rating" , "KPIs_met >80%", \
          "awards_won?" , "avg_training_score"]   # nome das variáveis independentes

alvo = ["is_promoted"]  # variável dependente

X = df[varind]
y = df[alvo]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.2, random_state = 0)
```


```python
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import classification_report, confusion_matrix
```


```python
logistic_classifier = LogisticRegression(random_state = 0)
logistic_classifier.fit(X_train, y_train.values.ravel())
```




    LogisticRegression(random_state=0)




```python
logistic_classifier.intercept_
```




    array([-6.18377766])




```python
logistic_classifier.coef_
```




    array([[-0.20164461, -0.00968186,  0.20143919,  1.34681812,  1.83694804,
             0.04388242]])




```python
logistic_classifier.predict_proba(X_train)
```




    array([[0.93934593, 0.06065407],
           [0.97055804, 0.02944196],
           [0.98057012, 0.01942988],
           ...,
           [0.92726779, 0.07273221],
           [0.70366972, 0.29633028],
           [0.9305093 , 0.0694907 ]])




```python
logistic_classifier.predict(X_train)
```




    array([0, 0, 0, ..., 0, 0, 0], dtype=int64)




```python
logistic_classifier.score(X_train, y_train)
```




    0.915362860922319




```python
logistic_classifier.predict(X_test)
```




    array([0, 0, 0, ..., 0, 0, 0], dtype=int64)




```python
logistic_classifier.score(X_test, y_test)
```




    0.9177157453019522




```python
confusion_matrix(y_test, logistic_classifier.predict(X_test))
```




    array([[9999,   42],
           [ 860,   61]], dtype=int64)




```python
logistic_classifier.predict_proba(X_test)[:,1]
```




    array([0.06371744, 0.06711491, 0.07330348, ..., 0.33516576, 0.27189   ,
           0.26714611])




```python
logistic_classifier.predict_proba(X_test)[:,1].max()  #maior probabilidade
```




    0.8640991629032407




```python
logistic_classifier.predict_proba(X_test)[:,1].argmax()
```




    8861




```python

```


```python
X_test
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>no_of_trainings</th>
      <th>age</th>
      <th>previous_year_rating</th>
      <th>KPIs_met &gt;80%</th>
      <th>awards_won?</th>
      <th>avg_training_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>28686</th>
      <td>1</td>
      <td>34</td>
      <td>3.0</td>
      <td>0</td>
      <td>0</td>
      <td>78</td>
    </tr>
    <tr>
      <th>16191</th>
      <td>1</td>
      <td>40</td>
      <td>4.0</td>
      <td>0</td>
      <td>0</td>
      <td>76</td>
    </tr>
    <tr>
      <th>12951</th>
      <td>2</td>
      <td>29</td>
      <td>0.0</td>
      <td>1</td>
      <td>0</td>
      <td>68</td>
    </tr>
    <tr>
      <th>7890</th>
      <td>2</td>
      <td>30</td>
      <td>5.0</td>
      <td>1</td>
      <td>0</td>
      <td>86</td>
    </tr>
    <tr>
      <th>29387</th>
      <td>1</td>
      <td>52</td>
      <td>3.0</td>
      <td>0</td>
      <td>0</td>
      <td>66</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>10771</th>
      <td>1</td>
      <td>31</td>
      <td>4.0</td>
      <td>0</td>
      <td>0</td>
      <td>62</td>
    </tr>
    <tr>
      <th>35658</th>
      <td>1</td>
      <td>27</td>
      <td>1.0</td>
      <td>0</td>
      <td>0</td>
      <td>82</td>
    </tr>
    <tr>
      <th>35453</th>
      <td>1</td>
      <td>46</td>
      <td>4.0</td>
      <td>1</td>
      <td>0</td>
      <td>91</td>
    </tr>
    <tr>
      <th>6155</th>
      <td>1</td>
      <td>29</td>
      <td>3.0</td>
      <td>1</td>
      <td>0</td>
      <td>85</td>
    </tr>
    <tr>
      <th>29736</th>
      <td>2</td>
      <td>36</td>
      <td>4.0</td>
      <td>1</td>
      <td>0</td>
      <td>86</td>
    </tr>
  </tbody>
</table>
<p>10962 rows × 6 columns</p>
</div>




```python
df.iloc[logistic_classifier.predict_proba(X_test)[:,1].argmax()]    #mudar X_test por X_topredict
```




    employee_id                   45153
    department              Procurement
    region                    region_11
    education                Bachelor's
    gender                            m
    recruitment_channel        sourcing
    no_of_trainings                   2
    age                              31
    previous_year_rating              3
    length_of_service                 4
    KPIs_met >80%                     0
    awards_won?                       0
    avg_training_score               70
    is_promoted                       0
    Name: 8861, dtype: object




```python

```


```python

```
