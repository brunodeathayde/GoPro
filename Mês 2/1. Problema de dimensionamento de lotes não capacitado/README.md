📦 Problema de Dimensionamento de Lotes – Instância Real (Indústria de Alimentos)
📌 Descrição do Problema
Este repositório apresenta uma instância do Problema de Dimensionamento de Lotes Não Capacitado (Uncapacitated Lot Sizing Problem – ULS), baseada em um cenário real da indústria de alimentos.
O problema consiste em determinar quando e quanto produzir de cada SKU ao longo de um horizonte de planejamento, de forma a atender a demanda diária, minimizando custos de produção e estocagem.
🎯 Enunciado do Problema
Definir o plano ótimo de produção para diferentes SKUs em um horizonte de 30 dias, garantindo que toda a demanda seja atendida, sem restrições de capacidade produtiva (não capacitado).
🧠 Descrição do Problema
O problema consiste em organizar a produção de diferentes SKUs ao longo do tempo.
Cada SKU possui:
Demanda diária (quantidade a ser atendida).
Possibilidade de antecipar produção (estoque).
Custos associados (produção e estocagem).
O planejamento deve garantir que:
Toda demanda seja atendida no dia correspondente.
Estoques sejam gerenciados corretamente.
Custos totais sejam minimizados.
O objetivo pode variar conforme a aplicação, incluindo:
Minimizar o custo total de produção e estoque.
Reduzir o número de setups de produção.
Garantir atendimento completo da demanda com menor custo operacional.
Este problema é uma extensão temporal do problema da mochila e é conhecido por sua alta complexidade computacional.
🚚 Dados da Instância
SKU	Dia	Quantidade
P4	1	5000
P4	2	8000
P1	3	2000
P1	3	1500
P4	4	7000
P2	5	4000
P3	6	3500
P5	7	10000
P3	8	4000
P1	9	3000
P5	10	40000
P5	10	30000
P6	11	9000
P3	12	5000
P4	13	6000
P2	14	4500
P6	15	8000
P1	16	4000
P4	17	12000
P3	18	4000
P5	19	15000
P7	20	10000
P2	21	3000
P3	22	4500
P4	23	5000
P6	24	7000
P5	25	18000
P1	26	3500
P3	27	4000
P7	28	6000
P4	29	4000
P5	30	5000


📚 Referências
Wagner, H. M., Whitin, T. M. (1958). Dynamic version of the economic lot size model. Management Science, 5(1), 89–96.
Pochet, Y., Wolsey, L. A. (2006). Production Planning by Mixed Integer Programming. Springer.
🚀 Possíveis Extensões
Inclusão de custos de setup (problema capacitado).
Considerar múltiplas linhas de produção.
Integração com planejamento de transporte.
Aplicação de heurísticas e metaheurísticas:
GRASP
Algoritmos Genéticos
Simulated Annealing
Busca Tabu
