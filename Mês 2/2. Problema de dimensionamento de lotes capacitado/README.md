📦 Problema de Dimensionamento de Lotes Capacitado – Instância Real (Indústria de Blocos Pré-moldados de Concreto)

📌 Descrição do Problema

Este repositório apresenta uma instância do Problema de Dimensionamento de Lotes Capacitado (Capacitated Lot Sizing Problem – CLSP), baseada em um cenário real de uma fábrica de blocos pré-moldados de concreto, conforme estudo de caso documentado na dissertação de mestrado de Bruno Gomes Cunha (UFPB, 2013).

O problema consiste em determinar o tamanho dos lotes e a sequência de produção de diferentes blocos ao longo de um horizonte de planejamento finito (2 semanas), respeitando restrições de capacidade produtiva (tempos de produção e setup), estoque mínimo e lote mínimo, de forma a minimizar os custos de produção, setup e armazenagem.

🎯 Enunciado do Problema

Definir o plano ótimo de produção para 4 tipos diferentes de blocos (Bloco, Meio Bloco, Paver e Outros) em um horizonte de 2 semanas (macroperíodos), onde cada semana é subdividida em 10 turnos de 4 horas (microperíodos), garantindo:

- Atendimento total da demanda sem atrasos (backlogging não é permitido);
- Respeito à capacidade produtiva disponível por turno (240 minutos);
- Cumprimento do estoque de segurança para cada produto;
- Respeito ao lote mínimo de produção por setup;
- Minimização da soma dos custos de produção, setup e estocagem.

Este é um problema de otimização combinatória de médio/curto prazo, classificado como NP-difícil, típico de ambientes com alta variedade de produtos e tempos de setup elevados.

🧠 Descrição do Problema

O problema consiste em organizar a produção de diferentes blocos pré-moldados ao longo do tempo, em uma única linha de prensagem.

Cada bloco (SKU) possui:

- Demanda determinística e dinâmica (varia por semana);
- Custo unitário de produção;
- Custo unitário de estocagem;
- Custo de setup (incorrido sempre que a linha é preparada para produzir aquele bloco);
- Tempo unitário de produção (minutos por unidade);
- Tempo de setup (minutos necessários para trocar a matriz/preparar a linha);
- Estoque inicial conhecido;
- Estoque de segurança obrigatório;
- Lote mínimo de produção (economia de escala).

O sistema produtivo tem as seguintes características:

- Única linha de produção (prensa vibratória);
- Capacidade limitada por turno (240 minutos);
- Setup elevado (50 a 80 minutos por troca);
- Dois turnos por dia, cinco dias por semana (10 turnos/semana);
- Não é permitida falta de estoque (atraso na entrega);
- Produtos classificados como MTS (make-to-stock) para alta demanda e MTO (make-to-order) para baixa demanda.

O planejamento deve garantir que:

- A demanda de cada semana seja atendida integralmente;
- Os estoques no final de cada semana respeitem o estoque de segurança;
- A capacidade de cada turno não seja excedida (tempo de produção + setup ≤ 240 min);
- A produção só ocorra se a linha estiver preparada para aquele bloco (setup ativo);
- O lote mínimo seja respeitado sempre que houver produção;
- A linha produza apenas um tipo de bloco por turno (unicidade de setup).

O objetivo principal é minimizar o custo total, composto por:

- Custo de produção (variável por unidade);
- Custo de setup (fixo por ativação do bloco);
- Custo de estocagem (sobre as unidades em estoque ao final de cada semana).

Este problema é uma extensão do CLSP clássico com janelas pequenas (small bucket) e é conhecido por sua alta complexidade computacional, especialmente quando se integram decisões de dimensionamento e sequenciamento.

🚚 Dados da Instância

Parâmetros Gerais

- Horizonte de planejamento: 2 semanas (S = 2)
- Turnos por semana: 10 turnos (T = 10)
- Capacidade por turno: 240 minutos (4 horas)
- Capacidade por semana: 2400 minutos (10 turnos × 240 min)

Produtos (SKUs)

| SKU | Custo Produção (R$/unid) | Custo Estocagem (R$/unid/semana) | Custo Setup (R$) | Tempo Unitário (min/unid) | Tempo Setup (min) | Lote Mínimo (unid) | Estoque Inicial (unid) | Estoque Segurança (unid) |
|-----|--------------------------|----------------------------------|------------------|---------------------------|--------------------|--------------------|------------------------|--------------------------|
| BLOCO | 2,27 | 0,11 | 2.025,00 | 0,0897 | 80 | 668 | 5.500 | 2.677 |
| MEIO BLOCO | 1,29 | 0,06 | 2.118,00 | 0,0475 | 78 | 1.263 | 7.800 | 5.053 |
| PAVER | 0,69 | 0,03 | 1.765,00 | 0,0215 | 55 | 2.791 | 350 | 11.163 |
| OUTROS | 0,50 | 0,03 | 1.442,00 | 0,0173 | 50 | 3.462 | 0 | 13.846 |

*Nota: Tempo unitário convertido de segundos para minutos (ex: 5,38s = 0,0897min)*

Demanda por Semana (unidades)

| SKU | Semana 1 | Semana 2 |
|-----|----------|----------|
| BLOCO | 6.750 | 7.500 |
| MEIO BLOCO | 13.500 | 16.250 |
| PAVER | 30.500 | 27.500 |
| OUTROS | 2.250 | 2.750 |

Capacidade Máxima por Turno (unidades)

| SKU | Unidades/turno |
|-----|----------------|
| BLOCO | 2.667 |
| MEIO BLOCO | 5.000 |
| PAVER | 10.000 |
| OUTROS | 13.333 |

*Fonte: Capacidade calculada como 240 minutos / tempo unitário*

📚 Referências

- Cunha, B. G. (2013). Otimização no Dimensionamento e Sequenciamento de Lotes de Produção: Estudo de Caso em uma Fábrica de Blocos Pré-moldados de Concreto. Dissertação (Mestrado em Engenharia de Produção), Universidade Federal da Paraíba, João Pessoa, PB, Brasil.
- Wagner, H. M., Whitin, T. M. (1958). Dynamic version of the economic lot size model. Management Science, 5(1), 89–96.
- Pochet, Y., Wolsey, L. A. (2006). Production Planning by Mixed Integer Programming. Springer.
- Drexl, A., & Kimms, A. (1997). Lot sizing and scheduling – survey and extensions. European Journal of Operational Research, 99, 221–235.
- Karimi, B., Ghomi, S. M. T. F., & Wilson, J. M. (2003). The capacitated lot sizing problem: A review of models and algorithms. Omega, 31, 365–378.

🚀 Possíveis Extensões

- Inclusão de múltiplas linhas de produção (máquinas paralelas idênticas ou distintas);
- Considerar manutenção preventiva programada nas linhas;
- Setup dependente da sequência (custos e tempos variam conforme a ordem de produção);
- Permitir backlogging (atraso na entrega) com penalização;
- Incorporar incerteza na demanda (modelos estocásticos);
- Integração com planejamento de distribuição e transporte;
- Aplicação de métodos exatos avançados (Branch-and-Cut, Branch-and-Price);
- Aplicação de heurísticas e metaheurísticas para problemas de grande porte:
  - GRASP com Path-Relinking;
  - Algoritmos Genéticos;
  - Simulated Annealing;
  - Busca Tabu;
  - Colônia de Formigas (Ant Colony);
  - Relax-and-Fix / Fix-and-Optimize.
