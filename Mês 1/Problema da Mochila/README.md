# 📊 Problema da Mochila Multidimensional – Instância Real (Weingartner & Ness, 1967)

## 📌 Descrição do Problema

Este repositório apresenta uma instância do **Problema da Mochila 0–1 Multidimensional (MKP)** baseada em uma aplicação real descrita na literatura.

O problema consiste em selecionar um subconjunto de projetos de modo a maximizar o retorno total, respeitando múltiplas restrições de recursos (capital e mão de obra).

---

## 🎯 Enunciado do Problema

Selecionar um conjunto de projetos de forma a maximizar o retorno total, respeitando as limitações de recursos disponíveis.

---

## 🧠 Descrição do Problema

O problema consiste em decidir quais projetos devem ser selecionados dentre um conjunto de alternativas disponíveis.

Cada projeto possui:
- um valor de retorno (benefício);  
- um consumo de recursos, como capital e mão de obra.

Os recursos disponíveis são limitados, ou seja:
- existe um orçamento máximo que não pode ser ultrapassado;  
- há uma quantidade limitada de mão de obra disponível.

Cada projeto pode ser:
- selecionado integralmente; ou  
- não selecionado (não é permitido selecionar frações de projetos).

O objetivo é escolher o subconjunto de projetos que:
- maximize o retorno total obtido;  
- sem ultrapassar os limites de capital e de mão de obra disponíveis.

Este problema é conhecido como **Problema da Mochila Multidimensional 0–1**, sendo amplamente utilizado em contextos de seleção de investimentos, portfólio de projetos e alocação de recursos escassos.

## 📊 Dados da Instância

### Parâmetros globais:
- **Capital disponível (B) = 500**
- **Mão de obra disponível (L) = 600**
- **Número de projetos (n = 28)**

### Projetos

| Projeto | Retorno (vᵢ) | Capital (wᵢ) | Mão de obra (aᵢ) |
| ------- | ------------ | ------------- | ---------------- |
| 1       | 1898         | 45            | 30               |
| 2       | 440          | 0             | 20               |
| 3       | 22507        | 85            | 125              |
| 4       | 270          | 150           | 5                |
| 5       | 14148        | 65            | 80               |
| 6       | 3100         | 95            | 25               |
| 7       | 4650         | 30            | 35               |
| 8       | 30800        | 0             | 73               |
| 9       | 615          | 170           | 12               |
| 10      | 4975         | 0             | 15               |
| 11      | 4225         | 25            | 40               |
| 12      | 510          | 0             | 5                |
| 13      | 11880        | 0             | 10               |
| 14      | 479          | 0             | 10               |
| 15      | 440          | 25            | 12               |
| 16      | 490          | 0             | 9                |
| 17      | 330          | 0             | 5                |
| 18      | 290          | 0             | 5                |
| 19      | 560          | 0             | 5                |
| 20      | 24355        | 165           | 25               |
| 21      | 2885         | 0             | 40               |
| 22      | 11748        | 85            | 55               |
| 23      | 4550         | 0             | 35               |
| 24      | 750          | 0             | 5                |
| 25      | 970          | 0             | 10               |
| 26      | 1950         | 0             | 20               |
| 27      | 10500        | 100           | 150              |
| 28      | 10500        | 100           | 150              |

---

## 📚 Referência

* Weingartner, M. H., & Ness, D. N. (1967).  
  *Methods for the Solution of the Multidimensional 0–1 Knapsack Problem*.  
  Management Science.

---

## 🎥 Vídeo explicativo

[![Assista ao vídeo no YouTube](https://img.youtube.com/vi/76B8lVqQPFM/maxresdefault.jpg)](https://youtu.be/76B8lVqQPFM?si=af_JMaD37vRSFyKL)

> *Vídeo apresentando o problema da mochila.*

---

## 🚀 Possíveis Extensões

* Instâncias maiores (100+ projetos)  
* Retornos estocásticos  
* Planejamento de investimentos multi-período  
* Integração com metaheurísticas (GA, VNS, GRASP)  
