# 🚚 Problema de Roteamento de Veículos Capacitado – Instância Real

📌 **Descrição do Problema**

Este repositório apresenta uma instância real do **Capacitated Vehicle Routing Problem (CVRP)**, baseada em um cenário com múltiplos clientes e demandas específicas, atendidos por uma frota de veículos com capacidade limitada.  

O objetivo é determinar as rotas que minimizam a distância total percorrida, garantindo que cada cliente seja atendido exatamente uma vez e que nenhuma rota exceda a capacidade dos veículos.

---

🎯 **Enunciado do Problema**

Definir o conjunto ótimo de rotas para uma frota de veículos que parte de um depósito central, atende todos os clientes com suas respectivas demandas e retorna ao depósito, respeitando as restrições de capacidade.

---

🧠 **Descrição do Problema**

- Cada cliente é representado como um nó do grafo.  
- As arestas correspondem às distâncias geodésicas entre pares de locais (calculadas pela fórmula de Haversine).  
- O planejamento deve garantir:  
  - Todos os clientes sejam atendidos exatamente uma vez.  
  - Nenhum veículo ultrapasse sua capacidade máxima.  
  - O percurso seja fechado (volta ao depósito).  
  - A distância total seja minimizada.  

Este problema é **NP-difícil**, e para instâncias maiores apenas heurísticas e metaheurísticas são viáveis.

---

🌍 **Dados da Instância**

A instância completa está disponível em `data/cvrp_instance.csv`.

---

⚙️ **Métodos de Resolução**

- Força Bruta – inviável para instâncias grandes.  
- Held–Karp – solução exata até ~25 clientes.  
- Vizinho Mais Próximo – heurística rápida, mas não ótima.  
- 2-opt – remove cruzamentos e melhora soluções heurísticas.  
- Metaheurísticas: GRASP, Algoritmos Genéticos, Simulated Annealing, Busca Tabu.  
- Algoritmos híbridos como o **hGWOAM** (Gray Wolf + Whale Optimization), conforme artigo de referência.  

---

📚 **Referências**

- Pham, V. H. S., Nguyen, V. N., & Nguyen Dang, N. T. (2025). *Applying a Hybrid Gray Wolf‐Enhanced Whale Optimization Algorithm to the Capacitated Vehicle Routing Problem*. Journal of Advanced Transportation.  
- Lawler, E. L., Lenstra, J. K., Rinnooy Kan, A. H. G., Shmoys, D. B. (1985). *The Traveling Salesman Problem: A Guided Tour of Combinatorial Optimization*. Wiley.  
- Applegate, D. L., Bixby, R. E., Chvátal, V., Cook, W. J. (2006). *The Traveling Salesman Problem: A Computational Study*. Princeton University Press.  
