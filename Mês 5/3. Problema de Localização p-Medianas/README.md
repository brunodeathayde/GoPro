# 📦 Problema das p-Medianas – Localização de Centros de Distribuição

## 📌 Descrição do Problema

Este repositório apresenta uma instância de médio/grande porte do **Problema das p-Medianas (p-Median Problem)** aplicada à otimização de uma rede logística de **Centros de Distribuição (CDs)**. 

O objetivo principal é determinar a localização exata de $p$ instalações (Centros de Distribuição) a partir de um conjunto de locais candidatos, de modo a alocar a demanda de diferentes regiões clientes minimizando a soma das distâncias ponderadas (ou custo total de frete) da malha de atendimento. 

Neste contexto real de *Supply Chain*, a diretoria definiu um budget restrito que fixa o número de CDs a serem abertos (ex: $p = 5$). Entretanto, **o modelo e os métodos de solução propostos devem ser flexíveis**, permitindo que os analistas realizem simulações de cenários variando o parâmetro $p$ (ex: de 3 a 10) para encontrar o *trade-off* ideal entre nível de serviço (proximidade ao cliente) e custo de instalações.

---

## 🎯 Enunciado do Problema

Desenvolver e analisar métodos de resolução (algoritmos exatos via solver MILP, heurísticas de construção, troca ou metaheurísticas) para resolver o **Problema de Localização p-Medianas**. O modelo deve definir quais $p$ polos logísticos serão ativados e determinar o mapeamento (alocação) de todas as regiões clientes para o CD mais próximo, garantindo o menor custo total de transporte de suprimentos.

---

## 🌍 Dados da Instância

A instância completa contém uma matriz de **75 regiões clientes/candidatas** e encontra-se disponível na planilha **`Instancia_CDs_pMedianas.xlsx`**.

### Amostra dos Dados dos Clientes/Candidatos

| ID Cliente/Candidato | Nome da Região | Latitude (Y) | Longitude (X) | Demanda (Paletes/mês) |
| :---: | :--- | :---: | :---: | :---: |
| CLI_001 | Região São Paulo-1 | -23,5505 | -46,6333 | 1.360 |
| CLI_002 | Região Campinas-2 | -22,9099 | -47,0626 | 1.794 |
| CLI_003 | Região Guarulhos-3 | -23,4628 | -46,5333 | 1.630 |
| CLI_004 | Região Osasco-4 | -23,5329 | -46,7917 | 1.595 |
| CLI_005 | Região Ribeirão Preto-5 | -21,1704 | -47,8103 | 2.138 |
| ... | ... | ... | ... | ... |
| **Total** | **75 Regiões** | — | — | **~135.517 Paletes** |

### Amostra da Matriz de Distâncias (km)

| Origem \ Destino | CLI_001 | CLI_002 | CLI_003 | CLI_004 | CLI_005 | ... | CLI_075 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **CLI_001** | **0,00** | 83,65 | 14,11 | 16,27 | 291,01 | ... | 67,58 |
| **CLI_002** | 83,65 | **0,00** | 81,89 | 74,60 | 208,21 | ... | 16,09 |
| **CLI_003** | 14,11 | 81,89 | **0,00** | 27,48 | 286,75 | ... | 65,96 |
| **CLI_004** | 16,27 | 74,60 | 27,48 | **0,00** | 282,81 | ... | 58,98 |
| **CLI_005** | 291,01 | 208,21 | 286,75 | 282,81 | **0,00** | ... | 223,96 |

---

## ⚙️ Métodos de Resolução Otimizados

Dado que o problema das p-Medianas é classificado como **NP-difícil**, instâncias de médio e grande porte exigem abordagens avançadas:

- **Programação Linear Inteira Mista (MILP)**:
  - Formulação clássica em grafos bipartite, viável para instâncias médias através de *solvers* de mercado (Gurobi, CPLEX, CBC, SCIP).
- **Heurísticas Clássicas**:
  - **Algoritmo de Teitz e Bart (1968)**: Heurística de busca local baseada na troca iterativa entre vértices medianos e não-medianos (1-opt).
  - **Heurística Gulosa de Construção**: Adição iterativa da mediana que promove a maior redução no custo total.
- **Metaheurísticas**:
  - **Variable Neighborhood Search (VNS)** e **ALNS (Adaptive Large Neighborhood Search)**.
  - **Algoritmos Genéticos (AG)** focados na codificação dos subconjuntos de $p$ elementos.

---

## 📚 Referências Bibliográficas

- Hakimi, S. L. (1964). *Optimum locations of switching centers and the absolute centers and medians of a graph*. Operations Research, 12(3), 450-459.
- Kariv, O., & Hakimi, S. L. (1979). *An algorithmic approach to network location problems. II: The p-medians*. SIAM Journal on Applied Mathematics, 37(3), 539-560.
- Mladenović, N., Brimberg, J., Hansen, P., & Moreno-Pérez, J. A. (2007). *The p-median problem: A survey of metaheuristic approaches*. European Journal of Operational Research, 179(3), 927-939.
- Daskin, M. S. (2013). *Network and discrete location: models, algorithms, and applications*. John Wiley & Sons.

---

## 🚀 Possíveis Extensões

- **p-Medianas Capacitado (CPMP)**: Inserção de limites operacionais máximos (paletes/mês) que cada Centro de Distribuição pode processar.
- **Análise Multi-Cenário (Sweep de p)**: Automatização da execução do algoritmo para gerar a Curva de Pareto entre $p$ (Investimento Fixo) vs Custo de Roteamento.
- **Multi-Período**: Planejamento do *ramp-up* da rede definindo a abertura sequencial dos CDs ao longo de 5 anos.
- **Demanda Estocástica**: Considerar incertezas sazonais na demanda dos clientes.

---

## 🎥 Vídeo Explicativo e Simulação

[![Vídeo demonstrando o Problema de p-Medianas aplicado à gestão de Malha Logística.](Link do Vídeo no Youtube)](#)
