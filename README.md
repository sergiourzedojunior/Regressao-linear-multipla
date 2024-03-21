# Análise Multivariada de dados - Regressão Linear Múltipla

Aplicações em python com dados financeiros do livro Análise Multivariada da FEA-USP

![tabela](figs/tabela.png) 

## Regressão Linear Múltipla - Técnicas de dependência

file: regressao_linear_multipla.ipynb

Selecionar a variável independente inicial
   Será selecionada aquela que apresentar a maior correlação com a variável dependente
|
|--- A variação percentual explicada é significativa estatisticamente?
|    |
|    |--- Sim
|    |    |
|    |    |--- Existem outras variáveis independentes disponíveis?
|    |    |    |
|    |    |    |--- Não
|    |    |    |    Examinar a adequação da equação preditiva final
|    |    |    |
|    |    |    |--- Sim
|    |    |    |    Selecionar a próxima variável independente
|    |    |    |
|    |    |    |--- A variação percentual explicada pelo conjunto de variáveis é significativa?
|    |    |    |    Verificar com testes F e t cada variável
|    |    |    |
|    |    |    |--- Não
|    |    |         Excluir as variáveis não significativas
|    |
|    |--- Não
|         Não há previsão possível com regressão múltipla


## Resumo:

**Base de dados:**

* Origem: Revista Exame - 500 Melhores & Maiores
* Ano: 2001
* Empresas: Brasileiras de capital aberto, exceto bancos e seguros
* Variáveis:
    * **Dependente:** Rentabilidade do Patrimônio Líquido (RENTPL)
    * **Independentes:**
        * Rentabilidade do Ativo (RENTAT)
        * Alavancagem Operacional (ALOPER)
        * Alavancagem Financeira (ALFIN)
        * Margem Líquida de Vendas (MARVEN)
        * Lucro ou Prejuízo (LUPRE)
* Observações: 297

**Metodologia:**

* Regressão Linear Múltipla
* Método de busca seqüencial stepwise

**Etapas:**

1. Definição das variáveis
2. Análise descritiva das variáveis
3. Cálculo da matriz de correlação
4. Regressão Múltipla Stepwise
    * Seleção das variáveis
    * Avaliação do modelo

**Observações:**

* As primeiras fases da pesquisa (definição da amostra, coleta de dados, etc.) não são abordadas neste estudo.
* A variável "Lucro ou Prejuízo" é qualitativa, enquanto as demais são quantitativas.


**Bibliografia:**

* [https://pt.wikipedia.org/wiki/Regress%C3%A3o_por_stepwise](https://pt.wikipedia.org/wiki/Regress%C3%A3o_por_stepwise)
* FIPECAFI - Fundação Instituto de Pesquisas Contábeis, Atuariais e Financeiras. (2009). Análise multivariada: para os cursos de administração, ciências contábeis e economia. 1. ed. - 2. reimpr. São Paulo: Atlas.



**Resultados:**
* primeiro modelo:

                            OLS Regression Results                            
==============================================================================
Dep. Variable:                     RP   R-squared:                       0.796
Model:                            OLS   Adj. R-squared:                  0.795
Method:                 Least Squares   F-statistic:                     574.7
Date:                Thu, 21 Mar 2024   Prob (F-statistic):          2.60e-102
Time:                        11:51:04   Log-Likelihood:                -1057.4
No. Observations:                 297   AIC:                             2121.
Df Residuals:                     294   BIC:                             2132.
Df Model:                           2                                         
Covariance Type:            nonrobust                                         
==============================================================================
                 coef    std err          t      P>|t|      [0.025      0.975]
------------------------------------------------------------------------------
Intercept     -0.9448      0.497     -1.900      0.058      -1.924       0.034
RA            28.0340      0.879     31.890      0.000      26.304      29.764
MV            -6.1135      0.670     -9.127      0.000      -7.432      -4.795
==============================================================================
Omnibus:                      270.045   Durbin-Watson:                   1.977
Prob(Omnibus):                  0.000   Jarque-Bera (JB):            92770.628
Skew:                           2.653   Prob(JB):                         0.00
Kurtosis:                      89.420   Cond. No.                         2.10
==============================================================================

R-squared: 0.7963222749266814
Adjusted R-squared: 0.7949367121710806
F-statistic: 574.7284067125353
Prob (F-statistic): 0.0
Regression equation: RP = -0.9448381400972627 + 28.03397045411322 * RA + -6.113507421618909 * MV
For every one-unit increase in 'RA', we expect 'RP' to change by 28.03397045411322 units, assuming all other variables remain constant.
For every one-unit increase in 'MV', we expect 'RP' to change by -6.113507421618909 units, assuming all other variables remain constant.
Degrees of freedom (regression): 294.0. This is the number of independent ways by which a dynamic system can move, without violating any constraint imposed on it.
Degrees of freedom (residual): 294.0. This is the number of values in the final calculation of a statistic that are free to vary.
Sum of squares (regression): 21515.436680945346. This is the sum of the squared differences between the prediction for each observation and the population mean.
Sum of squares (residual): 21515.436680945346. This is the sum of the squared differences between each observation and its group's mean.
Mean square (regression): 73.18175741818145. This is the average of the squares of the errors or deviations.
Mean square (residual): 73.18175741818145. This is the average of the squares of the errors or deviations.
F-statistic (ANOVA): nan. This is a measure of how significant the fit of the model is. The higher the F-statistic, the more likely it is that the variables we used for predictions are correlated with the output and can help us predict it.
Prob (F-statistic, ANOVA): nan. This is the probability that the null hypothesis is true (i.e., all of the regression coefficients are zero). The smaller the p-value, the stronger the evidence that at least one of the regression coefficients is not zero.
R-squared: 0.7963222749266814. This is the proportion of the variance in the dependent variable that is predictable from the independent variables.
Adjusted R-squared: 0.7949367121710806. This is the R-squared that has been adjusted for the number of predictors in the model.
F-statistic: 574.7284067125353. This is a measure of how significant the fit of the model is. The higher the F-statistic, the more likely it is that the variables we used for predictions are correlated with the output and can help us predict it.

VIF results
     VIF Factor features
0   7169.281698   NÚMERO
1   7273.504521       ID
2      4.404337   vendas
3      2.458279  plajust
4      4.194092  llajust
5      4.646259  ativoaj
6      7.096914       RP
7      1.875624       AO
8      2.808167       MV
9     10.476515       RA
10     1.871562       AF
11     2.768700    LUPRE
VIF values greater than 5 indicate high multicollinearity.

Durbin-Watson statistic: 1.976686766033608
Values close to 2.0 suggest no autocorrelation. Values towards 0 indicate positive autocorrelation, and values towards 4 indicate negative autocorrelation.

Shapiro-Wilk test: W=0.35958659648895264, p=0.0
The first value is the W test value, and the second value is the p-value. A p-value less than 0.05 suggests the residuals are not normally distributed.
Prob (F-statistic): 0.0. This is the probability that the null hypothesis is true (i.e., all of the regression coefficients are zero). The smaller the p-value, the stronger the evidence that at least one of the regression coefficients is not zero.
Regression equation: RP = -0.9448381400972627 + 28.03397045411322 * RA + -6.113507421618909 * MV
For every one-unit increase in 'RA', we expect 'RP' to change by 28.03397045411322 units, assuming all other variables remain constant.
For every one-unit increase in 'MV', we expect 'RP' to change by -6.113507421618909 units, assuming all other variables remain constant.


R-squared for the testing set: 0.1412590339987353
The model explains very little of the variability in the target variable. It's not a good fit for the data.


* segundo modelo: com variável dummy

                            OLS Regression Results                            
==============================================================================
Dep. Variable:                     RP   R-squared:                       0.752
Model:                            OLS   Adj. R-squared:                  0.751
Method:                 Least Squares   F-statistic:                     446.7
Date:                Thu, 21 Mar 2024   Prob (F-statistic):           7.67e-90
Time:                        11:51:05   Log-Likelihood:                -1086.4
No. Observations:                 297   AIC:                             2179.
Df Residuals:                     294   BIC:                             2190.
Df Model:                           2                                         
Covariance Type:            nonrobust                                         
===============================================================================
                  coef    std err          t      P>|t|      [0.025      0.975]
-------------------------------------------------------------------------------
Intercept       2.4828      0.960      2.587      0.010       0.594       4.371
LUPRE_dummy    -4.8275      1.194     -4.044      0.000      -7.177      -2.478
RA             24.2408      0.818     29.645      0.000      22.631      25.850
==============================================================================
Omnibus:                      261.711   Durbin-Watson:                   2.048
Prob(Omnibus):                  0.000   Jarque-Bera (JB):           100140.389
Skew:                           2.464   Prob(JB):                         0.00
Kurtosis:                      92.821   Cond. No.                         3.34
==============================================================================

Notes:
[1] Standard Errors assume that the covariance matrix of the errors is correctly specified.

ANOVA results
                df        sum_sq       mean_sq           F        PR(>F)
LUPRE_dummy    1.0   1292.310936   1292.310936   14.525536  1.684288e-04
RA             1.0  78185.741179  78185.741179  878.805358  2.514308e-90
Residual     294.0  26156.654248     88.968212         NaN           NaN

VIF results
     VIF Factor     features
0   7169.281698       NÚMERO
1   7273.504521           ID
2      4.404337       vendas
3      2.458279      plajust
4      4.194092      llajust
5      4.646259      ativoaj
6      7.096914           RP
7      1.875624           AO
8      2.808167           MV
9     10.476515           RA
10     1.871562           AF
11          inf        LUPRE
12          inf  LUPRE_dummy
VIF values greater than 5 indicate high multicollinearity.

Durbin-Watson statistic: 2.0480888618088757
Values close to 2.0 suggest no autocorrelation. Values towards 0 indicate positive autocorrelation, and values towards 4 indicate negative autocorrelation.

Shapiro-Wilk test: W=0.32806169986724854, p=0.0
The first value is the W test value, and the second value is the p-value. A p-value less than 0.05 suggests the residuals are not normally distributed.

R-squared: 0.7523857911019034. This is the proportion of the variance in the dependent variable that is predictable from the independent variables.
Adjusted R-squared: 0.7507013407012361. This is the R-squared that has been adjusted for the number of predictors in the model.
F-statistic: 446.6654469634921. This is a measure of how significant the fit of the model is. The higher the F-statistic, the more likely it is that the variables we used for predictions are correlated with the output and can help us predict it.
Prob (F-statistic): 0.0. This is the probability that the null hypothesis is true (i.e., all of the regression coefficients are zero). The smaller the p-value, the stronger the evidence that at least one of the regression coefficients is not zero.
Regression equation: RP = 2.482754078929762 + -4.8275114934565675 * LUPRE_dummy + 24.240771584202506 * RA
For every one-unit increase in 'LUPRE_dummy', we expect 'RP' to change by -4.8275114934565675 units, assuming all other variables remain constant.
For every one-unit increase in 'RA', we expect 'RP' to change by 24.240771584202506 units, assuming all other variables remain constant.
The weight of predictor 'RA' in the final model is -4.8275114934565675
The weight of predictor 'MV' in the final model is 24.240771584202506

R-squared for the testing set: 0.47508484546253604
The model explains a small portion of the variability in the target variable. It may not be a good fit for the data.


**Conclusões:**

apesar do R² ajustado no chegue a quase 80% e no segundo modelo 75%, percebe-se problemas de multicolinearidade nas variáveis utiliadas nos dois modelos e o teste de validação dos resultados no primeiro modelo o modelo explica muito pouco da variabilidade na variável-alvo (RP-RENTPL), em torno de 14%. Não é um bom ajuste para os dados. já no segundo modelo o modelo explica uma pequena parte da variabilidade na variável-alvo (RP-RENTPL), em torno de 47%. Também não é um bom ajuste para os dados.

