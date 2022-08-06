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



