# 👗 Problema de Escalonamento de Projetos via PERT/CPM – Lançamento de uma Coleção de Verão (Indústria de Confecção do Ceará)

## 📌 Descrição do Problema

Este repositório apresenta uma instância de grande porte do **Problema de Planejamento e Controle de Projetos via PERT/CPM (Program Evaluation and Review Technique / Critical Path Method)** aplicada ao ciclo completo de desenvolvimento e lançamento de uma **nova coleção de verão** de uma indústria de confecção sediada no estado do Ceará.

O objetivo principal é modelar o projeto como uma rede de atividades interdependentes — da concepção criativa da coleção até a produção em escala e o lançamento comercial — determinando a **duração esperada do projeto**, o **caminho crítico**, as **folgas (slacks)** de cada atividade e a **variabilidade** associada aos prazos, de modo a apoiar decisões de alocação de recursos, aceleração de atividades (*crashing*) e gestão de riscos de atraso.

---

## 🎯 Enunciado do Problema

Desenvolver e analisar métodos de resolução (cálculo determinístico via CPM, análise probabilística via PERT, nivelamento de recursos e técnicas de compressão de cronograma) para o **Problema de Planejamento do Lançamento de Coleção (Fashion Collection Launch Scheduling Problem – FCLSP)**, cobrindo as etapas de concepção, desenvolvimento de produto, suprimentos, produção fabril, marketing e distribuição, sob restrições de precedência entre atividades e de disponibilidade de equipes por departamento.

---

## 🌍 Dados da Instância de Grande Porte

A instância completa contendo **41 atividades**, organizadas em **6 fases do ciclo de vida do projeto** (Concepção e Pesquisa; Design e Desenvolvimento; Pré-Produção; Produção; Marketing e Preparação de Lançamento; Distribuição e Lançamento), encontra-se disponível na planilha **`Instancia_PERT_CPM_Colecao_Verao.xlsx`**.

Para cada atividade são fornecidas as três estimativas de tempo do PERT (otimista, mais provável e pessimista, em dias úteis), o custo estimado, a equipe necessária e as atividades predecessoras diretas, que definem a rede de precedências do projeto.

### Amostra dos Dados das Atividades

| ID | Nome da Atividade | Fase | Departamento | Predecessoras | Tempo Otimista (a) | Tempo Mais Provável (m) | Tempo Pessimista (b) | Custo (R$) | Equipe |
| :---: | :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| A1 | Pesquisa de tendências de moda | 1 - Concepção e Pesquisa | Criação | - | 5 | 8 | 12 | R$ 8.000,00 | 2 |
| A4 | Definição do conceito e tema da coleção | 1 - Concepção e Pesquisa | Criação | A1,A2,A3 | 3 | 5 | 8 | R$ 4.000,00 | 3 |
| A11 | Compra de tecidos | 2 - Design e Desenvolvimento | Suprimentos | A10 | 5 | 8 | 14 | R$ 180.000,00 | 1 |
| A17 | Aprovação final da coleção pela diretoria | 2 - Design e Desenvolvimento | Diretoria | A16 | 1 | 2 | 3 | R$ 1.000,00 | 4 |
| A24 | Costura e montagem das peças | 4 - Produção | Costura | A23 | 10 | 15 | 22 | R$ 90.000,00 | 20 |
| ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |
| A40 | Lançamento oficial da coleção | 6 - Distribuição e Lançamento | Diretoria | A35,A36,A37,A38,A39,A32,A33 | 1 | 1 | 2 | R$ 50.000,00 | 10 |
| **Total** | **41 atividades** | — | — | — | — | — | — | **R$ 892.500,00** | — |
---

## ⚙️ Métodos de Resolução Recomendados

Devido à quantidade de atividades, às múltiplas cadeias de precedência paralelas (desenvolvimento de produto, suprimentos e marketing correndo simultaneamente) e à incerteza nas estimativas de tempo, o problema pode ser resolvido com as seguintes técnicas:

- **CPM (Critical Path Method)**:
  - Construção do diagrama de rede (AON – Activity on Node).
  - Cálculo de passagem de ida (*forward pass*) e de volta (*backward pass*) para obter ES, EF, LS, LF.
  - Identificação do **caminho crítico** e das **folgas total e livre** de cada atividade.
- **PERT (Program Evaluation and Review Technique)**:
  - Cálculo do tempo esperado, da variância e do desvio-padrão de cada atividade a partir das três estimativas.
  - Estimativa da **probabilidade de concluir o projeto até uma data-alvo**, usando a aproximação Normal.
---

## 📚 Referências Bibliográficas

- Kerzner, H. (2017). *Project Management: A Systems Approach to Planning, Scheduling, and Controlling* (12th ed.). Wiley.
- Malcolm, D. G., Roseboom, J. H., Clark, C. E., & Fazar, W. (1959). *Application of a technique for research and development program evaluation*. Operations Research, 7(5), 646-669.
- Kelley, J. E., & Walker, M. R. (1959). *Critical-path planning and scheduling*. Proceedings of the Eastern Joint Computer Conference.
- Project Management Institute (PMI). (2021). *A Guide to the Project Management Body of Knowledge (PMBOK Guide)* (7th ed.).

---

## 🚀 Possíveis Extensões

- **Sequenciamento com Recursos Limitados (RCPSP)**: incorporar as restrições de equipe por departamento (coluna "Equipe Necessária"), de forma análoga a problemas de *flow shop* com recursos/trabalhadores limitados.
- **Múltiplas Coleções em Paralelo**: expandir o modelo para o planejamento simultâneo de coleções de verão e inverno, competindo pelos mesmos recursos de modelagem e produção.
- **Simulação de Monte Carlo**: substituir a aproximação Normal do PERT por simulação da duração do projeto, amostrando cada atividade em sua distribuição Beta.
- **Análise de Custo x Prazo (Time-Cost Trade-off)**: modelar formalmente o problema de *crashing* como um programa de otimização, minimizando o custo total de aceleração para atingir uma data de lançamento desejada (ex.: antes do verão comercial).
- **Riscos Climáticos e Logísticos Regionais**: considerar variabilidade adicional em atividades de transporte e distribuição sujeitas às condições logísticas do Ceará (ex.: prazos de fornecedores, sazonalidade turística).

---

## 🎥 Vídeo Explicativo e Simulação

[![Vídeo demonstrando o Problema de Planejamento de Projetos via PERT/CPM aplicado ao lançamento de uma coleção de verão.](Link do Vídeo no Youtube)](https://youtu.be/XXXXXXXXX)
