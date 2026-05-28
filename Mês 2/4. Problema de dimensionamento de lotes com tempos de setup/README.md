# 📦 Problema de Dimensionamento de Lotes com Tempos de Setup – Instância Real (Indústria de Alimentos)

## 📌 Descrição do Problema

Este repositório apresenta uma instância do **Problema de Dimensionamento de Lotes com Tempos de Setup**, baseada em um cenário real da indústria de alimentos.  

O problema consiste em determinar quando e quanto produzir de cada SKU ao longo de um horizonte de planejamento, levando em consideração:  
- **Demandas sazonais** dos produtos.  
- **Custos de setup** associados à troca de linha de produção.  
- **Custos de estocagem** e restrições de perecibilidade.  
- **Limitações de recursos produtivos** disponíveis em cada período.  

O objetivo é atender toda a demanda, minimizando os custos totais de produção, setup e estoque, sem ultrapassar a capacidade produtiva disponível.

---

## 🎯 Enunciado do Problema

Definir o plano ótimo de produção para diferentes SKUs em um horizonte de 12 períodos, garantindo:  
- Atendimento integral da demanda.  
- Estoques finais conforme metas estabelecidas.  
- Custos totais mínimos, considerando produção, setup e estocagem.  
- Respeito às restrições de capacidade produtiva e perecibilidade.  

---

## 🧠 Descrição do Problema

Cada SKU possui:  
- **Demanda por período** (quantidade a ser atendida).  
- **Custos de setup** (quando há produção no período).  
- **Custos de estocagem** (para unidades mantidas em estoque).  
- **Consumo de recursos produtivos** (tempo ou capacidade por unidade produzida).  

O planejamento deve garantir que:  
- Toda demanda seja atendida no período correspondente.  
- Estoques sejam gerenciados corretamente, sem exceder limites de perecibilidade.  
- Custos totais sejam minimizados.  

Este problema é uma extensão do **Problema de Dimensionamento de Lotes Não Capacitado (ULS)**, incorporando **custos de setup** e **restrições de capacidade**, o que aumenta significativamente sua complexidade computacional.

---

## 🚚 Dados da Instância

### Parâmetros Gerais
- Número de produtos: 2  
- Número de períodos: 12  

### Demandas por período
| Período | Produto 1 | Produto 2 |
|---------|-----------|-----------|
| 1       | 185       | 210       |
| 2       | 250       | 0         |
| 3       | 0         | 165       |
| 4       | 120       | 0         |
| 5       | 175       | 330       |
| 6       | 210       | 0         |
| 7       | 0         | 0         |
| 8       | 0         | 240       |
| 9       | 180       | 55        |
| 10      | 260       | 70        |
| 11      | 0         | 120       |
| 12      | 140       | 0         |

### Recursos disponíveis por período

[100, 160, 120, 80, 80, 80, 120, 140, 160, 160, 160, 160]


### Parâmetros dos produtos
- Estoque inicial: `[300, 120]`  
- Estoque final desejado: `[300, 200]`  
- Custo de setup: `[500, 300]`  
- Custo de estoque: `[2, 3]`  
- Consumo de recursos por unidade: `[0.2, 0.4]`  

---

## 📚 Referências

- Wagner, H. M., Whitin, T. M. (1958). *Dynamic version of the economic lot size model*. Management Science, 5(1), 89–96.  
- Pochet, Y., Wolsey, L. A. (2006). *Production Planning by Mixed Integer Programming*. Springer.  

---

## 🚀 Possíveis Extensões

- Inclusão de restrições de **perecibilidade máxima** dos produtos.  
- Considerar **múltiplas linhas de produção** com setups distintos.  
- Integração com **planejamento de transporte**.  
- Aplicação de heurísticas e metaheurísticas:  
  - GRASP  
  - Algoritmos Genéticos  
  - Simulated Annealing  
  - Busca Tabu  


