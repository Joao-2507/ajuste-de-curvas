
<div align="center">

# 📈 Ajuste de Curvas e Identificação de Sistemas Dinâmicos

### Projeto de Computação Numérica — UFRN

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

</div>

---

## 📖 Sobre o projeto

Este projeto foi desenvolvido como atividade acadêmica da disciplina de **Computação Numérica**, da Universidade Federal do Rio Grande do Norte (UFRN).

O objetivo é realizar a identificação e o ajuste de dados de um sistema dinâmico não linear, comparando duas abordagens numéricas:

- Filtragem utilizando funções no domínio dos complexos.
- Método dos Mínimos Quadrados (MMQ).

A comparação é realizada utilizando o **Erro Médio Quadrático (EMQ)** e o **Coeficiente de Correlação de Pearson**, além de representações gráficas dos sinais.

---

## 🎯 Objetivos

- Implementar métodos numéricos de ajuste de dados.
- Aplicar filtragem no domínio dos complexos.
- Estimar parâmetros utilizando Mínimos Quadrados.
- Avaliar a qualidade dos ajustes por meio do EMQ.
- Analisar a correlação entre os dados e os valores estimados.
- Comparar os resultados obtidos pelos métodos.

---

## 🧮 Fundamentação matemática

O sistema dinâmico considerado é representado por:

$$
y[n] = f(y[n-1], y[n-2], u[n], u[n-1])
$$

Em que:

- $y[n]$: saída atual do sistema.
- $y[n-1]$ e $y[n-2]$: saídas anteriores.
- $u[n]$ e $u[n-1]$: entradas atual e anterior.

### 1. Filtragem no domínio dos complexos

O primeiro método utiliza uma transformação discreta baseada em exponenciais complexas para representar os sinais no domínio da frequência.

A matriz de transformação é construída a partir de:

$$
W_{m,n} = \frac{1}{\sqrt{N}}e^{-j\frac{2\pi mn}{N}}
$$

Em que:

- $N$: quantidade de amostras.
- $m$ e $n$: índices da transformação.
- $j$: unidade imaginária.

Os sinais são transformados para o domínio da frequência:

$$
X = Wx
$$

$$
Y = Wy
$$

Em seguida, aplica-se uma máscara de filtragem $H$ para selecionar componentes de frequência.

$$
X_f = H \odot X
$$

$$
Y_f = H \odot Y
$$

O símbolo $\odot$ representa a multiplicação elemento a elemento.


Por fim, os sinais são reconstruídos utilizando a transformação inversa:

$$
x_{\text{filtrado}} = \mathrm{Re}(W^H X_f)
$$

$$
y_{\text{filtrado}} = \mathrm{Re}(W^H Y_f)
$$

Em que $W^H$ representa a transposta conjugada da matriz de transformação.


### 2. Método dos Mínimos Quadrados (MMQ)

O segundo método estima os parâmetros de um modelo linear em seus coeficientes, utilizando amostras anteriores das saídas e entradas do sistema.

O modelo pode ser representado por:

$$
Y = \Phi\theta + \varepsilon
$$

Em que:

- $\Phi$: matriz de regressores.
- $\theta$: vetor de parâmetros.
- $Y$: vetor de saídas observadas.
- $\varepsilon$: vetor de erros.

A estimativa dos parâmetros é obtida por:

$$
\hat{\theta} = \Phi^{+}Y
$$

Em que:

- $\Phi^{+}$: pseudoinversa da matriz de regressores.
- $\hat{\theta}$: vetor de parâmetros estimados.

Após a estimação, os valores ajustados são calculados por:

$$
\hat{Y} = \Phi\hat{\theta}
$$

---

## 📊 Métricas de avaliação

### Erro Médio Quadrático (EMQ)

Mede a diferença quadrática média entre os valores observados e os valores estimados.

$$
EMQ = \frac{1}{N}\sum_{i=1}^{N}(y_i-\hat{y}_i)^2
$$

Em que:

- $N$: número de amostras.
- $y_i$: valor observado.
- $\hat{y}_i$: valor estimado.

Valores menores indicam menor erro de ajuste.

### Coeficiente de Correlação de Pearson

Avalia a intensidade da relação linear entre os dados observados e os valores ajustados.

$$
r = \frac{\sum_{i=1}^{N}(y_i-\bar{y})(\hat{y}_i-\bar{\hat{y}})}{\sqrt{\sum_{i=1}^{N}(y_i-\bar{y})^2}\sqrt{\sum_{i=1}^{N}(\hat{y}_i-\bar{\hat{y}})^2}}
$$

Em que:

- $y_i$: valor observado.
- $\hat{y}_i$: valor estimado.
- $\bar{y}$: média dos valores observados.
- $\bar{\hat{y}}$: média dos valores estimados.

O coeficiente varia entre -1 e 1, sendo valores próximos de 1 indicativos de forte correlação linear positiva.

---

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

---

## 🛠️ Tecnologias utilizadas

- **Python:** implementação dos métodos numéricos.
- **NumPy:** operações matriciais e cálculos numéricos.
- **SciPy:** regressão linear e análise estatística.
- **Matplotlib:** geração de gráficos.
- **Jupyter Notebook:** desenvolvimento e documentação da solução.

---

## 📂 Estrutura do projeto

```text
ajuste-de-curvas-python/
│
├── README.md
├── Projeto_02_U2_resposta.ipynb
├── dados.txt
└── requirements.txt
```

---

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

---

## 📌 Conclusão

O projeto permitiu aplicar técnicas de computação numérica para identificação e ajuste de sinais de um sistema dinâmico.

Na comparação realizada, a filtragem no domínio dos complexos apresentou melhores resultados nas métricas de erro e correlação utilizadas.

O estudo evidencia a importância da escolha do método numérico e da avaliação quantitativa dos resultados na modelagem de sistemas dinâmicos.

---

## 👨‍💻 Autor

**João Victor Salústio**

Estudante de Engenharia da Computação — UFRN

[GitHub](https://github.com/Joao-2507) | [Currículo Lattes](http://lattes.cnpq.br/7048388853999078)
