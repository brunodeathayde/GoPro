# 🗓️ Escalonamento de Recursos em Múltiplos Projetos sem Precedência – Alocação de Consultores em Projetos de Consultoria em Engenharia de Produção

## 📌 Descrição do Problema

Este repositório apresenta uma instância de grande porte do **Problema de Escalonamento de Recursos em Múltiplos Projetos sem Restrições de Precedência (Multi-Project Resource Scheduling Problem – MPRSP, variante não-preemptiva e sem precedência)**, aplicada à programação da carteira de contratos de uma **empresa de consultoria em engenharia de produção**.

Cada **projeto** representa uma consultoria contratada por uma empresa cliente para resolver um problema de processo (perda de qualidade, baixa produtividade, gargalos operacionais etc.). Cada projeto é decomposto em **atividades** que correspondem às etapas do ciclo de vida de resolução de problemas usado pela consultoria (diagnóstico, mapeamento do processo, identificação da causa raiz, plano de ação e plano de controle). O objetivo é decidir **quando** iniciar cada atividade de cada projeto, alocando a equipe de consultores (recurso compartilhado e limitado) entre todos os clientes simultaneamente, minimizando o atraso/tempo de conclusão dos projetos e respeitando estritamente a capacidade disponível de cada tipo de consultor a cada semana.

Diferentemente do RCPSP clássico, **não há relação de precedência obrigatória entre as atividades**: embora as fases sigam uma ordem lógica dentro de cada metodologia de resolução de problemas, a equipe de consultores atende várias frentes de vários clientes ao mesmo tempo, de modo que cada atividade é tratada como um pacote de trabalho independente, sujeito apenas à disputa pelos mesmos consultores no mesmo período.

---

## 🎯 Enunciado do Problema

Desenvolver e analisar métodos de resolução (algoritmos exatos via solver MILP, heurísticas de construção ou metaheurísticas) para o **Problema de Escalonamento de Recursos em Múltiplos Projetos de Consultoria (PERMP)**, otimizando a alocação da equipe técnica (consultores sêniores, plenos, analistas de dados e especialistas em melhoria contínua) entre os diversos contratos ativos, sob restrições de capacidade de recursos, janelas de liberação e prazos contratuais.

---

## 🌍 Dados da Instância de Grande Porte

A instância completa contendo **50 projetos (contratos de clientes)** e **250 atividades (5 por projeto)**, distribuídos ao longo de um horizonte de **52 semanas**, encontra-se disponível na planilha **`Instancia_Escalonamento_Multiprojetos_Grande_Porte.xlsx`**.

### Amostra dos Dados dos Projetos (aba `Projetos`)

| ID Projeto | Empresa Cliente | Setor | Semana de Liberação | Prazo (semana) | Valor do Contrato (R$) |
| :---: | :--- | :--- | :---: | :---: | :---: |
| P001 | Grupo Progresso Ltda. | Logística e Transporte | 14 | 25 | R$ 465.718,71 |
| P002 | Grupo Cidadela Indústria e Comércio Ltda. | Eletroeletrônicos | 2 | 12 | R$ 204.623,65 |
| P003 | Distribuidora Ceará Ltda. | Bebidas | 34 | 48 | R$ 336.049,16 |
| P004 | Corporação Ceará Ltda. | Agroindústria | 27 | 41 | R$ 168.623,31 |
| P005 | Grupo Nordeste Indústria e Comércio Ltda. | Telecomunicações | 6 | 20 | R$ 424.123,84 |
| ... | ... | ... | ... | ... | ... |
| **Total** | **50 Projetos** | — | — | — | **R$ 17.835.828,38** |

### Amostra das Atividades do Projeto P001 (aba `Atividades`)

| ID Atividade | Fase / Atividade | Duração (semanas) | Consultor Sênior | Consultor Pleno | Analista de Dados | Especialista LSS |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: |
| A0001 | Diagnóstico Inicial e Coleta de Dados | 1 | 1 | 1 | 1 | 0 |
| A0002 | Mapeamento do Processo (AS-IS) | 4 | 0 | 2 | 2 | 0 |
| A0003 | Identificação da Causa Raiz | 1 | 1 | 0 | 1 | 1 |
| A0004 | Elaboração do Plano de Ação | 1 | 2 | 2 | 0 | 0 |
| A0005 | Implementação do Plano de Controle | 3 | 0 | 1 | 1 | 1 |

### Capacidade dos Recursos (aba `Recursos`)

| Recurso ($k$) | Capacidade/Semana ($R_k$) | Custo-Hora (R$) |
| :--- | :---: | :---: |
| Consultor Sênior | 8 | R$ 380,00 |
| Consultor Pleno | 14 | R$ 220,00 |
| Analista de Dados | 6 | R$ 180,00 |
| Especialista Lean Six Sigma | 5 | R$ 320,00 |

A aba `Resumo` traz indicadores agregados calculados por fórmula (nº de projetos e atividades, valor total dos contratos, duração média das atividades e consumo total planejado de cada recurso frente à capacidade disponível no horizonte), e a aba `Legenda` documenta a correspondência entre cada coluna e os parâmetros do modelo MILP.

---

## 🧮 Dados

### Conjuntos
- projetos (contratos de clientes)
- atividades do projeto $p$
- tipos de recurso renovável (categorias de consultores)
- semanas do horizonte de planejamento

### Parâmetros
- duração da atividade (semanas)
- consultores de cada tipo requeridos por cada tividade em cada semana ativa
- capacidade de um determinado recurso por semana
- semana de liberação do projeto (release date)
- prazo contratual de entrega de cada projeto
- peso/prioridade do projeto $p$ (ex.: valor do contrato)

Note que **não há restrição de precedência** entre atividades de um mesmo projeto — a única interação entre elas ocorre pela disputa por consultores na restrição de capacidade.

---

## ⚙️ Métodos de Resolução Otimizados

Devido ao caráter **NP-difícil** do escalonamento de recursos compartilhados entre múltiplos projetos, o problema admite diferentes estratégias de resolução:

- **Programação Linear Inteira Mista (MILP)**:
  - Resolução exata utilizando *solvers* de alto desempenho (IBM ILOG CPLEX, Gurobi, CBC, SCIP, PyPSA/PuLP).
  - Formulações alternativas indexadas no tempo ou disjuntivas (*big-M*) com cortes válidos para acelerar o *Branch-and-Bound*.
- **Metaheurísticas e Algoritmos Aproximados**:
  - **GRASP (Greedy Randomized Adaptive Search Procedure)**
  - **Algoritmos Genéticos (AG)**
  - **Simulated Annealing (SA) / Busca Tabu**
  - **Variable Neighborhood Search (VNS)**
  - **Priority-Rule Based Scheduling** (regras de despacho adaptadas de RCPSP, ex.: prazo mais cedo, maior valor de contrato, menor folga)

---

## 📚 Referências Bibliográficas

- Kolisch, R., & Padman, R. (2001). *An integrated survey of deterministic project scheduling*. Omega, 29(3), 249-272.
- Lova, A., Tormos, P., & Barber, F. (2006). *Multi-mode resource constrained project scheduling: Scheduling schemes, priority rules and mode selection*. Inteligencia Artificial, 10(30), 69-86.
- Confessore, G., Giordani, S., & Rismondo, S. (2007). *A market-based multi-agent system model for decentralized multi-project scheduling*. Annals of Operations Research, 150(1), 115-135.
- Vanhoucke, M. (2013). *Project Management with Dynamic Scheduling: Baseline Scheduling, Risk Analysis and Project Control*. Springer.
- Pritsker, A. A. B., Watters, L. J., & Wolfe, P. M. (1969). *Multiproject scheduling with limited resources: A zero-one programming approach*. Management Science, 16(1), 93-108.

---

## 🚀 Possíveis Extensões

- **Múltiplos Modos de Execução (Multi-Mode)**: cada atividade poderia ser executada com diferentes combinações de equipe (ex.: mais consultores plenos e menos horas, ou um sênior sozinho), trocando duração por consumo de recurso.
- **Recursos Não-Renováveis**: incorporação de orçamento total de viagens/despesas por projeto.
- **Precedência Suave (Soft Precedence)**: penalizar, mas não proibir, o início de uma fase antes da anterior estar concluída, para refletir dependências informais do método de resolução de problemas.
- **Alocação Multiobjetivo**: balancear simultaneamente atraso, custo de horas extras dos consultores e nivelamento de carga (*resource leveling*) entre as equipes.
- **Reagendamento Dinâmico**: chegada estocástica de novos contratos ao longo do ano, exigindo replanejamento contínuo da carteira de projetos.

---

## 🎥 Vídeo Explicativo e Simulação

[![Vídeo demonstrando o Problema de Escalonamento de Recursos em Múltiplos Projetos aplicado à alocação de consultores em contratos de engenharia de produção.](Link do Vídeo no Youtube)](https://youtu.be/XXXXXXXXX)
