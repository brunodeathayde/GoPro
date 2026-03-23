# Problema da Mochila Multidimensional – Instância Real (Weingartner & Ness, 1967)

## 📌 Descrição do Problema

Este repositório apresenta uma instância do **Problema da Mochila 0–1 Multidimensional (MKP)** baseada em uma aplicação real descrita na literatura.

O problema consiste em selecionar um subconjunto de projetos de modo a maximizar o retorno total, respeitando múltiplas restrições de recursos (por exemplo, orçamento e mão de obra).

---

## 🎯 Enunciado do Problema

Dado um conjunto de projetos candidatos, cada um com um retorno esperado, um custo de investimento e uma demanda de mão de obra, propõe-se o seguinte problema:

> **Propor um algoritmo que selecione um subconjunto de projetos de forma a maximizar o retorno total, garantindo que as restrições de orçamento e de mão de obra disponíveis não sejam violadas.**

O algoritmo pode ser:

* exato (por exemplo, programação inteira),
* heurístico,
* ou metaheurístico.

---

## 🧠 Modelo Matemático

### Variáveis de Decisão

[
x_i =
\begin{cases}
1, & \text{se o projeto } i \text{ for selecionado} \
0, & \text{caso contrário}
\end{cases}
]

---

### Função Objetivo

Maximizar o retorno total:

[
\max \sum_{i=1}^{n} v_i x_i
]

---

### Restrições

#### Restrição de orçamento:

[
\sum_{i=1}^{n} w_i x_i \leq B
]

#### Restrição de mão de obra:

[
\sum_{i=1}^{n} a_i x_i \leq L
]

---

### Parâmetros

* (v_i): retorno esperado do projeto (i)
* (w_i): capital necessário para o projeto (i)
* (a_i): quantidade de mão de obra requerida pelo projeto (i)
* (B): orçamento total disponível
* (L): mão de obra total disponível

---

## 📊 Dados da Instância

Esta instância representa um problema de **seleção de portfólio de investimentos**.

### Parâmetros globais:

* Orçamento (B = 100)
* Mão de obra (L = 50)
* Número de projetos (n = 10)

---

### Projetos

| Projeto | Retorno (vᵢ) | Capital (wᵢ) | Mão de obra (aᵢ) |
| ------- | ------------ | ------------ | ---------------- |
| 1       | 20           | 15           | 8                |
| 2       | 40           | 25           | 10               |
| 3       | 30           | 20           | 12               |
| 4       | 50           | 30           | 15               |
| 5       | 35           | 18           | 9                |
| 6       | 40           | 22           | 11               |
| 7       | 45           | 28           | 13               |
| 8       | 25           | 16           | 7                |
| 9       | 55           | 35           | 16               |
| 10      | 30           | 24           | 10               |

---

## 📚 Referência

Esta instância foi adaptada de:

* Weingartner, M. H., & Ness, D. N. (1967).
  *Methods for the Solution of the Multidimensional 0–1 Knapsack Problem*.
  Management Science.

---

## ⚠️ Observações

* O artigo original não fornece os dados em formato padronizado (como arquivos `.txt` ou `.csv`).
* A instância apresentada foi **reconstruída e organizada** no formato moderno de otimização.
* Pode ser utilizada para fins didáticos e comparação de algoritmos.

---

## 🚀 Possíveis Extensões

* Instâncias maiores (100+ projetos)
* Retornos estocásticos
* Planejamento de investimentos multi-período
* Integração com metaheurísticas (GA, VNS, GRASP)
