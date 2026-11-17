# 📈 Ajuste de Curvas e Identificação de Sistemas Dinâmicos

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

## 📖 Sobre o projeto

Este projeto foi desenvolvido como atividade acadêmica da disciplina de **Computação Numérica**, da Universidade Federal do Rio Grande do Norte (UFRN).

O objetivo é realizar a identificação e o ajuste de dados de um sistema dinâmico não linear, comparando duas abordagens numéricas:

- Filtragem utilizando funções no domínio dos complexos.
- Método dos Mínimos Quadrados (MMQ).

A comparação é realizada utilizando o **Erro Médio Quadrático (EMQ)** e o **Coeficiente de Correlação de Pearson**, além de representações gráficas dos sinais.

## 🎯 Objetivos

- Implementar métodos numéricos de ajuste de dados.
- Aplicar filtragem no domínio dos complexos.
- Estimar parâmetros utilizando Mínimos Quadrados.
- Avaliar a qualidade dos ajustes por meio do EMQ.
- Analisar a correlação entre os dados e os valores estimados.
- Comparar os resultados obtidos pelos métodos.

## 🧮 Fundamentação matemática

O sistema dinâmico considerado é representado por:

\[
y[n] = f(y[n-1], y[n-2], u[n], u[n-1])
\]

Em que:

- \(y[n]\): saída atual do sistema.
- \(y[n-1]\) e \(y[n-2]\): saídas anteriores.
- \(u[n]\) e \(u[n-1]\): entradas atual e anterior.

### 1. Filtragem no domínio dos complexos

O primeiro método utiliza uma transformação discreta baseada em exponenciais complexas para representar os sinais no domínio da frequência.

A partir dessa representação, aplica-se uma máscara de filtragem para selecionar componentes de frequência e reconstruir os sinais por meio da transformação inversa.

### 2. Método dos Mínimos Quadrados (MMQ)

O segundo método estima os parâmetros de um modelo linear em seus coeficientes, utilizando amostras anteriores das saídas e entradas do sistema.

A estimativa dos parâmetros é obtida por:

\[
\hat{\theta} = \Phi^{+}Y
\]

Em que:

- \(\Phi\): matriz de regressores.
- \(\Phi^{+}\): pseudoinversa da matriz de regressores.
- \(Y\): vetor de saídas observadas.
- \(\hat{\theta}\): vetor de parâmetros estimados.

## 📊 Métricas de avaliação

### Erro Médio Quadrático (EMQ)

Mede a diferença quadrática média entre os valores observados e os valores estimados.

\[
EMQ = \frac{1}{N}\sum_{i=1}^{N}(y_i-\hat{y}_i)^2
\]

Valores menores indicam menor erro de ajuste.

### Coeficiente de Correlação de Pearson

Avalia a intensidade da relação linear entre os dados observados e os valores ajustados.

O coeficiente varia entre -1 e 1, sendo valores próximos de 1 indicativos de forte correlação linear positiva.

## 📈 Resultados

Os resultados registrados na conclusão do notebook foram:

| Método | EMQ (x) | EMQ (y) | Pearson (x) | Pearson (y) |
|---|---:|---:|---:|---:|
| Filtro complexo | 0,0099 | 0,0105 | 0,7242 | 0,9403 |
| MMQ | 0,0131 | 0,0155 | 0,6088 | 0,9106 |

### Análise dos resultados

Os valores registrados indicam que a filtragem no domínio dos complexos apresentou menores erros médios quadráticos para ambos os sinais analisados.

Além disso, os coeficientes de correlação de Pearson foram superiores aos obtidos pelo Método dos Mínimos Quadrados.

Esses resultados sugerem que, para os dados analisados e as configurações utilizadas, o filtro complexo apresentou melhor desempenho segundo as métricas adotadas.

## 🛠️ Tecnologias utilizadas

- **Python:** implementação dos métodos numéricos.
- **NumPy:** operações matriciais e cálculos numéricos.
- **SciPy:** regressão linear e análise estatística.
- **Matplotlib:** geração de gráficos.
- **Jupyter Notebook:** desenvolvimento e documentação da solução.

## 🚀 Como executar

1. Clone ou baixe este repositório.
2. Instale Python e Jupyter Notebook.
3. Instale as bibliotecas necessárias:

```bash
pip install numpy scipy matplotlib notebook
```

4. Mantenha o arquivo `dados.txt` no mesmo diretório do notebook.
5. Abra o notebook:

```bash
jupyter notebook Projeto_02_U2_resposta.ipynb
```

6. Execute as células sequencialmente para reproduzir os cálculos e gráficos.

## 📌 Conclusão

O projeto permitiu aplicar técnicas de computação numérica para identificação e ajuste de sinais de um sistema dinâmico.

Na comparação realizada, a filtragem no domínio dos complexos apresentou melhores resultados nas métricas de erro e correlação utilizadas.

O estudo evidencia a importância da escolha do método numérico e da avaliação quantitativa dos resultados na modelagem de sistemas dinâmicos.

## 👨‍💻 Autor

**João Victor Salústio**

Estudante de Engenharia da Computação — UFRN

[GitHub](https://github.com/Joao-2507) | [Currículo Lattes](http://lattes.cnpq.br/7048388853999078)
