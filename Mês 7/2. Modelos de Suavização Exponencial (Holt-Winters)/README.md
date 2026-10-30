# 🏥 Previsão de Demanda de Pacientes em uma UPA — Modelos de Suavização Exponencial (Holt-Winters)

## 📌 Descrição do Problema

Este repositório apresenta uma instância de **previsão de demanda diária de pacientes** em uma unidade  de pronto atendimento (UPA) situada na **Região Metropolitana de Fortaleza, Ceará**. O problema está relacionado ao planejamento e dimensionamento da capacidade assistencial: estimar quantos pacientes poderão chegar à unidade e como esse volume se distribui entre categorias de criticidade.

A previsão por categoria pode apoiar o planejamento de escalas de equipes, salas e consultórios, capacidade de triagem, disponibilidade de insumos e organização dos recursos ao longo dos dias da semana. O estudo pode utilizar **Modelos de Suavização Exponencial de Holt-Winters**, que representam nível, tendência e um padrão sazonal recorrente.

---

## 🎯 Enunciado do Problema

Desenvolver, ajustar e avaliar modelos de previsão de séries temporais para estimar o número de pacientes que chegarão diariamente à unidade em cada uma das cinco categorias operacionais: **emergência, muito urgente, urgência, menos graves e leves**. Os resultados devem ajudar a responder perguntas de planejamento como:

- Qual é a demanda diária esperada para cada categoria nos próximos 7, 14 ou 28 dias?
- Há diferenças sistemáticas entre dias úteis e finais de semana?
- Um modelo Holt-Winters com sazonalidade semanal melhora o erro em relação a uma versão sem sazonalidade ou a uma previsão ingênua sazonal?
- Como a incerteza das previsões deve ser considerada no dimensionamento da capacidade e na criação de margens de segurança?

O desafio consiste em comparar alternativas de suavização exponencial e justificar a configuração escolhida com base no conjunto de teste, no comportamento da série e no objetivo operacional.

---

## 🌍 Dados da Instância

A instância está disponível em **`Instancia_Pacientes_UPA_Holt_Winters.xlsx`** e contém 731 observações diárias, de **01/01/2024 a 31/12/2025**, distribuídas em cinco categorias. A planilha também traz uma versão em formato longo, dicionário de dados, instruções e um painel com estatísticas descritivas e gráficos.

### Categorias de pacientes

| Variável | Categoria didática | Cor indicativa | Utilização operacional ilustrativa |
| :--- | :--- | :--- | :--- |
| `Emergencia` | Emergência | Vermelho | Estimar o volume da categoria de maior criticidade. |
| `Muito_Urgente` | Muito urgente | Laranja | Apoiar o planejamento para pacientes que demandam atenção rápida. |
| `Urgencia` | Urgência | Amarelo | Estimar a demanda de casos classificados como urgentes. |
| `Menos_Graves` | Menos graves | Verde | Apoiar a previsão de casos de menor prioridade relativa. |
| `Leves` | Leves | Azul | Estimar atendimentos de menor complexidade no cenário didático. |

As cores são apenas indicativas. A classificação formal deve seguir o protocolo institucional e ser realizada por profissionais habilitados. Protocolos podem adotar nomes, quantidade de níveis e critérios específicos.

### Amostra dos dados diários

A tabela abaixo apresenta os primeiros registros da série sintética:

| Data | Dia da semana | Emergência | Muito urgente | Urgência | Menos graves | Leves | Total de pacientes |
| :---: | :--- | ---: | ---: | ---: | ---: | ---: | ---: |
| 01/01/2024 | Segunda-feira | 11 | 21 | 35 | 60 | 47 | 174 |
| 02/01/2024 | Terça-feira | 9 | 15 | 34 | 61 | 34 | 153 |
| 03/01/2024 | Quarta-feira | 9 | 16 | 26 | 53 | 42 | 146 |
| 04/01/2024 | Quinta-feira | 8 | 18 | 31 | 52 | 37 | 146 |
| 05/01/2024 | Sexta-feira | 9 | 22 | 35 | 49 | 40 | 155 |

### Estatísticas descritivas do período

| Categoria | Média (pacientes/dia) | Mínimo diário | Máximo diário | Total no período |
| :--- | ---: | ---: | ---: | ---: |
| Emergência | 9,9 | 6 | 14 | 7.216 |
| Muito urgente | 18,3 | 12 | 26 | 13.392 |
| Urgência | 34,8 | 23 | 50 | 25.443 |
| Menos graves | 47,5 | 22 | 74 | 34.707 |
| Leves | 37,2 | 14 | 62 | 27.162 |
| **Total de pacientes** | **147,6** | — | — | **107.920** |

### Organização do arquivo Excel

- **`Leia_Me`**: contexto, período, divisão treino/teste e observações de uso.
- **`Serie_Diaria`**: uma linha por dia, com uma coluna para cada categoria e o total diário. É a aba recomendada para importar os dados no Python.
- **`Dados_Longos`**: uma linha por data e categoria, útil para filtros, análises e tabelas dinâmicas.
- **`Dicionario`**: explicação das variáveis e limitações dos dados.
- **`Painel`**: médias, máximos, mínimos, totais e gráficos de evolução temporal.

---

## Métricas de avaliação das previsões

- **MAE (Mean Absolute Error)**: erro absoluto médio em pacientes/dia, simples de interpretar operacionalmente.
- **RMSE (Root Mean Squared Error)**: penaliza mais fortemente erros maiores, útil quando picos de demanda têm impacto elevado.
- **WAPE (Weighted Absolute Percentage Error)**: soma dos erros absolutos dividida pelo total observado, expressa em porcentagem.

Compare também os resultados com uma previsão ingênua sazonal: para cada dia do teste, usar como previsão o valor observado no mesmo dia da semana da semana anterior. A avaliação deve ser realizada por categoria, pois erros semelhantes em números absolutos podem ter impactos distintos dependendo da criticidade.

---

## 📚 Referências Bibliográficas

- Winters, P. R. (1960). *Forecasting sales by exponentially weighted moving averages*. **Management Science, 6**(3), 324–342.
- Hyndman, R. J., & Athanasopoulos, G. *Forecasting: Principles and Practice* — capítulo sobre suavização exponencial. Disponível em: https://otexts.robjhyndman.com/fpp2/exponential-smoothing.html
- `statsmodels`. *ExponentialSmoothing — Holt Winter’s Exponential Smoothing*. Documentação da API: https://www.statsmodels.org/stable/generated/statsmodels.tsa.holtwinters.ExponentialSmoothing.html
- Secretaria da Saúde do Estado da Bahia (SESAB). *Classificação de Risco* — descrição geral de categorias de criticidade em serviços de urgência: https://www.ba.gov.br/saude/atencao-a-saude/comofuncionaosus/classificacaoderisco
- Secretaria Municipal da Saúde de Fortaleza — SAMU. *Acolhimento e Classificação de Risco*: https://samu.fortaleza.ce.gov.br/index.php/auxilio-a-regulacao-medica/408-acolhimento-e-classificacao-de-risco
- Ministério da Saúde. *Acolhimento e classificação de risco nos serviços de urgência*. Biblioteca Virtual em Saúde: https://bvsms.saude.gov.br/bvs/publicacoes/acolhimento_classificaao_risco_servico_urgencia.pdf

---

## 🚀 Possíveis Extensões

- **Comparação aditivo versus multiplicativo**: comparar desempenho no teste para cada categoria, usando os próprios dados de teste.
- **Validação temporal deslizante (*rolling-origin*)**: avaliar robustez em diferentes janelas e horizontes.
- **Sazonalidade dupla**: combinar ciclo semanal com padrões anuais ou períodos especiais. O Holt-Winters clássico configura um período sazonal por vez; modelos de múltiplas sazonalidades ou regressões com variáveis de calendário podem ser mais adequados para capturar ambos.
- **Efeitos de calendário**: incluir feriados, férias, eventos locais e dias úteis, desde que haja dados confiáveis e disponíveis antes da previsão.
- **Previsões probabilísticas e capacidade**: construir intervalos de previsão e transformar cenários em regras de dimensionamento com margem de segurança.
- **Desagregação por turno**: ampliar a série diária para horas ou turnos, quando a base de dados permitir.
- **Modelos comparativos**: comparar Holt-Winters com SARIMA, regressão com variáveis de calendário, modelos de contagem e métodos de aprendizado de máquina.

---

## 🎥 Material Explicativo e Simulação

Sugestão de atividade: definir períodos de teste e treino, executar o exemplo para as cinco categorias, comparar erros e gráficos do período de teste e produzir uma recomendação de planejamento para as próximas duas semanas. Um recurso de aula ou vídeo pode ser adicionado aqui:

![Vídeo explicativo sobre Holt-Winters e previsão de demanda diária](Link do vídeo no YouTube)(https://youtu.be/XXXXXXXXX)
