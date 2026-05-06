# Problema de Corte Bidimensional Guilhotinado – Instância Real (Rochas Ornamentais)

📌 **Descrição do Problema**

Este repositório apresenta uma instância do **Problema de Corte Bidimensional Guilhotinado (2D-CSP)** baseada em um cenário real de produção de chapas de granito em uma empresa de rochas ornamentais.

O problema consiste em determinar como cortar chapas (bins) de dimensões fixas em peças menores, de modo a atender à demanda de diferentes tipos de produtos, minimizando o desperdício de material ou o número total de chapas utilizadas.

---

🎯 **Enunciado do Problema**

Determinar um plano de corte que atenda à demanda de todos os tipos de peças de granito, respeitando as dimensões das chapas disponíveis, de modo a minimizar o número de chapas utilizadas ou o desperdício total de material.

---

🧠 **Descrição do Problema**

O problema consiste em planejar o corte de chapas de granito (bins) de tamanho fixo em peças menores de diferentes dimensões.

Cada tipo de peça possui:

- uma largura e altura específicas;
- uma demanda que deve ser totalmente atendida.

As chapas possuem dimensões limitadas, ou seja, a soma das peças cortadas a partir de uma mesma chapa não pode exceder suas dimensões totais.

Para isso, podem ser utilizados diferentes padrões de corte guilhotinado, onde cada padrão define quantas peças de cada tipo são produzidas a partir de uma única chapa.

O objetivo é determinar:

- quais padrões de corte devem ser utilizados;
- e quantas vezes cada padrão será aplicado;

de forma que:

- toda a demanda de peças seja atendida;
- nenhuma chapa tenha sua capacidade excedida;
- e o número total de chapas utilizadas (ou o desperdício de material) seja minimizado.

Este problema é característico do **Problema de Corte Bidimensional Guilhotinado**, sendo amplamente aplicado em contextos industriais como corte de vidro, madeira, papel e rochas ornamentais.

---

📊 **Dados da Instância**

### Dimensões das chapas (bins)
- **2,80 m x 1,80 m**

### Tipos de peças demandadas

| Quantidade | Largura (m) | Altura (m) |
|------------|-------------|------------|
| 88         | 0,200       | 1,650      |
| 8          | 0,200       | 1,650      |
| 2          | 0,050       | 1,175      |
| 2          | 0,050       | 1,000      |

---

📚 **Referência**

- Pessoa, R. L. (2018). Contributions to the two-dimensional guillotine cutting stock problem.  
Dissertação de Mestrado, Universidade Federal do Ceará.

---

🚀 **Possíveis Extensões**

- Minimização explícita do desperdício (loss minimization)  
- Múltiplos tipos de chapas (heterogeneous cutting stock)  
- Problema multiperíodo  
- Integração com planejamento da produção  
- Métodos de solução:  
  - Geração de colunas  
  - GRASP  
  - Algoritmos Genéticos  
  - VNS  

