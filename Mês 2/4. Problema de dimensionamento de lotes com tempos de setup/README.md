📦 Problema de Dimensionamento de Lotes com tempos de *setup* – Instância Real (Indústria de Fundição sob-pressão de Alumínio)

📌 Descrição do Problema

Este repositório apresenta uma instância do Problema de Dimensionamento de Lotes Capacitado com Preparação de Máquina e Precedência (CSLP com setup carryover), baseada em um cenário real da indústria de fundição sob-pressão de alumínio para o setor automotivo, conforme estudo de caso documentado na dissertação de mestrado de Alfredo Carvalho de Castro (UFMG, 2007).

O problema consiste em determinar o tamanho dos lotes e a sequência de produção de múltiplas peças em máquinas paralelas (injetoras de alumínio) ao longo de um horizonte de planejamento finito, respeitando restrições de capacidade produtiva (tempos de produção e setup), disponibilidade de ferramentas (moldes), demanda mínima e máxima contratada, e a condição de precedência (setup não é necessário quando a mesma peça continua em produção na passagem de um período para outro).

🎯 Enunciado do Problema

Definir o plano ótimo de produção para múltiplas peças em um parque de máquinas paralelas heterogêneas (injetoras de alumínio) em um horizonte de planejamento de 4 a 7 semanas (períodos), onde cada máquina pode produzir diferentes peças a cada período, respeitando:

- Demanda mínima e máxima contratada para cada peça em cada período;
- Capacidade produtiva disponível por máquina em cada período (horas);
- Tempos de setup (preparação) que consomem capacidade e incorrem em custo;
- Condição de precedência: se a mesma peça for produzida na mesma máquina em períodos consecutivos, não há necessidade de novo setup;
- Disponibilidade limitada de ferramentas (moldes) por tipo de peça;
- Capacidade limitada da equipe de preparação (setup) por período;
- Curva de aprendizado/rampa de produção no início da produção após setup;
- Máquinas heterogêneas (taxas de produção diferentes para a mesma peça);
- Não é permitido atraso na entrega (backlogging).

O objetivo principal é **maximizar o resultado operacional** (lucro), que é a margem de contribuição das peças vendidas subtraída dos custos de estocagem e preparação.

🧠 Descrição do Problema

O problema consiste em organizar a produção de diferentes peças fundidas sob-pressão ao longo do tempo, em um parque de máquinas injetoras de alumínio.

O processo produtivo (fundição sob-pressão) possui as seguintes características:

- Ciclo produtivo de única operação (single-level): a injeção é o gargalo do processo;
- Múltiplas máquinas em paralelo, heterogêneas (diferentes tonelagens, tempos de ciclo, capacidades);
- Cada máquina pode produzir apenas um subconjunto das peças (limitação técnica da ferramenta/matriz);
- Ferramentas (moldes) são recursos limitados e podem ser alocados a apenas uma máquina por vez;
- Setup (troca de ferramenta) consome tempo e recursos, mas é evitado quando há precedência;
- Curva de ramp-up: no início da produção após setup, há uma perda de produtividade e maior geração de peças defeituosas;
- Demanda com regime de variação: semanas 1-2 congeladas, semanas 3-4 com variação de até 15%, semanas 5+ com variação de até 100%;
- Estoques podem ser utilizados para antecipar produção e suavizar a utilização de capacidade.

Cada peça (SKU) possui:

- Demanda mínima e máxima por período (contrato com montadora);
- Margem de contribuição (preço de venda - custo variável);
- Custo de estocagem por período;
- Custo de setup (por preparação, variável por máquina);
- Tempo de setup (horas, podendo ser evitado por precedência);
- Tempo de produção unitário (horas/peça, variável por máquina);
- Estoque inicial conhecido.

Cada máquina possui:

- Capacidade disponível por período (horas, considerando manutenções);
- Conjunto de peças que pode produzir (compatibilidade ferramenta-máquina).

O planejamento deve garantir que:

- A demanda entregue em cada período esteja entre o mínimo e máximo contratado;
- A capacidade de cada máquina não seja excedida (tempo de produção + tempo de setup ≤ capacidade);
- O setup seja contabilizado apenas no primeiro período de produção de uma peça em uma máquina (precedência);
- No máximo uma peça tenha precedência por máquina por período;
- O número de ferramentas de cada peça em uso simultâneo não exceda o disponível;
- A equipe de preparação não exceda sua capacidade de setups por período.

O objetivo é **maximizar**:
Lucro Total = Soma(peças vendidas × margem) - Soma(estoque × custo estocagem) - Soma(setups realizados × custo setup)

Este problema é classificado na notação de Salomon (1991) como **P/*/*/SI/G/SI** (máquinas paralelas heterogêneas, número variável de máquinas e produtos, setup independente da sequência, custo de produção variável, tempo de setup independente da sequência), com a particularidade da precedência (setup carryover) que permite economia de setup em períodos consecutivos.

A complexidade combinatória é alta, caracterizando-se como um problema NP-difícil, especialmente quando se integram decisões de dimensionamento e sequenciamento.

🚚 Dados da Instância

Parâmetros Gerais

- Horizonte de planejamento: 4 a 7 semanas (T = 4, 5, 6 ou 7)
- Máquinas disponíveis: 4 a 10 injetoras (M = 4, 5, 6, 7, 8, 9, 10)
- Peças produzidas: 4 a 13 tipos (P = 4, 5, 6, 7, 8, 9, 10, 11, 12, 13)
- Capacidade por máquina por semana: variável (típico: 120 horas/semana)
- Capacidade da equipe de setup: limitada (típico: 40 horas/semana)

Produtos (Peças) – Exemplo para instância de pequeno porte

| Peça | Margem (R$/unid) | Custo Estoque (R$/unid/sem) | Custo Setup (R$) | Tempo Setup (h) | Tempo Unitário (h/unid) | Estoque Inicial |
|------|------------------|----------------------------|------------------|-----------------|------------------------|-----------------|
| P1    | 15,00            | 0,50                       | 800,00           | 2,5             | 0,15                   | 1.000           |
| P2    | 12,00            | 0,40                       | 600,00           | 2,0             | 0,12                   | 800             |
| P3    | 18,00            | 0,60                       | 1.000,00         | 3,0             | 0,18                   | 500             |
| P4    | 10,00            | 0,30                       | 500,00           | 1,5             | 0,10                   | 1.200           |

Máquinas – Exemplo para instância de pequeno porte

| Máquina | Capacidade (h/semana) | Peças compatíveis |
|---------|----------------------|-------------------|
| M1      | 120                   | P1, P2, P3        |
| M2      | 120                   | P1, P2, P4        |
| M3      | 110                   | P2, P3, P4        |
| M4      | 100                   | P1, P3, P4        |

Ferramentas (moldes) disponíveis

| Peça | Nº de ferramentas |
|------|-------------------|
| P1   | 2                 |
| P2   | 2                 |
| P3   | 1                 |
| P4   | 2                 |

Demanda por semana (exemplo para 4 períodos)

| Peça | Semana 1 (min/max) | Semana 2 (min/max) | Semana 3 (min/max) | Semana 4 (min/max) |
|------|--------------------|--------------------|--------------------|--------------------|
| P1   | 500 / 550          | 520 / 580          | 530 / 650          | 510 / 600          |
| P2   | 600 / 650          | 610 / 680          | 620 / 750          | 600 / 700          |
| P3   | 300 / 330          | 310 / 350          | 320 / 400          | 310 / 380          |
| P4   | 700 / 750          | 720 / 800          | 730 / 880          | 710 / 820          |

Condição de partida (ferramentas instaladas no início do período 1)

| Máquina | Peça instalada |
|---------|----------------|
| M1      | P1             |
| M2      | P2             |
| M3      | Nenhuma        |
| M4      | P4             |

Rampa de produção (perda no início)

| Peça | Perda no ramp-up (unidades) | Tempo adicional no setup (h) |
|------|----------------------------|------------------------------|
| P1   | 50                         | 0,5                          |
| P2   | 40                         | 0,4                          |
| P3   | 60                         | 0,6                          |
| P4   | 30                         | 0,3                          |

*Nota: O tempo de setup efetivo a ser modelado é Time_Setup + (Perda_RampUp × Tempo_Unitário)*

Classificação do porte da instância

| Porte | Nº máquinas (M) | Nº peças (P) | Nº períodos (T) | Nº variáveis aproximado |
|-------|----------------|--------------|-----------------|------------------------|
| Pequeno | 4 - 5 | 4 - 6 | 4 - 5 | Até 300 |
| Médio | 6 - 10 | 7 - 13 | 5 - 7 | 301 - 3.500 |
| Grande | 10 - 20 | 13 - 24 | 6 - 8 | 3.500 - 13.000 |

📚 Referências

- Castro, A. C. (2007). Tamanhos de lotes capacitados com preparação de máquina em sistemas produtivos ininterruptos. Dissertação (Mestrado em Engenharia de Produção), Universidade Federal de Minas Gerais, Belo Horizonte, MG, Brasil.
- Wagner, H. M., Whitin, T. M. (1958). Dynamic version of the economic lot size model. Management Science, 5(1), 89–96.
- Pochet, Y. (2001). Mathematical programming models and formulations for deterministic production planning problems. Computational Combinatorial Optimization, Lecture Notes in Computer Science 2241, 57–111, Springer-Verlag.
- Salomon, M. (1991). Deterministic Lot Sizing Models for Production Planning. Lecture Notes in Economics and Mathematical Systems, Springer-Verlag.
- Drexl, A., & Kimms, A. (1997). Lot sizing and scheduling – Survey and extensions. European Journal of Operational Research, 99, 221–235.
- Fleischmann, B. (1990). The discrete lot-sizing and scheduling problem. European Journal of Operational Research, 44, 337–348.
- Trigeiro, W., Thomas, L., & McClain, O. (1989). Capacitated lot sizing with setup times. Management Science, 35(3), 353–366.
- Karmarkar, U., & Schrage, L. (1985). The deterministic dynamic production cycling problem. Operations Research, 33(2), 326–345.
- Vanderbeck, F. (1998). Lot-sizing with start-up times. Management Science, 44(10), 1409–1425.
- Wolsey, L. A. (2002). Solving multi-item lot-sizing problems with an MIP solver using classification and reformulation. Management Science, 48(12), 1587–1602.

🚀 Possíveis Extensões

- Setup dependente da sequência (changeover): custo e tempo variam conforme a ordem de produção (ex: tinta clara → escura vs escura → clara);
- Incluir múltiplos estágios (multi-level): produção depende de subcomponentes;
- Permitir backlogging (atraso na entrega) com penalização;
- Incorporar incerteza na demanda (modelos estocásticos);
- Integração com planejamento de manutenção preventiva;
- Considerar custo de oportunidade do capital imobilizado em estoque;
- Aplicação de métodos exatos avançados:
  - Branch-and-Cut;
  - Branch-and-Price;
  - Geração de colunas com relaxação lagrangeana;
- Aplicação de heurísticas e metaheurísticas para problemas de grande porte:
  - Heurística construtiva de duas etapas (conforme proposta na dissertação);
  - GRASP;
  - Algoritmos Genéticos;
  - Simulated Annealing;
  - Busca Tabu (já aplicada em Gopalakrishnan et al., 2001);
  - Colônia de Formigas (Ant Colony);
- Considerar produção em lote mínimo (economia de escala);
- Incorporar múltiplas cavidades por ferramenta (mais peças por ciclo);
- Modelar a perda de qualidade no ramp-up (peças defeituosas) como custo adicional.

- ## 🎥 Vídeo explicativo

[![Assista ao vídeo no YouTube](https://img.youtube.com/vi/UJBrpC1NvZc/maxresdefault.jpg)](https://youtu.be/UJBrpC1NvZc)

> *Vídeo demonstrando uma instância real do Problema de Dimensionamento de Lotes Capacitado com Preparação de Máquina e Precedência (CSLP com setup carryover), aplicada à indústria de fundição sob-pressão de alumínio para o setor automotivo.*

