# 📦 Problema de Carregamento de Contêineres – Instância Real (Transporte Rodoviário)

## 📌 Descrição do Problema

Este repositório apresenta uma instância do **Problema de Carregamento de Contêineres (Container Loading Problem – CLP)**, baseada em um cenário real de transporte rodoviário de cargas.

O problema consiste em determinar como alocar caixas retangulares dentro de um caminhão, respeitando restrições físicas e operacionais, de modo a **otimizar o uso do espaço e/ou atender critérios logísticos (como destinos distintos)**.

---

## 🎯 Enunciado do Problema

Determinar como carregar um conjunto de caixas em um caminhão, respeitando suas dimensões e capacidade de peso, de forma a acomodar o maior número possível de itens (ou toda a demanda), considerando também possíveis restrições de destino.

---

## 🧠 Descrição do Problema

O problema consiste em organizar o carregamento de diferentes tipos de caixas dentro de um caminhão com espaço limitado.

Cada tipo de caixa possui:
- dimensões específicas (comprimento, largura e altura);  
- peso individual;  
- quantidade disponível para transporte;  
- destino associado (por exemplo, A ou B).

O caminhão possui:
- dimensões fixas (comprimento, largura e altura);  
- capacidade máxima de peso.

As caixas devem ser alocadas dentro do caminhão de forma que:
- não haja sobreposição entre caixas;  
- todas as caixas estejam completamente dentro do espaço disponível;  
- o peso total carregado não ultrapasse a capacidade máxima do caminhão.

Além disso, podem existir restrições logísticas, como:
- separação de cargas por destino;  
- facilidade de descarregamento (ex: caixas de um destino devem estar mais acessíveis).

O objetivo pode variar conforme a aplicação, incluindo:
- maximizar o número de caixas transportadas;  
- maximizar o volume ocupado;  
- ou garantir o atendimento completo da demanda com o menor número de viagens.

Este problema é uma extensão tridimensional do problema da mochila e é conhecido por sua alta complexidade computacional.

---

## 🚚 Dados da Instância

### Caminhão

- **Dimensões:** 6,0 m × 2,4 m × 2,6 m  
- **Capacidade máxima:** 7.000 kg  

---

### Itens (Caixas)

| Tipo | Quantidade | Dimensões (cm) | Peso (kg) | Destino |
|------|-----------|----------------|-----------|---------|
| 1    | 11        | 60 x 40 x 40   | 142       | A       |
| 2    | 6         | 60 x 40 x 40   | 110       | A       |
| 3    | 22        | 60 x 30 x 40   | 222       | B       |
| 4    | 217       | 50 x 36 x 32   | 3625      | B       |
| 5    | 45        | 60 x 30 x 40   | 495       | B       |
| 6    | 6         | 60 x 40 x 40   | 90        | B       |
| 7    | 2         | 60 x 40 x 30   | 24        | B       |
| 8    | 15        | 71 x 40 x 38   | 225       | B       |
| 9    | 15        | 73 x 35 x 33   | 170       | B       |
| 10   | 22        | 60 x 40 x 40   | 305       | B       |
| 11   | 20        | 64 x 35 x 52,5 | 360       | B       |

---

## 📚 Referências

- Correia, M. H., Gomes, A. M., Oliveira, J. F., Ferreira, J. S. (1992).  
  *Problemas de empacotamento tridimensional*.  
  Investigação Operacional, v. 12, p. 169–180.

---

## 🚀 Possíveis Extensões

- Múltiplos caminhões (Multiple Container Loading Problem)  
- Restrições de empilhamento e fragilidade  
- Integração com roteamento de veículos (VRP + CLP)  
- Heurísticas e metaheurísticas:
  - GRASP  
  - Algoritmos Genéticos  
  - Simulated Annealing  
  - Busca Tabu  
