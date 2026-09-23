# 💊 Problema de Sequenciamento de Projetos com Recursos Limitados (RCPSP) – Cronograma de Desenvolvimento de um Novo Antibiótico

## 📌 Descrição do Problema

Este repositório apresenta uma instância de grande porte do **Problema de Sequenciamento de Projetos com Recursos Limitados (Resource-Constrained Project Scheduling Problem – RCPSP)**, aplicada ao planejamento do **cronograma de desenvolvimento de um novo antibiótico** em uma indústria farmacêutica.

Diferentemente do PSP clássico (apenas com restrições de precedência), o RCPSP aqui tratado é estruturado com **restrições de precedência E restrições de recursos renováveis limitados**: além de respeitar a ordem lógica entre as atividades, o cronograma deve respeitar, a cada instante, a **capacidade limitada** de equipes de pesquisadores, equipamentos de laboratório, equipes/centros de pesquisa clínica, linhas de produção piloto e equipes regulatórias disponíveis para a execução simultânea das atividades.

O objetivo principal é determinar a **programação (datas de início e término) de todas as atividades** que **minimize a duração total do projeto** (makespan), respeitando simultaneamente a rede de precedências e a disponibilidade limitada de cada tipo de recurso ao longo de todo o horizonte de planejamento das etapas de **pesquisa, desenvolvimento e lançamento** do novo medicamento.

---

## 🎯 Enunciado do Problema

O projeto abrange todo o ciclo de vida de P&D de um novo antibiótico — da descoberta do composto candidato até o lançamento comercial — organizado em três grandes fases:

1. **Pesquisa (Research)**: identificação do alvo molecular, triagem e síntese de compostos, ensaios in vitro e in vivo, seleção do candidato a fármaco e depósito de patente. Demanda principalmente **equipe de pesquisadores** e **equipamentos de laboratório**.
2. **Desenvolvimento (Development)**: ensaios clínicos Fase I, II e III, scale-up produtivo, validações analíticas e de boas práticas de fabricação (GMP), e elaboração do dossiê regulatório. Demanda principalmente **equipamentos de laboratório**, **equipes de pesquisa clínica** e **equipe regulatória**.
3. **Lançamento (Launch)**: submissão e obtenção do registro sanitário, produção em escala comercial, precificação, estratégia comercial, distribuição e farmacovigilância pós-lançamento (Fase IV). Demanda principalmente **linhas de produção** e **equipe regulatória**.

Cada atividade do projeto possui: (i) uma ou mais **atividades predecessoras**, que devem ser concluídas antes do seu início; e (ii) uma **demanda constante de recursos renováveis** durante toda a sua execução (por exemplo, 2 pesquisadores e 1 equipamento de laboratório, do início ao fim da atividade). Cada tipo de recurso possui uma **disponibilidade (capacidade) constante e limitada** ao longo de todo o horizonte do projeto — os recursos não se acumulam de um dia para o outro.

O problema consiste em programar todas as atividades — respeitando **simultaneamente** as relações de precedência e as restrições de capacidade de cada recurso a cada instante — de forma a **minimizar a duração total do projeto**. Diferentemente do PSP sem recursos (resolvido em tempo polinomial via CPM), o RCPSP é **NP-difícil**, sendo tipicamente resolvido por meio de **heurísticas construtivas baseadas em regras de prioridade** ou por **metaheurísticas**.

---

## 🌍 Dados da Instância de Grande Porte

A instância completa contendo **100 atividades** (36 de Pesquisa, 40 de Desenvolvimento, 20 de Lançamento e 4 marcos de transição entre fases) e **5 tipos de recursos renováveis** encontra-se disponível na planilha **`Instancia_RCPSP_Farmaceutico_com_Recursos.xlsx`**.

### Amostra dos Dados das Atividades (aba `Atividades`)

| ID | Nome da Atividade | Fase | Predecessoras | Duração (dias) | R1 | R2 | R3 | R4 | R5 | Custo Normal (R$) |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| M000 | Início do Projeto (Marco) | Marco | — | 0 | 0 | 0 | 0 | 0 | 0 | R$ 0,00 |
| PES001 | Revisão da literatura e identificação de gaps terapêuticos | Pesquisa | M000 | 5 | 2 | 2 | 0 | 0 | 1 | R$ 167.774,00 |
| PES005 | Síntese química de compostos candidatos | Pesquisa | M000 | 23 | 1 | 1 | 0 | 0 | 0 | R$ 166.284,00 |
| PES006 | Purificação e caracterização estrutural dos compostos | Pesquisa | PES001,PES002,PES003,PES004,PES005 | 21 | 3 | 2 | 0 | 0 | 1 | R$ 27.211,00 |
| M001 | Aprovação do Candidato a Fármaco (Marco) | Marco | PES033,PES034,PES035,PES036 | 0 | 0 | 0 | 0 | 0 | 0 | R$ 0,00 |
| DEV001 | Elaboração do protocolo de ensaio clínico Fase I | Desenvolvimento | M001 | ... | ... | ... | ... | ... | ... | ... |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |
| **Total** | **100 Atividades** | — | — | **2.662 dias** | **89** | **109** | **91** | **59** | **108** | **R$ 28.414.496,00** |

> A soma das durações e das demandas de recursos **não** representa a solução do problema — o cronograma final (e sua duração mínima, o makespan) depende de como as atividades são sequenciadas respeitando tanto a precedência quanto a disponibilidade de recursos a cada instante.

### Recursos Renováveis e Disponibilidade (aba `Recursos`)

| Código | Recurso (renovável) | Unidade | Disponibilidade (capacidade constante) |
| :---: | :--- | :---: | :---: |
| R1 | Equipe de Pesquisadores (P&D) | pesquisadores/dia | 8 |
| R2 | Equipamentos de Laboratório/Síntese | equipamentos/dia | 5 |
| R3 | Equipe e Centros de Pesquisa Clínica | equipes clínicas/dia | 8 |
| R4 | Linha de Produção Piloto/Industrial | linhas de produção/dia | 6 |
| R5 | Equipe Regulatória e de Qualidade | analistas/dia | 5 |

> As disponibilidades foram calibradas para ficarem **abaixo do pico de demanda simultânea** que ocorreria se todas as atividades elegíveis (segundo a precedência) fossem iniciadas ao mesmo tempo — tornando o problema efetivamente restrito por recursos, e não apenas por precedência.

---

## ⚙️ Métodos de Resolução

Por combinar restrições de precedência **e** de recursos, o RCPSP é **NP-difícil** em sentido forte, não admitindo solução exata eficiente para instâncias de grande porte:

- **Métodos Exatos**:
  - Formulação em **Programação Linear Inteira Mista (MILP)**, resolvida por *solvers* de alto desempenho (CPLEX, Gurobi, CBC), viável apenas para instâncias de pequeno/médio porte dado o crescimento combinatório do espaço de soluções.
  - **Branch-and-Bound** especializado, explorando esquemas de geração de cronogramas (*Schedule Generation Scheme – SGS*).
- **Heurísticas Construtivas** baseadas em **regras de prioridade** (*priority rules*), aplicadas dentro de um esquema serial ou paralelo de geração de cronograma (SGS):
  - **SPT/LPT** (menor/maior duração), **LFT** (*Latest Finish Time*), **MTS** (*Most Total Successors*), **GRPW** (*Greatest Rank Positional Weight*), entre outras.
- **Metaheurísticas**, amplamente utilizadas na literatura para instâncias de grande porte:
  - **Simulated Annealing (SA)** e **Busca Tabu**
  - **Iterated Greedy (IG)**, inclusive variantes híbridas com busca local (**IG+CP**) e reaquecimento (**RIG+CP**)
  - **Algoritmos Genéticos (AG)** e **GRASP**
  - **Otimização por Colônia de Formigas (ACO)** e **Variable Neighborhood Search (VNS)**
  - **Resolvedores de Programação por Restrições (Constraint Programming - CP)**

---

## 📚 Referências Bibliográficas

- Kelley, J. E., & Walker, M. R. (1959). *Critical-path planning and scheduling*. Proceedings of the Eastern Joint Computer Conference, 160-173.
- Kolisch, R., & Padman, R. (2001). *An integrated survey of deterministic project scheduling*. Omega, 29(3), 249-272.
- Kolisch, R., & Sprecher, A. (1997). *PSPLIB – A project scheduling problem library*. European Journal of Operational Research, 96(1), 205-216.
- Demeulemeester, E. L., & Herroelen, W. S. (2002). *Project scheduling: A research handbook*. Springer.
- Hartmann, S., & Briskorn, D. (2010). *A survey of variants and extensions of the resource-constrained project scheduling problem*. European Journal of Operational Research, 207(1), 1-14.
- Vanhoucke, M. (2012). *Project management with dynamic scheduling*. Springer.

---

## 🚀 Possíveis Extensões

- **Recursos Não Renováveis e Duplamente Restritos**: incorporação de orçamento total limitado (recurso não renovável), combinando restrições de recursos renováveis e não renováveis (RCPSP com múltiplos modos, *Multi-Mode RCPSP*).
- **Múltiplos Modos de Execução (MRCPSP)**: cada atividade pode ser executada em diferentes modos (combinações de duração x consumo de recursos x custo), permitindo *time-resource tradeoff*.
- **Multiprojeto (RCMPSP)**: gestão simultânea do cronograma de várias moléculas em desenvolvimento (pipeline farmacêutico), compartilhando o mesmo pool de recursos renováveis.
- **Incerteza (RCPSP Estocástico)**: durações ou disponibilidade de recursos variáveis, tratadas via simulação de Monte Carlo ou programação estocástica.
- **Janelas Regulatórias**: incorporação de prazos fixos de resposta e datas de corte impostas por agências reguladoras (ex: ANVISA, FDA) como restrições adicionais de tempo.

---

## 🎥 Vídeo Explicativo e Simulação

[![Vídeo demonstrando o Problema de Sequenciamento de Projetos com Recursos Limitados (RCPSP) aplicado ao cronograma de desenvolvimento de um novo antibiótico.](Link do Vídeo no Youtube)](https://youtu.be/XXXXXXXXX)
