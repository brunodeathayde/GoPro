# 📊 Problema de Corte Unidimensional – Instância Real (Vigas Pré-Moldadas)

## 📌 Descrição do Problema

Este repositório apresenta uma instância do **Problema de Corte Unidimensional (Cutting Stock Problem – CSP)** baseada em um cenário real de produção de **vigas pré-moldadas**.

O problema consiste em determinar como cortar fôrmas (barras) de comprimento fixo em peças menores, de modo a atender à demanda de diferentes tipos de vigas, **minimizando o desperdício de material** ou o número total de fôrmas utilizadas.

---

## 🎯 Enunciado do Problema

Determinar um plano de corte que atenda à demanda de todos os tipos de vigas pré-moldadas, respeitando a capacidade das fôrmas disponíveis, de modo a minimizar o número de fôrmas utilizadas ou o desperdício total de material.

---

## 🧠 Descrição do Problema

O problema consiste em planejar o corte de fôrmas (barras) de comprimento fixo em peças menores (vigas pré-moldadas) de diferentes tamanhos.

Cada tipo de viga possui:
- um comprimento específico;  
- uma demanda que deve ser totalmente atendida.

As fôrmas possuem capacidade limitada, ou seja, a soma dos comprimentos das vigas cortadas a partir de uma mesma fôrma não pode exceder seu comprimento total.

Para isso, podem ser utilizados diferentes **padrões de corte**, onde cada padrão define quantas peças de cada tipo são produzidas a partir de uma única fôrma.

O objetivo é determinar:
- quais padrões de corte devem ser utilizados;  
- e quantas vezes cada padrão será aplicado;  

de forma que:
- toda a demanda de vigas seja atendida;  
- nenhuma fôrma tenha sua capacidade excedida;  
- e o número total de fôrmas utilizadas (ou o desperdício de material) seja minimizado.

Este problema é característico do **Problema de Corte Unidimensional**, sendo amplamente aplicado em contextos industriais como corte de aço, madeira, papel e concreto pré-moldado.

## 📊 Dados da Instância

### Tipos de vigas

| Tipo | Tamanho (m) | Demanda |
|------|------------|---------|
| 1    | 1,22       | 24      |
| 2    | 1,45       | 60      |
| 3    | 2,35       | 56      |
| 4    | 2,50       | 72      |
| 5    | 2,65       | 16      |
| 6    | 2,95       | 17      |
| 7    | 3,30       | 12      |

---

### Capacidade das fôrmas

| Tipo de fôrma | Capacidade (m) |
|--------------|---------------|
| 1            | 11,95         |
| 2            | 11,95         |
| 3            | 11,95         |
| 4            | 11,95         |
| 5            | 11,95         |
| 6            | 11,95         |
| 7            | 5,95          |

---

## 📚 Referência

- Prata, B. A., Pitombeira-Neto, A. R., & de Moraes Sales, C. J. (2015).  
  *An integer linear programming model for the multiperiod production planning of precast concrete beams*.  
  Journal of Construction Engineering and Management, 141(10), 04015029.

---

## 🎥 Vídeo explicativo

[![Assista ao vídeo no YouTube](https://img.youtube.com/vi/pKAilLHk7qQ/maxresdefault.jpg)](https://youtu.be/pKAilLHk7qQ)

> *Vídeo demonstrando o processo de corte e otimização das fôrmas.*

---

## 🚀 Possíveis Extensões

- Minimização explícita do desperdício (loss minimization)  
- Múltiplos tipos de fôrmas (heterogeneous cutting stock)  
- Problema multiperíodo  
- Integração com planejamento da produção  
- Métodos de solução:
  - Geração de colunas  
  - GRASP  
  - Algoritmos Genéticos  
  - VNS  
