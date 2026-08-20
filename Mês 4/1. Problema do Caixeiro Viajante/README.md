# 🧳 Problema do Caixeiro Viajante – Instância Real (Capitais Brasileiras)

## 📌 Descrição do Problema

Este repositório apresenta uma instância real do **Problema do Caixeiro Viajante (Travelling Salesman Problem – TSP)**, baseada em um cenário de **15 capitais brasileiras**.  

O problema consiste em determinar a rota mais curta que visita todas as cidades exatamente uma vez e retorna ao ponto inicial, minimizando a distância total percorrida.

---

## 🎯 Enunciado do Problema

Definir a rota ótima de um caixeiro viajante que deve visitar 15 capitais brasileiras, retornando ao ponto de partida, com base nas distâncias geodésicas (fórmula de Haversine).

---

## 🧠 Descrição do Problema

Cada cidade representa um nó do grafo.  
As arestas correspondem às distâncias geodésicas entre pares de cidades.  

O planejamento deve garantir que:
- Todas as cidades sejam visitadas exatamente uma vez.
- O percurso seja fechado (volta ao ponto inicial).
- A distância total seja minimizada.

Este problema é **NP-difícil**, e para instâncias maiores apenas heurísticas e metaheurísticas são viáveis.

---

## 🌍 Dados da Instância

| Cidade        | Latitude  | Longitude |
|---------------|-----------|-----------|
| Brasília      | -15.7801  | -47.9292  |
| São Paulo     | -23.5489  | -46.6388  |
| Rio de Janeiro| -22.9035  | -43.2096  |
| Belo Horizonte| -19.9208  | -43.9378  |
| Salvador      | -12.9711  | -38.5108  |
| Fortaleza     | -3.7172   | -38.5433  |
| Recife        | -8.0539   | -34.8811  |
| Porto Alegre  | -30.0331  | -51.23    |
| Curitiba      | -25.4278  | -49.2731  |
| Manaus        | -3.1019   | -60.025   |
| Belém         | -1.4558   | -48.4902  |
| Goiânia       | -16.6786  | -49.2539  |
| Vitória       | -20.3155  | -40.3128  |
| Natal         | -5.795    | -35.2094  |
| Maceió        | -9.6658   | -35.7353  |

---

## ⚙️ Métodos de Resolução

- **[Força Bruta](ca://s?q=Forca_bruta_TSP)** – inviável para \(n>10\).  
- **[Held–Karp](ca://s?q=Programacao_dinamica_Held-Karp)** – solução exata até ~25 cidades.  
- **[Vizinho Mais Próximo](ca://s?q=Heuristica_vizinho_mais_proximo)** – heurística rápida, mas não ótima.  
- **[2-opt](ca://s?q=Algoritmo_2-opt)** – remove cruzamentos e melhora soluções heurísticas.  
- **Metaheurísticas**: [GRASP](ca://s?q=GRASP_TSP), [Algoritmos Genéticos](ca://s?q=Algoritmos_geneticos_TSP), [Simulated Annealing](ca://s?q=Simulated_Annealing_TSP), [Busca Tabu](ca://s?q=Busca_Tabu_TSP).

---

## 📚 Referências

- Lawler, E. L., Lenstra, J. K., Rinnooy Kan, A. H. G., Shmoys, D. B. (1985). *The Traveling Salesman Problem: A Guided Tour of Combinatorial Optimization*. Wiley.  
- Applegate, D. L., Bixby, R. E., Chvátal, V., Cook, W. J. (2006). *The Traveling Salesman Problem: A Computational Study*. Princeton University Press.

---

## 🎥 Vídeo explicativo

[![Assista ao vídeo no YouTube](https://img.youtube.com/vi/nPo4UnaO9Qs/maxresdefault.jpg)](https://youtu.be/nPo4UnaO9Qs)

> *Vídeo demonstrando o problema do caixeiro viajante e suas aplicações reais.*

---

## 🚀 Possíveis Extensões

- Inclusão de **restrições de tempo de entrega** (TSP com janelas de tempo).  
- Considerar **custos variáveis de transporte** (combustível, pedágios).  
- Integração com **planejamento logístico urbano**.  
- Aplicação em **roteirização de entregas** e **planejamento turístico**.  


