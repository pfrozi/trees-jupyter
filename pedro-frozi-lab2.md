# Laboratório 02- Algoritmos de Indução de Árvores e Florestas Aleatórias

## I. Avaliando um dataset simples com árvores individuais

1. **Todos os atributos foram necessários para fazer a classificação? Caso não, por que razão você acha que isso ocorreu?**  
    Não, o tom de voz não foi necessário. Não há ganho de informação ao testar este atributo em relação aos outros atributos analisados.

2. **Observe os valores de entropia nos nodos folha. Qual a interpretação intuitiva destes valores? Com base neles, é possível inferir algo sobre o quão bem a árvore conseguiria classificar os dados usados durante o seu treinamento?**  
   Nos nós das folhas já é possível determinar a qual classe uma determinada instância pertence, pois todo o conjunto de informação das instâncias daquela folha são homogêneos em relação ao atributo analisado. Desta forma, para os dados utilizados para o treinamento, é possível classificar corretamente todas instâncias.

## II. Comparando árvores individuais e florestas

```
Execução para o exercicio #3 e #4:

(arvore unica #1 para dataset de cancer) Numero de erros de predicao: 5/30	Taxa de erros: 16.67%
(arvore unica #2 para dataset de cancer) Numero de erros de predicao: 1/30	Taxa de erros: 3.33%
(arvore unica #3 para dataset de cancer) Numero de erros de predicao: 0/30	Taxa de erros: 0.00%
```

3. **Que você pode dizer sobre a estrutura da árvore aprendida, com base no subconjunto específico de dados sendo utilizado no treinamento? A estrutura em todos os casos é semelhante? Explique por que razão você acha que isso ocorre;**  
    A estrutura sempre muda, dado os dados de treinamento que foram utilizados. Os Parâmetros considerados nos nós das árvores possuem valores diferentes, fazendo que a estrutura da árvore também seja alterada para se adequar ao novo conjunto de treinamento.

4. **O que você pode dizer sobre o erro de predição de cada árvore? Todas as árvores (treinadas com diferentes subconjuntos de dados) têm performance semelhante? Por que você acha que isso ocorre?**  
    Não. A taxa de erros da primeira árvore é a pior delas (16.67%), seguido pela segunda (3.33%). A terceira árvore, mais equilibrada em relação à profundidade, acaba sendo a que apresenta menos erros. Se observarmos o ganho de informação de cada uma das árvores da raiz em relação ao atributo testado no seguindo nível temos 59% para #1, 69% para #2 e 76% para #3. Além disso, a maior quandidade de níveis e folhas de #1 e #2 faz com que a árvore gerada fique muito ajustada em relação ao conjuto de treinamento (overfitting), o que acaba aumentando o erro de para novas instâncias.

5. **Calcule e informe a média das taxas de erro das três árvores (some as taxas de erro e divida por três).**  
    6,67%.

```
Execução para o exercicio #6:

(arvore unica #1 para dataset de cancer) Numero de erros de predicao: 5/30	Taxa de erros: 16.67%
(arvore unica #2 para dataset de cancer) Numero de erros de predicao: 1/30	Taxa de erros: 3.33%
(arvore unica #3 para dataset de cancer) Numero de erros de predicao: 0/30	Taxa de erros: 0.00%
(voto majoritario para dataset de cancer) Numero de erros de predicao: 0/30	Taxa de erros: 0.00%
```

6. **Qual a taxa de erro de predição obtida quando se usa o sistema de votação entre as árvores da floresta? Caso essa taxa seja menor do que a média das taxas de erros das três árvores, discuta por que razão você acha que isso pode ocorrer.**
    0%, sendo menor que a média das taxas de erro das 3 árvores. As novas instâncias são testadas nas 3 árvores e a decisão quanto a predição da nova instância é atribuida através do voto majoritário de cada uma das árvores. Portanto, para que uma instância seja classificada erroneamente, é necessário que a árvore #1 (16.67%) e #2(3.33%) errem juntas, o que para os dados utilizados representaria uma probabilidade de 0,55%.

```
Execução para o exercicio 7:

(arvore unica para wine, criterio entropy) Numero de erros de predicao: 7/30	Taxa de erros: 23.33%

(arvore unica para wine, criterio gini) Numero de erros de predicao: 2/30	Taxa de erros: 6.67%
```

7. **As árvores geradas são iguais? Há diferença significativa entre as taxas de erro de predição para cada um desses critérios para escolha de atributos durante o treinamento da árvore?**  
   As árvores geradas são diferentes. O critério GINI se mostrou mais eficiente, com um erro de predição de 6.67%, contra 23.33% do critério entropy. Para o GINI, houve uma variação maior nos atributos que são utilizados nos nós, tornando a árvore menos "especializada" em determinados atributos.