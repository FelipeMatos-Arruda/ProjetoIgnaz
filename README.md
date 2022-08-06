# Dr. Semmelweis e a descoberta da lavagem das mãos

Descrição do Projeto: Em 1847, o médico húngaro Ignaz Semmelweis fez uma descoberta revolucionária: ele descobre a lavagem das mãos. As mãos contaminadas foram uma das principais causas da febre puerperal e, ao impor a lavagem das mãos em seu hospital, ele salvou centenas de vidas.

## Parte 1 - Conhecendo o Dr. Ignaz Semmelweis

![image](https://user-images.githubusercontent.com/84130785/183248102-cad5ffd4-e58f-49ad-8c9d-68efafa8a7e3.png)

Esse é o Dr. Ignaz Semmelweis húngaro nascido em 1818 e ativo no Hospital Geral de Viena. Se o Dr. Semmelweis parece preocupado, provavelmente é porque está pensando em febre puerperal: uma doença mortal que afeta mulheres que acabaram de dar à luz. Ele está pensando nisso porque, no início da década de 1840, no Hospital Geral de Viena, cerca de 10% das mulheres que dão à luz morriam por causa disso. Ele está pensando nisso porque conhece a causa da febre puerperal: são as mãos contaminadas dos médicos que fazem o parto. E eles não vão ouvi-lo e lavar as mãos!

Neste caderno, vamos reanalisar os dados que fizeram Semmelweis descobrir a importância de lavar as mãos. Vamos começar analisando os dados que fizeram Semmelweis perceber que algo estava errado com os procedimentos do Hospital Geral de Viena.

```
# Importando módulos
import pandas as pd

# Ler o dataset yearly_deaths_by_clinic
yearly = pd.read_csv("/yearly_deaths_by_clinic.csv")

# Printe o Dataset
print(yearly)
```
![image](https://user-images.githubusercontent.com/84130785/183248139-04185312-cf55-4208-aac3-41c00818e9e8.png)

## PARTE 2 - O alarmante número de mortes.

A tabela acima mostra o número de mulheres que deram à luz nas duas clínicas do Hospital Geral de Viena nos anos de 1841 a 1846. Você notará que dar à luz era muito perigoso; um número alarmante de mulheres morreu como resultado do parto, a maioria delas de febre puerperal.

Veremos isso mais claramente se observarmos a proporção de mortes em relação ao número de mulheres que dão à luz. Vamos ampliar a proporção de mortes na Clínica 1.

```
# Calcular a proporção de óbitos por nascimentos.
yearly["proportion_deaths"] = yearly["deaths"]/yearly["births"]

#Extraia os dados da Clínica 1 na variável clinic 1 e os dados da Clínica 2 na variável clinic 2
clinic_1 = yearly[yearly["clinic"] == "clinic 1"]
clinic_2 = yearly[yearly["clinic"] == "clinic 2"]

# Printe os dados de clinic 1
print(clinic_1)
```
![image](https://user-images.githubusercontent.com/84130785/183248191-894585ae-a21b-49ff-98bb-58d5413e498c.png)

## Parte 3 - Morte nas clínicas

Se agora traçarmos a proporção de mortes na Clínica 1 e na Clínica 2, veremos um padrão curioso...

```
# Importar matplotlib.
import matplotlib.pyplot as plt

# Isso faz com que os gráficos apareçam no notebook.
%matplotlib inline

# Um gráfico com a proporção anual de mortes nas duas clínicas.
ax = clinic_1.plot(x = "year", y = "proportion_deaths", label = "Clinic 1", xlabel = "Ano", ylabel = "Proporções de mortes")
clinic_2.plot(x = "year", y = "proportion_deaths", label = "Clinic 2", ax = ax, xlabel = "Ano", ylabel = "Proporções de mortes")

```
![image](https://user-images.githubusercontent.com/84130785/183248238-20994ef8-c0a2-4856-9635-a4b92ea70910.png)

## Parte 4 - A lavagem das mãos começa

Por que a proporção de mortes é consistentemente muito maior na Clínica 1? Semmelweis viu o mesmo padrão e ficou intrigado e angustiado. A única diferença entre as clínicas era que muitos estudantes de medicina serviam na Clínica 1, enquanto a maioria dos estudantes de obstetrícia servia na Clínica 2. Enquanto as parteiras só cuidavam das mulheres que davam à luz, os estudantes de medicina também passavam um tempo nas salas de autópsia examinando cadáveres.

Semmelweis começou a suspeitar que algo nos cadáveres, espalhado pelas mãos dos estudantes de medicina, causava febre puerperal. Então, em uma tentativa desesperada de parar as altas taxas de mortalidade, ele decretou: Lave as mãos! Este foi um pedido heterodoxo e controverso, ninguém em Viena sabia sobre bactérias neste momento.

. A lavagem das mãos começa Por que a proporção de mortes é consistentemente muito maior na Clínica 1? Semmelweis viu o mesmo padrão e ficou intrigado e angustiado. A única diferença entre as clínicas era que muitos estudantes de medicina serviam na Clínica 1, enquanto a maioria dos estudantes de obstetrícia servia na Clínica 2. Enquanto as parteiras só cuidavam das mulheres que davam à luz, os estudantes de medicina também passavam um tempo nas salas de autópsia examinando cadáveres.

Semmelweis começou a suspeitar que algo nos cadáveres, espalhado pelas mãos dos estudantes de medicina, causava febre puerperal. Então, em uma tentativa desesperada de parar as altas taxas de mortalidade, ele decretou: Lave as mãos! Este foi um pedido heterodoxo e controverso, ninguém em Viena sabia sobre bactérias neste momento.

Vamos carregar os dados mensais da Clínica 1 para ver se a lavagem das mãos teve algum efeito.

```
# Ler o Dataset monsthly_deaths.
monthly = pd.read_csv("/monthly_deaths.csv")

# Calcular a proporção de óbitos por n° de nascimentos.
monthly["proportion_deaths"] = monthly["deaths"]/monthly["births"]

#Imprimir as primeiras linhas.
print(monthly)

```
![image](https://user-images.githubusercontent.com/84130785/183248267-5c6680f7-3c85-429c-be9b-f3f893596693.png)

## Parte 5 - O resultado de lavar as mãos

Com os dados carregados, agora podemos ver a proporção de mortes ao longo do tempo. No gráfico abaixo, não marcamos onde a lavagem obrigatória das mãos começou, mas reduziu a proporção de mortes a tal ponto que você deve ser capaz de identificá-la!

```
# Carregue um gráfico para proporção mensal de mortes
%matplotlib inline

ax = monthly.plot(x = "date", y = "proportion_deaths", xlabel = "Proporção de mortes", ylabel = "Data")
```
![image](https://user-images.githubusercontent.com/84130785/183248292-cc806d87-c5b4-4ae5-978f-368e3f4781d1.png)

## Parte 6 - O efeito de lavar as mãos

A partir do verão de 1847 a proporção de mortes é drasticamente reduzida e, sim, foi quando Semmelweis tornou obrigatória a lavagem das mãos.

O efeito da lavagem das mãos fica ainda mais claro se destacarmos isso no gráfico.

```
# Data em que foi declarada obrigatória a lavagem de mãos
handwashing_start = pd.to_datetime('1847-06-01')

# Divida as informações do Dataset antes e depois do início da lavagem das mãos.
before_washing = monthly[monthly["date"] < '1847-06-01']
after_washing = monthly[monthly["date"] >= '1847-06-01']

# Plotar um gráfico que mostra a proporção de mortes antes e depois da lavagem das mãos
ax = before_washing.plot(x="date", y="proportion_deaths", label="Before handwashing", scalex = True)
after_washing.plot(x="date", y="proportion_deaths",label="After handwashing", ax=ax, ylabel="Proportion deaths",scaley = bool)
plt.xticks(rotation = 50)
```
![image](https://user-images.githubusercontent.com/84130785/183248310-1f2bcfaf-1367-445b-af26-dee399b93ac8.png)

## Parte 7 - Mais mãos limpas, menos mortes ?

Mais uma vez, o gráfico mostra que a lavagem das mãos teve um efeito enorme. Quanto reduziu a proporção mensal de mortes em média?

```
# Diferença na proporção média mensal de morte por lavagem das mãos
before_proportion = before_washing["proportion_deaths"]
after_proportion = after_washing["proportion_deaths"]
mean_diff =after_proportion.mean() - before_proportion.mean()
mean_diff
```

![image](https://user-images.githubusercontent.com/84130785/183248335-ddeedc5b-7e78-4158-be52-a78044d80ff9.png)


## Parte 8 - Uma análise Bootstrap dos dados de lavagem das mãos de Semmelweis

Reduziu a proporção de mortes em cerca de 8 pontos percentuais! De 10% em média para apenas 2% (o que ainda é um número alto para os padrões modernos).

Para ter uma ideia da incerteza sobre o quanto a lavagem das mãos reduz a mortalidade, podemos olhar para um intervalo de confiança (aqui calculado usando o método bootstrap).

```
# Uma análise inicial da redução de mortes devido à lavagem das mãos
boot_mean_diff = []
```

```
for i in range(3000):
  boot_before = before_proportion.sample(frac=1, replace = True)
  boot_after = after_proportion.sample(frac =1, replace = True)
  boot_mean_diff.append(boot_after.mean() - boot_before.mean())

# Calculando um intervalo de confiança de 95% de boot_mean_diff
confidende_interval = pd.Series(boot_mean_diff).quantile([0.25, 0.975])
confidende_interval
```
![image](https://user-images.githubusercontent.com/84130785/183248354-6c86aea2-62ec-49b8-b1da-f311ce757465.png)

## Parte 9 - O destino do Dr. Semmelweis

Assim, a lavagem das mãos reduziu a proporção de mortes entre 6,7 e 10 pontos percentuais, de acordo com um intervalo de confiança de 95%. Ao todo, parece que Semmelweis tinha evidências sólidas de que lavar as mãos era um procedimento simples, mas altamente eficaz, que poderia salvar muitas vidas.

A tragédia é que, apesar das evidências, a teoria de Semmelweis - que a febre puerperal era causada por alguma "substância" (o que hoje conhecemos como bactérias) de cadáveres de salas de autópsia - foi ridicularizada por cientistas contemporâneos. A comunidade médica rejeitou amplamente sua descoberta e em 1849 ele foi forçado a deixar o Hospital Geral de Viena para sempre.

Uma razão para isso foi que estatísticas e argumentos estatísticos eram incomuns na ciência médica em 1800. Semmelweis publicou seus dados apenas como longas tabelas de dados brutos, mas não mostrou gráficos nem intervalos de confiança. Se ele tivesse acesso à análise que acabamos de fazer, poderia ter tido mais sucesso em fazer com que os médicos vienenses lavassem as mãos.

```
# Os dados coletador por Semmelweis apontam que:
doctors_should_wash_their_hands = True

```
