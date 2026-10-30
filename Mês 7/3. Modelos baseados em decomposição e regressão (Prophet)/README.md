# 🚓 Previsão de Demanda de Ligações ao 190 (Fortaleza-CE) — Modelos de Decomposição e Regressão (Prophet)

## 📌 Descrição do Problema

Este repositório apresenta uma instância de **previsão de demanda diária de ligações ao número de emergência de segurança 190** na cidade de **Fortaleza, Ceará**. O problema está relacionado ao planejamento e ao dimensionamento da capacidade das unidades de segurança: estimar quantas ocorrências serão acionadas por telefone e como esse volume se distribui entre diferentes tipos de intercorrência.

A previsão por tipo de ocorrência pode apoiar a definição de escalas de atendentes e despachantes da central, o dimensionamento de viaturas e efetivo por turno, a distribuição de recursos entre dias da semana e períodos especiais (feriados, Carnaval, Réveillon) e a antecipação de picos de demanda. O estudo utiliza o **Prophet**, um modelo de séries temporais baseado em **decomposição** (tendência + sazonalidades + feriados) com **regressão** sobre variáveis externas.

---

## 🎯 Enunciado do Problema

Desenvolver, ajustar e avaliar modelos de previsão de séries temporais para estimar o número de ligações diárias ao 190 em cada uma das três categorias operacionais: **crimes contra a vida, crimes contra o patrimônio e perturbação da ordem pública**. Os resultados devem ajudar a responder perguntas de planejamento como:

- Qual é a demanda diária esperada para cada categoria nos próximos 7, 14, 28 ou 90 dias?
- Quais são os padrões semanais e anuais de cada categoria? Os fins de semana diferem dos dias úteis?
- Qual é o efeito de feriados e datas especiais (Carnaval, Natal, Réveillon) sobre cada categoria?
- A tendência mudou ao longo do período? Onde o Prophet detecta pontos de mudança?
- Regressores externos (dia de pagamento, chuva) melhoram o erro no conjunto de teste?
- Como a incerteza das previsões deve ser considerada no dimensionamento da capacidade e na criação de margens de segurança?

O desafio consiste em comparar configurações do Prophet (modo de sazonalidade aditivo ou multiplicativo, feriados, regressores, flexibilidade da tendência) e justificar a configuração escolhida com base no conjunto de teste, na análise dos componentes e no objetivo operacional.

---

## 🌍 Dados da Instância

A instância está disponível em **`Instancia_Ligacoes_190_Fortaleza_Prophet.xlsx`** e contém 1.096 observações diárias, de **01/01/2023 a 31/12/2025**, para três categorias. A planilha também traz uma versão em formato longo (`ds`, `y`), a tabela de feriados no formato exigido pelo Prophet, dicionário de dados e um painel com estatísticas descritivas e gráficos.

> ⚠️ **Os dados são sintéticos e didáticos.** Não representam estatísticas oficiais da Secretaria da Segurança Pública e Defesa Social do Ceará (SSPDS-CE), da CIOPS ou de qualquer outro órgão. 

### Categorias de ocorrência

| Variável | Categoria | Cor indicativa | Utilização operacional ilustrativa |
| :--- | :--- | :--- | :--- |
| `Crimes_Vida` | Crimes contra a vida | Vermelho | Estimar o volume da categoria de maior gravidade (ex.: homicídios e tentativas, disparos de arma de fogo). |
| `Crimes_Patrimonio` | Crimes contra o patrimônio | Laranja | Apoiar o planejamento do policiamento ostensivo para roubos, furtos e danos. |
| `Perturbacao_Ordem` | Perturbação da ordem pública | Azul | Estimar a demanda de som alto, brigas, desordem e aglomerações. |

Os exemplos de crimes entre parênteses são ilustrativos. As cores são apenas indicativas.

### Amostra dos dados diários

A tabela abaixo apresenta os primeiros registros da série sintética:

| Data | Dia da semana | Crimes contra a vida | Crimes contra o patrimônio | Perturbação da ordem | Total de ligações |
| :---: | :--- | ---: | ---: | ---: | ---: |
| 01/01/2023 | Domingo (Confraternização Universal) | 21 | 102 | 355 | 478 |
| 02/01/2023 | Segunda-feira | 24 | 160 | 211 | 395 |
| 03/01/2023 | Terça-feira | 21 | 148 | 197 | 366 |
| 04/01/2023 | Quarta-feira | 19 | 170 | 165 | 354 |
| 05/01/2023 | Quinta-feira | 18 | 126 | 269 | 413 |

### Estatísticas descritivas do período

| Categoria | Média (ligações/dia) | Mínimo diário | Máximo diário | Total no período |
| :--- | ---: | ---: | ---: | ---: |
| Crimes contra a vida | 18,8 | 5 | 39 | 20.603 |
| Crimes contra o patrimônio | 141,1 | 72 | 245 | 154.613 |
| Perturbação da ordem pública | 258,6 | 127 | 478 | 283.391 |
| **Total de ligações** | **418,4** | — | — | **458.607** |

### Padrões embutidos na instância

- **Sazonalidade semanal**: crimes contra a vida e perturbação da ordem concentram-se de sexta a domingo; crimes contra o patrimônio têm pico na sexta-feira e vale no domingo.
- **Sazonalidade anual**: ciclos suaves, com mais ocorrências no fim e no início do ano.
- **Mudança de tendência** em meados de 2024: queda dos crimes contra a vida, queda seguida de recuperação nos crimes contra o patrimônio e crescimento contínuo da perturbação da ordem.
- **Feriados e datas especiais**: Carnaval e Réveillon elevam a perturbação da ordem e os crimes contra a vida; no patrimônio, o efeito é de queda.
- **Regressores**: dias 5 a 7 do mês (proxy de pagamento) elevam ligeiramente patrimônio e ordem pública; a chuva reduz ligeiramente essas duas categorias.
- **Variância acima de Poisson** (sobredispersão) e **anomalias documentadas** (pico em 10/11/2024 na perturbação da ordem; queda em 17 e 18/05/2025 nos crimes contra o patrimônio).

### Organização do arquivo Excel

- **`Leia_Me`**: contexto, período, divisão treino/teste, aviso sobre dados sintéticos e legenda de cores.
- **`Serie_Diaria`**: uma linha por dia, com as três categorias, o total diário (fórmula), indicador de feriado, dia de pagamento, chuva (mm) e conjunto (treino/teste). Aba recomendada para importar os dados no Python.
- **`Dados_Longos`**: formato `ds`, `y`, `categoria`, `conjunto`, útil para ajustar um modelo por categoria em um laço.
- **`Feriados`**: tabela com colunas `holiday`, `ds`, `lower_window`, `upper_window` (formato do parâmetro `holidays` do Prophet), cobrindo 2023 a 2026 para permitir previsões futuras.
- **`Dicionario`**: explicação das variáveis, anomalias e limitações dos dados.
- **`Painel`**: estatísticas descritivas, médias por dia da semana, comparação feriado versus dia comum, parâmetros de dimensionamento editáveis e gráficos.

---

## Métricas de avaliação das previsões

- **MAE (Mean Absolute Error)**: erro absoluto médio em ligações/dia, simples de interpretar operacionalmente.
- **RMSE (Root Mean Squared Error)**: penaliza mais fortemente erros maiores, útil quando picos de demanda têm impacto elevado na central.
- **WAPE (Weighted Absolute Percentage Error)**: soma dos erros absolutos dividida pelo total observado, em porcentagem; adequado quando há valores pequenos (como crimes contra a vida) que distorcem o MAPE.
- **Viés (bias)**: média de `previsto − observado`, para verificar subestimação sistemática, que pode levar a subdimensionamento.
- **Cobertura do intervalo de previsão**: proporção de dias do teste dentro do intervalo de 80% (`yhat_lower`, `yhat_upper`), para checar se a incerteza está bem calibrada.

Compare também com uma **previsão ingênua sazonal**: para cada dia do teste, usar o valor observado no mesmo dia da semana da semana anterior. A avaliação deve ser feita por categoria, pois erros semelhantes em números absolutos têm impactos distintos conforme a gravidade da ocorrência.

---

## 📚 Referências Bibliográficas

- Taylor, S. J., & Letham, B. (2018). *Forecasting at scale*. **The American Statistician, 72**(1), 37–45.
- Documentação oficial do Prophet (Quick Start, holidays, regressores, diagnostics): https://facebook.github.io/prophet/docs/quick_start.html
- Hyndman, R. J., & Athanasopoulos, G. *Forecasting: Principles and Practice* — capítulos sobre decomposição de séries temporais e avaliação de previsões. Disponível em: https://otexts.com/fpp3/
- Cleveland, R. B., Cleveland, W. S., McRae, J. E., & Terpenning, I. (1990). *STL: A seasonal-trend decomposition procedure based on Loess*. **Journal of Official Statistics, 6**(1), 3–73.
- Secretaria da Segurança Pública e Defesa Social do Ceará (SSPDS-CE). Portal institucional e estatísticas oficiais: https://www.sspds.ce.gov.br

> Verifique as referências e os links antes de usar em material didático ou científico.

---

## 🚀 Possíveis Extensões

- **Comparação aditivo versus multiplicativo**: comparar desempenho no teste para cada categoria; contagens com nível crescente costumam favorecer o modo multiplicativo.
- **Ajuste de hiperparâmetros**: `changepoint_prior_scale`, `seasonality_prior_scale`, `holidays_prior_scale` e `fourier_order`, por validação cruzada temporal (`cross_validation`).
- **Validação temporal deslizante (*rolling-origin*)**: avaliar robustez em diferentes janelas e horizontes.
- **Tratamento de anomalias**: remover os pontos atípicos (definindo `y = NaN`) ou modelá-los como eventos, e comparar o erro.
- **Regressores externos**: incluir chuva (exige previsão meteorológica), eventos de grande público, jogos de futebol e datas de pagamento, desde que estejam disponíveis antes da previsão.
- **Sazonalidades adicionais**: sazonalidade mensal customizada via `add_seasonality`.
- **Previsões probabilísticas e capacidade**: transformar `yhat_upper` e cenários em regras de dimensionamento (operadores, viaturas) com margem de segurança.
- **Modelos de contagem**: como o `y` é uma contagem, comparar com regressão de Poisson ou binomial negativa e com a transformação `log1p`.
- **Desagregação**: ampliar a série para horas, turnos ou áreas integradas de segurança, quando a base permitir.
- **Modelos comparativos**: comparar o Prophet com Holt-Winters, SARIMA, regressão com variáveis de calendário e métodos de aprendizado de máquina.

---

## 🎥 Material Explicativo e Simulação

Sugestão de atividade: definir períodos de treino e teste, ajustar um Prophet para cada uma das três categorias, analisar os componentes (tendência, semana, ano, feriados), comparar erros e gráficos do período de teste e produzir uma recomendação de dimensionamento para as próximas quatro semanas.

![Vídeo explicativo sobre Prophet e previsão de demanda diária](Link do vídeo no YouTube)(https://youtu.be/XXXXXXXXX)
