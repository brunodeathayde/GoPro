# 🚚 Vehicle Routing Problem with Simultaneous Pickup and Delivery (VRPSPD)

## 📌 Descrição

Este repositório apresenta uma instância real do **Vehicle Routing Problem with Simultaneous Pickup and Delivery (VRPSPD)** aplicada ao balanceamento operacional de uma empresa de patinetes elétricos compartilhados.

O objetivo é determinar rotas ótimas para uma frota de caminhões responsáveis simultaneamente por:

- Coletar patinetes de estações com excesso de veículos.
- Entregar patinetes em estações com falta de veículos.

Minimizando a distância total percorrida e respeitando a capacidade dos caminhões.

---

## 🎯 Objetivo

Encontrar o conjunto de rotas que:

- Atenda todos os estacionamentos.
- Respeite a capacidade máxima dos caminhões.
- Minimize a distância total.
- Inicie e termine no depósito central.

---

## 🛴 Estudo de Caso

Empresa de compartilhamento de patinetes elétricos.

### Dados Operacionais

| Parâmetro | Valor |
|------------|---------|
| Estacionamentos | 350 |
| Capacidade dos caminhões | 50 patinetes |
| Depósito | 1 |
| Distância | Haversine |
| Problema | VRPSPD |

---

## 🧠 Formulação do Problema

Cada estacionamento é representado por um nó:

- Demanda > 0 → Necessita receber patinetes
- Demanda < 0 → Possui excesso para coleta
- Demanda = 0 → Balanceado

Os caminhões podem realizar simultaneamente:

- Coletas
- Entregas

durante uma mesma rota.

---


### Metaheurísticas

- Simulated Annealing
- Genetic Algorithm
- Tabu Search

---

## 📈 Função Objetivo

Minimizar

```

Σ distância percorrida por todas as rotas

```

sujeito a:

- Todo estacionamento visitado exatamente uma vez.
- Capacidade do caminhão ≤ 50.
- Início e retorno ao depósito.

---
## 🎥 Vídeo explicativo

https://img.youtube.com/vi/WymIjVsPimQ/maxresdefault.jpg](https://youtu.be/WymIjVsPimQ)

> *Vídeo demonstrando a aplicação do Vehicle Routing Problem with Simultaneous Pickup and Delivery (VRPSPD) para o balanceamento operacional de uma frota de patinetes elétricos compartilhados.*
