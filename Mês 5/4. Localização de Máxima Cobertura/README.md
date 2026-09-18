# ⚡ Problema de Localização de Máxima Cobertura (PLMC) – Instalação de Eletropostos


## 📌 Enunciado do Problema

Desenvolver e analisar métodos de resolução (algoritmos exatos, heurísticas ou metaheurísticas) para resolver o **Problema de Localização de Máxima Cobertura (Maximal Covering Location Problem - MCLP)** aplicado à instalação de estações de recarga (eletropostos) para veículos elétricos. O objetivo é otimizar a distribuição espacial dos pontos de atendimento considerando o orçamento disponível e maximizando a cobertura da frota em circulação, considerando os pesos de cada ponto de demanda.

---

## 🧠 Descrição do Problema

Em vez de focar apenas na cobertura estática de pontos geográficos isolados (como bairros), a alocação de eletropostos para veículos elétricos concentra-se em cobrir fluxos de tráfego (rotas de viagem) ou nós de alta demanda (centros comerciais, shoppings, cruzamentos rodoviários) onde os motoristas passam ou estacionam frequentemente, levando em consideração o alcance limitado das baterias.

O planejamento espacial exige o atendimento às seguintes premissas operacionais:
- **Pontos de Demanda de Recarga:** Representam os locais de atração de tráfego ou concentração de veículos elétricos , contendo pesos correspondentes à demanda estimada ou ao fluxo diário.
- **Locais Candidatos:** Representam os locais disponíveis e viáveis para a instalação física dos eletropostos.
- **Raio de Cobertura:** Distância ou tempo máximo aceitável que um usuário está disposto a desviar de sua rota ou deslocar-se para recarregar o veículo.
- **Orçamento de Instalação ($p$):** Limitação de recursos financeiros ou operacionais que restringe o número total de eletropostos que podem ser construídos.

Por pertencer à classe de problemas **NP-difícil (NP-hard)**, a obtenção de soluções ótimas para instâncias de grande porte exige o uso de modelos matemáticos avançados de programação inteira e algoritmos de otimização eficientes.

---

## 🌍 Dados da Instância

Uma instância de grande porte está estruturada no arquivo **`Instancia_PLMC_Eletropostos.xlsx`**, contendo abas específicas para os conjuntos, parâmetros e mapeamento de cobertura:

**1. Aba `Pontos_Demanda` (Conjunto $I$ com nomes e pesos)**:
| i | Nome_Demanda | lat | lon | peso |
| :---: | :--- | :---: | :---: | :---: |
| 1 | Polo Comercial Centro | -3.8515 | -38.4224 | 45 |
| 2 | Rodovia CE-040 km 18 | -3.7420 | -38.5533 | 120 |
| ... | ... | ... | ... | ... |

**2. Aba `Locais_Candidatos` (Conjunto $J$ com nomes dos postos potenciais)**:
| j | Nome_Candidato | lat | lon |
| :---: | :--- | :---: | :---: |
| 1 | Posto BR Rodovia Sul | -3.8832 | -38.4918 |
| 2 | Estacionamento Shopping Iguatemi | -3.7878 | -38.5139 |
| ... | ... | ... | ... |

**3. Aba `Conjunto_Ni` (Mapeamento de Cobertura $N_i$ pré-calculado)**:
Esta aba mapeia explicitamente quais locais candidatos cobrem cada ponto de demanda considerando o raio de cobertura:
| i | Nome_Demanda | candidatos_cobertura |
| :---: | :--- | :--- |
| 1 | Polo Comercial Centro | 3, 14, 42, 105 |
| 2 | Rodovia CE-040 km 18 | 8, 12, 19 |

**4. Aba `ParametrosGlobais`**:
| Parametro | Valor |
| :--- | :--- |
| p (Eletropostos a instalar) | 50 |
| Raio de cobertura em km | 3.5 |

---

## ⚙️ Métodos de Resolução Sugeridos
Devido à natureza NP-difícil do problema, sugerem-se as seguintes abordagens:
- **Modelagem Exata (MILP)**: Utilizando solvers (Gurobi, CPLEX, SCIP) com o auxílio da aba `Conjunto_Ni` para alimentar diretamente os parâmetros de restrição.
- **Metaheurísticas**: GRASP, Algoritmos Genéticos ou Simulated Annealing para explorar a matriz de cobertura em instâncias de larga escala.

## 📚 Referências

Church, R., & ReVelle, C. (1974). The Maximal Covering Location Problem. Papers of the Regional Science Association, 32(1), 101-118.

Kuby, M., & Lim, S. (2005). The flow-refueling location problem for alternative-fuel vehicles. Socio-Economic Planning Sciences, 39(2), 125-145.

Capar, I., Kuby, M., Leon, V. J., & Tsai, Y. J. (2013). An arc cover-path-cover formulation and strategic analysis of the flow-refueling location problem. European Journal of Operational Research, 227(3), 482-492.

## 🚀 Possíveis Extensões

Inclusão de Múltiplos Tipos de Carregadores (Lento, Rápido, Ultra-rápido).

Formulação como Problema de Localização Capacitada, onde cada eletroposto tem um limite máximo de veículos atendidos por hora (evitando filas).

Consideração do Comportamento Estocástico da Demanda (variações de tráfego por horário/dia da semana).

Flow Refueling Location Model (FRLM): Focar estritamente em garantir que veículos completem viagens inteiras de origem-destino sem ficar sem bateria, em vez de apenas cobertura de nós.

## 🎥 Vídeo Explicativo e Simulação

[![Vídeo demonstrando o Problema de p-Medianas aplicado à gestão de Malha Logística.](Link do Vídeo no Youtube)](#)