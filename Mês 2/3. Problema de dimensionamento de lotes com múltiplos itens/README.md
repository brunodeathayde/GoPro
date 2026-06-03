# 📦 Problema de Dimensionamento de Lotes Multi-itens Capacitado – Instância Real (Indústria de Bebidas)

## 📌 Descrição do Problema

Este repositório apresenta uma instância do Problema de Dimensionamento de Lotes Capacitado Multi-itens (Capacitated Lot Sizing Problem – CLSP), baseada em um cenário real de planejamento da produção em uma indústria de bebidas não alcoólicas.

O problema consiste em determinar as quantidades ótimas de produção de múltiplos produtos ao longo de um horizonte de planejamento finito, respeitando limitações de capacidade produtiva, disponibilidade de matérias-primas, demandas dos clientes e custos de estocagem.

Diferentemente dos problemas integrados de dimensionamento e sequenciamento, esta instância não considera tempos nem custos de setup, sendo o foco exclusivamente a decisão de quanto produzir e estocar em cada período.

---

# 🎯 Enunciado do Problema

Definir o plano ótimo de produção para múltiplos produtos em uma fábrica de bebidas ao longo de um horizonte de planejamento de 6 a 12 meses, respeitando:

* Demanda de cada produto em cada período;
* Capacidade produtiva disponível da linha de envase;
* Disponibilidade de concentrados e embalagens;
* Limitações de armazenagem;
* Estoque inicial disponível;
* Ausência de atrasos de entrega (backlogging não permitido).

O objetivo principal é minimizar os custos totais de produção e estocagem.

---

# 🧠 Descrição do Problema

O problema consiste em planejar a produção mensal de diferentes bebidas comercializadas pela empresa.

O sistema produtivo possui as seguintes características:

* Produção em único estágio (single-level);
* Uma linha principal de envase compartilhada por todos os produtos;
* Capacidade produtiva limitada por horas disponíveis;
* Produção antecipada permitida;
* Estoques utilizados para balancear a utilização da capacidade;
* Demanda determinística conhecida ao longo do horizonte;
* Não são permitidos atrasos de entrega.

Cada produto (SKU) possui:

* Demanda mensal;
* Custo unitário de produção;
* Custo unitário de armazenagem;
* Tempo de processamento por unidade;
* Estoque inicial.

A linha produtiva possui:

* Capacidade mensal limitada;
* Disponibilidade variável devido a manutenções preventivas;
* Compartilhamento entre todos os produtos.

O planejamento deve garantir que:

* Toda a demanda seja atendida;
* O estoque permaneça não negativo;
* A capacidade produtiva mensal não seja excedida;
* O balanço de estoque seja respeitado em todos os períodos.

O objetivo é minimizar:

**Custo Total = Custos de Produção + Custos de Estocagem**

Este problema é classificado na literatura como um problema de Dimensionamento de Lotes Capacitado Multi-itens (CLSP), sendo um dos modelos clássicos de planejamento agregado da produção.

A complexidade combinatória cresce rapidamente com o número de produtos e períodos, caracterizando o problema como NP-difícil.

---

# 🚚 Dados da Instância

## Parâmetros Gerais

* Horizonte de planejamento: 6 meses
* Produtos: 5 SKUs
* Linha produtiva: 1
* Capacidade produtiva variável por mês
* Backlogging não permitido

---

## Produtos – Instância de Pequeno Porte

| Produto | Descrição                   |
| ------- | --------------------------- |
| P1      | Refrigerante Cola 350 ml    |
| P2      | Refrigerante Laranja 350 ml |
| P3      | Refrigerante Limão 350 ml   |
| P4      | Água Tônica 350 ml          |
| P5      | Energético 269 ml           |

---

## Dados dos Produtos

| Produto | Custo Produção (R$/caixa) | Custo Estoque (R$/caixa/mês) | Tempo Unitário (h/caixa) | Estoque Inicial |
| ------- | ------------------------- | ---------------------------- | ------------------------ | --------------- |
| P1      | 18,00                     | 0,80                         | 0,020                    | 2.000           |
| P2      | 17,00                     | 0,75                         | 0,018                    | 1.500           |
| P3      | 19,00                     | 0,85                         | 0,022                    | 1.000           |
| P4      | 20,00                     | 0,90                         | 0,025                    | 800             |
| P5      | 28,00                     | 1,20                         | 0,030                    | 500             |

---

## Demanda Mensal

| Produto | Mês 1 | Mês 2 | Mês 3 | Mês 4 | Mês 5  | Mês 6  |
| ------- | ----- | ----- | ----- | ----- | ------ | ------ |
| P1      | 8.000 | 8.500 | 9.000 | 9.500 | 10.000 | 10.500 |
| P2      | 5.000 | 5.200 | 5.500 | 5.700 | 6.000  | 6.200  |
| P3      | 4.000 | 4.300 | 4.500 | 4.800 | 5.000  | 5.200  |
| P4      | 3.000 | 3.200 | 3.400 | 3.600 | 3.800  | 4.000  |
| P5      | 2.000 | 2.200 | 2.500 | 2.800 | 3.000  | 3.200  |

---

## Capacidade Produtiva

| Mês | Capacidade Disponível (horas) |
| --- | ----------------------------- |
| 1   | 500                           |
| 2   | 520                           |
| 3   | 550                           |
| 4   | 530                           |
| 5   | 560                           |
| 6   | 600                           |

---

## Estoques Máximos Permitidos

| Produto | Estoque Máximo |
| ------- | -------------- |
| P1      | 6.000          |
| P2      | 4.000          |
| P3      | 3.000          |
| P4      | 2.500          |
| P5      | 2.000          |

---

## Classificação do Porte da Instância

| Porte   | Nº Produtos | Nº Períodos | Nº Variáveis Aproximado |
| ------- | ----------- | ----------- | ----------------------- |
| Pequeno | 5           | 6           | Até 100                 |
| Médio   | 20          | 12          | 500 – 2.000             |
| Grande  | 50          | 24          | 2.000 – 10.000          |

---

# 📚 Referências

* Trigeiro, W. W., Thomas, L. J., & McClain, J. O. (1989). Capacitated lot sizing with setup times. Management Science, 35(3), 353–366.

* Wagner, H. M., & Whitin, T. M. (1958). Dynamic version of the economic lot size model. Management Science, 5(1), 89–96.

* Pochet, Y., & Wolsey, L. A. (2006). Production Planning by Mixed Integer Programming. Springer.

* Drexl, A., & Kimms, A. (1997). Lot sizing and scheduling: Survey and extensions. European Journal of Operational Research, 99, 221–235.

* Florian, M., Lenstra, J. K., & Rinnooy Kan, A. H. G. (1980). Deterministic production planning: Algorithms and complexity. Management Science, 26(7), 669–679.

---

# 🚀 Possíveis Extensões

* Inclusão de tempos e custos de setup;
* Dimensionamento de lotes multinível (MLCLSP);
* Restrições de matérias-primas;
* Backlogging com penalização;
* Demandas estocásticas;
* Planejamento colaborativo da cadeia de suprimentos;
* Programação integrada produção-distribuição;
* Métodos exatos:

  * Branch-and-Bound;
  * Branch-and-Cut;
  * Decomposição de Benders;
  * Relaxação Lagrangeana.
* Metaheurísticas:

  * GRASP;
  * Busca Tabu;
  * Algoritmos Genéticos;
  * Simulated Annealing;
  * Variable Neighborhood Search.

