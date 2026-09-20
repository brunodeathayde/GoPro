# 💊 Problema de Sequenciamento de Projetos (PSP) – Cronograma de Desenvolvimento de um Novo Antibiótico

## 📌 Descrição do Problema

Este repositório apresenta uma instância de grande porte do **Problema de Sequenciamento de Projetos (Project Scheduling Problem – PSP)**, também conhecido na literatura como problema de programação de projetos com restrições de precedência, aplicada ao planejamento do **cronograma de desenvolvimento de um novo antibiótico** em uma indústria farmacêutica.

Diferentemente do RCPSP (Resource-Constrained Project Scheduling Problem), o PSP aqui tratado é estruturado **apenas com restrições de precedência**: as atividades possuem uma ordem lógica que deve ser respeitada (uma atividade só pode começar após a conclusão de suas predecessoras), mas **não há restrição de recursos** — considera-se disponibilidade ilimitada de mão de obra, maquinário e capital para executar quantas atividades forem necessárias simultaneamente.

O objetivo principal é determinar a **duração mínima do projeto** (makespan), identificar o **caminho crítico** e calcular as **folgas** de cada atividade, além de **estimar, via Simulação de Monte Carlo, a distribuição de probabilidade da duração total do projeto**, apoiando a tomada de decisão sobre o cronograma das etapas de **pesquisa, desenvolvimento e lançamento** do novo medicamento.

Diferentemente da abordagem clássica do PERT — que assume uma distribuição **Beta** para a duração de cada atividade —, nesta instância cada atividade com três tempos (otimista, mais provável e pessimista) segue uma **distribuição triangular**. Essa premissa é amplamente utilizada em análise de risco de cronogramas por não exigir o cálculo dos parâmetros da distribuição Beta e por permitir amostragem direta e eficiente em simulações de Monte Carlo.

---

## 🎯 Enunciado do Problema

O projeto abrange todo o ciclo de vida de P&D de um novo antibiótico — da descoberta do composto candidato até o lançamento comercial — organizado em três grandes fases:

1. **Pesquisa (Research)**: identificação do alvo molecular, triagem e síntese de compostos, ensaios in vitro e in vivo, seleção do candidato a fármaco e depósito de patente.
2. **Desenvolvimento (Development)**: ensaios clínicos Fase I, II e III, scale-up produtivo, validações analíticas e de boas práticas de fabricação (GMP), e elaboração do dossiê regulatório.
3. **Lançamento (Launch)**: submissão e obtenção do registro sanitário, produção em escala comercial, precificação, estratégia comercial, distribuição e farmacovigilância pós-lançamento (Fase IV).

Cada atividade do projeto possui uma ou mais **atividades predecessoras**, que devem ser concluídas antes do seu início. O problema consiste em programar todas as atividades — respeitando exclusivamente essas relações de precedência — de forma a **minimizar a duração total do projeto**, sendo resolvido de forma exata (determinística) por **CPM (Critical Path Method)**. Como as durações reais das atividades são incertas e modeladas por uma **distribuição triangular** (parametrizada por To, Tm e Tp), solicita-se adicionalmente a aplicação de uma **Simulação de Monte Carlo** para estimar a distribuição de probabilidade da duração total do projeto (makespan), a probabilidade de cumprimento de uma data-alvo de lançamento e a frequência com que cada atividade integra o caminho crítico (criticidade). Heurísticas e metaheurísticas podem ser empregadas quando extensões do problema (ver seção de extensões) são incorporadas.

---

## 🌍 Dados da Instância de Grande Porte

A instância completa contendo **100 atividades** (36 de Pesquisa, 40 de Desenvolvimento, 20 de Lançamento e 4 marcos de transição entre fases) encontra-se disponível na planilha **`Instancia_PSP_Farmaceutico.xlsx`**.

Para cada atividade são fornecidas três estimativas de duração — **Otimista (To)**, **Mais Provável (Tm)** e **Pessimista (Tp)** —, que definem os parâmetros de uma **distribuição triangular** Tri(To, Tm, Tp) para a duração da atividade. A duração determinística Tm é utilizada na resolução via **CPM**; já a incerteza descrita pela tripla (To, Tm, Tp) deve ser utilizada para **amostrar aleatoriamente** a duração de cada atividade a cada iteração da **Simulação de Monte Carlo**, recalculando o caminho crítico e a duração total do projeto a cada amostra. Também é fornecido um **Custo Normal** estimado por atividade, útil para extensões de *time-cost tradeoff* (aceleração de cronograma).

### Amostra dos Dados das Atividades

| ID | Nome da Atividade | Fase | Predecessoras | Dur. Otimista (dias) | Dur. Mais Provável (dias) | Dur. Pessimista (dias) | Custo Normal (R$) |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| M000 | Início do Projeto (Marco) | Marco | — | 0 | 0 | 0 | R$ 0,00 |
| PES001 | Revisão da literatura e identificação de gaps terapêuticos | Pesquisa | M000 | 3 | 5 | 6 | R$ 167.774,00 |
| PES005 | Síntese química de compostos candidatos | Pesquisa | M000 | 16 | 23 | 40 | R$ 166.284,00 |
| PES006 | Purificação e caracterização estrutural dos compostos | Pesquisa | PES001,PES002,PES003,PES004,PES005 | 14 | 21 | 37 | R$ 27.211,00 |
| M001 | Aprovação do Candidato a Fármaco (Marco) | Marco | PES033,PES034,PES035,PES036 | 0 | 0 | 0 | R$ 0,00 |
| DEV001 | Elaboração do protocolo de ensaio clínico Fase I | Desenvolvimento | M001 | — | — | — | — |
| ... | ... | ... | ... | ... | ... | ... | ... |
| **Total** | **100 Atividades** | — | — | **1.814 dias** | **2.662 dias** | **4.054 dias** | **R$ 28.414.496,00** |

> Os totais da tabela somam as durações e custos individuais de todas as atividades — **não** representam a duração real do projeto (makespan), que deve ser calculada respeitando a rede de precedências (caminho crítico).

---

## ⚙️ Métodos de Resolução

Por não possuir restrição de recursos, o PSP admite solução exata em tempo polinomial no caso determinístico. A instância, no entanto, pede explicitamente o tratamento probabilístico das durações via simulação:

- **Método do Caminho Crítico (CPM – Critical Path Method)** — linha de base determinística:
  - Cálculo de início mais cedo (ES), término mais cedo (EF), início mais tarde (LS), término mais tarde (LF) e folga (slack) de cada atividade, usando a duração Mais Provável (Tm).
  - Identificação do caminho crítico (sequência de atividades com folga zero) e da duração mínima do projeto no cenário determinístico.
- **Simulação de Monte Carlo com distribuição triangular** — método principal solicitado para estimar o risco do cronograma:
  1. Para cada uma das *N* iterações da simulação, sortear, para **cada atividade**, uma duração aleatória a partir da distribuição **triangular** Tri(To, Tm, Tp) — em vez da distribuição Beta assumida pelo PERT clássico.
  2. Recalcular a rede de precedências (forward/backward pass do CPM) com as durações sorteadas, obtendo a duração total do projeto (makespan) e o caminho crítico daquela iteração.
  3. Repetir por um número elevado de iterações (ex.: 10.000+) para construir a **distribuição empírica da duração do projeto**.
  4. A partir da distribuição empírica, estimar: a duração esperada e o desvio-padrão do projeto; a **probabilidade de conclusão até uma data-alvo**; e o **índice de criticidade** de cada atividade (percentual de iterações em que a atividade pertence ao caminho crítico).
- **Heurísticas e Metaheurísticas** (necessárias apenas em extensões do problema, como as descritas abaixo, que reintroduzem trade-offs de custo, recursos ou incerteza combinatória):
  - **Busca Tabu / Simulated Annealing** para *time-cost tradeoff* (aceleração de atividades do caminho crítico).
  - **Algoritmos Genéticos (AG)** para variantes multiobjetivo (tempo x custo x risco).

---

## 📚 Referências Bibliográficas

- Kelley, J. E., & Walker, M. R. (1959). *Critical-path planning and scheduling*. Proceedings of the Eastern Joint Computer Conference, 160-173.
- Malcolm, D. G., Roseboom, J. H., Clark, C. E., & Fazar, W. (1959). *Application of a technique for research and development program evaluation*. Operations Research, 7(5), 646-669.
- Kolisch, R., & Padman, R. (2001). *An integrated survey of deterministic project scheduling*. Omega, 29(3), 249-272.
- Demeulemeester, E. L., & Herroelen, W. S. (2002). *Project scheduling: A research handbook*. Springer.
- Vanhoucke, M. (2012). *Project management with dynamic scheduling*. Springer.
- Hulett, D. T. (2016). *Integrated cost-schedule risk analysis*. Routledge.
- Vose, D. (2008). *Risk analysis: A quantitative guide* (3rd ed.). John Wiley & Sons.
- Williams, T. M. (1992). *Practical use of distributions in network analysis*. Journal of the Operational Research Society, 43(3), 265-270.

---

## 🚀 Possíveis Extensões

- **RCPSP (Resource-Constrained Project Scheduling Problem)**: reintrodução de restrições de recursos limitados (equipes de pesquisadores, reatores de síntese, leitos de estudo clínico, linhas de produção piloto), tornando o problema NP-difícil e exigindo heurísticas/metaheurísticas.
- **Time-Cost Tradeoff (Crashing)**: uso dos custos normais fornecidos para modelar a aceleração de atividades do caminho crítico mediante custo adicional, buscando o menor custo para uma dada redução de prazo.
- **Multiprojeto**: gestão simultânea do cronograma de várias moléculas em desenvolvimento (pipeline farmacêutico), compartilhando marcos regulatórios e janelas de submissão.
- **Correlação entre atividades**: incorporação de correlação entre as durações de atividades similares (ex.: diferentes sites clínicos de uma mesma fase) na simulação de Monte Carlo, o que tende a aumentar a variância da duração total do projeto em relação ao cenário de independência.
- **Janelas Regulatórias**: incorporação de prazos fixos de resposta e datas de corte impostas por agências reguladoras (ex: ANVISA, FDA) como restrições adicionais de tempo.

---

## 🎥 Vídeo Explicativo e Simulação

[![Vídeo demonstrando o Problema de Sequenciamento de Projetos (PSP) aplicado ao cronograma de desenvolvimento de um novo antibiótico.](Link do Vídeo no Youtube)](https://youtu.be/XXXXXXXXX)
