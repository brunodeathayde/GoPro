# ♻️ Problema de Localização de Facilidades Capacitado (SSCFLP) – Localização de Ecopontos em Fortaleza

## 📌 Descrição do Problema

Este repositório apresenta uma instância de grande porte do **Problema de Localização de Facilidades Capacitado com Atendimento Único (Single-Source Capacitated Facility Location Problem – SSCFLP)** aplicada à otimização da rede de **Ecopontos urbanos** (pontos de entrega voluntária de resíduos recicláveis, volumosos e eletroeletrônicos).

O objetivo principal é determinar quais locais candidatos devem ser ativados como Ecopontos e como alocar a demanda de descartes de cada bairro/região da cidade a um único Ecoponto, minimizando a soma dos custos fixos de instalação e dos custos de transporte/atendimento, respeitando estritamente a capacidade máxima de cada unidade.

---

## 🎯 Enunciado do Problema

Desenvolver e analisar métodos de resolução (algoritmos exatos via solver MILP, heurísticas de construção ou metaheurísticas) para resolver o **Ecoponto Facility Location Problem (EFLP)**, otimizando a infraestrutura de logística reversa e coleta seletiva urbana sob restrições operacionais, geográficas e de capacidade.

---


## 🌍 Dados da Instância de Grande Porte

A instância completa contendo **100 bairros e 100 Ecopontos candidatos** ($10.100$ variáveis binárias e $10.200$ restrições) encontra-se disponível na planilha **`Instancia_Ecopontos_Grande_Porte.xlsx`**.

### Amostra dos Dados dos Bairros e Candidatos

| ID Bairro | Nome do Bairro | Coordenada X | Coordenada Y | Demanda (ton/mês) | Custo Fixo (R$) | Capacidade (ton/mês) |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| 1 | Centro | -38,5267 | -3,7275 | 28 | R$ 60.200,00 | 308 |
| 2 | Aldeota | -38,5020 | -3,7348 | 44 | R$ 90.600,00 | 322 |
| 3 | Meireles | -38,4942 | -3,7265 | 87 | R$ 75.600,00 | 211 |
| 4 | Mucuripe | -38,4770 | -3,7210 | 107 | R$ 126.200,00 | 301 |
| 5 | Varjota | -38,4875 | -3,7330 | 99 | R$ 119.500,00 | 436 |
| ... | ... | ... | ... | ... | ... | ... |
| **Total** | **100 Bairros** | — | — | **6.714 ton** | **R$ 9.303.100,00** | **32.297 ton** |

### Amostra da Matriz de Custos de Atendimento 

| Ecoponto ($i$) \ Bairro ($j$) | B_001 | B_002 | B_003 | B_004 | B_005 | ... | B_100 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Eco_Centro** | **R$ 0,00** | R$ 1.572,97 | R$ 3.927,82 | R$ 7.446,21 | R$ 5.440,79 | ... | R$ 8.854,93 |
| **Eco_Aldeota** | R$ 1.000,98 | **R$ 0,00** | R$ 1.372,54 | R$ 4.238,00 | R$ 2.008,35 | ... | R$ 10.390,49 |
| **Eco_Meireles** | R$ 1.264,13 | R$ 694,16 | **R$ 0,00** | R$ 2.681,72 | R$ 1.280,33 | ... | R$ 11.592,19 |
| **Eco_Mucuripe** | R$ 1.948,54 | R$ 1.742,73 | R$ 2.180,47 | **R$ 0,00** | R$ 2.186,16 | ... | R$ 13.471,81 |
| **Eco_Varjota** | R$ 1.538,81 | R$ 892,60 | R$ 1.125,14 | R$ 2.362,82 | **R$ 0,00** | ... | R$ 11.828,12 |

---

## ⚙️ Métodos de Resolução Otimizados

Devido ao caráter **NP-difícil** e ao atendimento único (*Single-Source*), o problema exige estratégias eficientes de otimização:

- **Programação Linear Inteira Mista (MILP)**:
  - Resolução exata utilizando *solvers* de alto desempenho (IBM ILOG CPLEX, Gurobi, CBC, SCIP, PyPSA/PuLP).
  - Formulação reforçada com cortes válidos (ex: *knapsack covers*) para acelerar a busca na árvore de *Branch-and-Bound*.
- **Metaheurísticas e Algoritmos Aproximados**:
  - **GRASP (Greedy Randomized Adaptive Search Procedure)**
  - **Algoritmos Genéticos (AG)**
  - **Simulated Annealing (SA) / Busca Tabu**
  - **Variable Neighborhood Search (VNS)**

---

## 📚 Referências Bibliográficas

- Diaz, J. A., & Fernández, E. (2002). *A scatter search algorithm for the single source capacitated facility location problem*. Annals of Operations Research, 117(1), 251-262.
- Holmberg, K., Rönnqvist, M., & Yuan, D. (1999). *An exact algorithm for the capacitated facility location problem with single source constraints*. European Journal of Operational Research, 113(3), 544-559.
- Daskin, M. S. (2013). *Network and discrete location: models, algorithms, and applications*. John Wiley & Sons.
- Beasley, J. E. (1990). *OR-Library: distributing test problems in operational research*. Journal of the Operational Research Society, 41(11), 1069-1072.

---

## 🚀 Possíveis Extensões

- **Múltiplos Tipos de Resíduos (Multi-Commodity)**: Capacidades e custos diferenciados para coleta de resíduos secos recicláveis, entulhos de construção e eletrônicos.
- **Planejamento Multiperíodo**: Expansão e abertura gradual dos Ecopontos ao longo de um horizonte de planejamento de 5 a 10 anos.
- **Pegada de Carbono e Impacto Ambiental**: Minimização da emissão de CO₂ dos veículos de transporte dos moradores e da frota pública municipal.
- **Janelas de Atendimento e Horários**: Integração com rotas de caminhões de transbordo e horários de pico de descarte populacional.

---
