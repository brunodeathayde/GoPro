# 📈 Previsão de Demanda em uma indústria alimentícia – Séries Temporais com ARIMA, SARIMA e suas variações

## 📌 Descrição do Problema

Este repositório apresenta uma instância de previsão de demanda aplicada ao **Planejamento e Controle da Produção (PCP)** de uma empresa do setor alimentício. A empresa atende supermercados, mercadinhos e distribuidores no estado do Ceará e precisa estimar a demanda mensal de diferentes famílias de produtos para planejar a produção, a compra de matérias-primas e embalagens, os estoques e a capacidade produtiva.

O objetivo é construir modelos de séries temporais, em especial **ARIMA** (*AutoRegressive Integrated Moving Average*) e suas variações que considerem sazonalidade como os Modelos sazonais (**SARIMA**) que representam explicitamente padrões que se repetem a cada 12 meses, para produzir previsões por família de produto. Uma previsão confiável ajuda a reduzir tanto o risco de falta de produto quanto o excesso de estoque, mas deve ser avaliada continuamente com dados observados e conhecimento do processo de negócio.

---

## 🎯 Enunciado do Problema

Desenvolver, ajustar e avaliar modelos de previsão da demanda mensal para pelo menos três famílias de produtos alimentícios. Para cada série, deve-se explorar tendência e sazonalidade, estimar parâmetros ARIMA, selecionar uma especificação com base em critérios estatísticos e avaliar a precisão em um período de teste posterior ao período de treinamento.

As previsões devem ser interpretadas no contexto do PCP, respondendo a questões como: **quanto produzir nos próximos meses e quais famílias exigem maior capacidade?**.

---

## 🌍 Dados da Instância

A instância está disponível na planilha **`Instancia_Previsao_Demanda_ARIMA.xlsx`** e contém **60 observações mensais por família**, de janeiro de 2021 a dezembro de 2025. São quatro famílias e 240 registros no formato longo.

| Família | Nome da série no Excel | Unidade | Padrão de demanda observado |
| :--- | :--- | :--- | :--- |
| Biscoitos e snacks | `Biscoitos_Snacks` | Caixas/mês | Crescimento moderado, com aumento no fim do ano |
| Massas secas | `Massas_Secas` | Caixas/mês | Demanda relativamente estável e elevação no período de festas |
| Molhos e conservas | `Molhos_Conservas` | Caixas/mês | Maior demanda no verão e no fim do ano |
| Farinhas e misturas | `Farinhas_Misturas` | Caixas/mês | Picos  em períodos associados a festas e preparações domésticas |

### Amostra dos dados (primeiros cinco meses)

| Mês | Biscoitos e snacks | Massas secas | Molhos e conservas | Farinhas e misturas |
| :--- | ---: | ---: | ---: | ---: |
| 01/2021 | 11.306 | 8.384 | 7.026 | 6.897 |
| 02/2021 | 11.407 | 8.148 | 6.251 | 6.970 |
| 03/2021 | 12.397 | 7.738 | 6.275 | 7.671 |
| 04/2021 | 10.831 | 8.602 | 6.013 | 7.402 |
| 05/2021 | 12.531 | 8.472 | 6.029 | 6.907 |

A planilha organiza os dados em quatro abas:

- **`Instrucoes`**: contexto do problema, objetivo e roteiro sugerido.
- **`Serie_Mensal`**: formato largo, com uma linha por mês e uma coluna por família. Inclui um gráfico comparativo.
- **`Dados_Longos`**: formato tabular, com uma linha para cada combinação de mês e família, adequado a filtros, visualizações e análises agrupadas.
- **`Dicionario`**: definição dos campos, unidades e observações.
---

## 📚 Referências e Documentação

- Hyndman, R. J., Athanasopoulos, G., Garza, A., Challu, C., Mergenthaler, M., & Olivares, M. K. **Forecasting: Principles and Practice, the Pythonic Way**. Livro on-line. Disponível em: https://otexts.com/fpppy/
- Box, G. E. P., Jenkins, G. M., Reinsel, G. C., & Ljung, G. M. **Time Series Analysis: Forecasting and Control**. 5. ed. Wiley, 2015.
- Statsmodels Developers. **`statsmodels.tsa.arima.model.ARIMA` — documentação da API**. Disponível em: https://www.statsmodels.org/stable/generated/statsmodels.tsa.arima.model.ARIMA.html

---

## 🚀 Possíveis Extensões

- **Comparação com modelos de referência**: último valor, média móvel, suavização exponencial e tendência sazonal ingênua.
- **Validação temporal**: testar várias janelas históricas, em vez de apenas uma separação treino/teste.
- **Variáveis explicativas (ARIMAX/SARIMAX)**: incluir preço, promoções, calendário, feriados ou indicadores comerciais, desde que disponíveis no momento da previsão.
- **Previsão hierárquica**: reconciliar previsões por família com a demanda total e, em uma etapa posterior, desagregar por SKU, região ou canal.
- **Integração com o PCP**: converter previsões em plano mestre de produção, necessidades de materiais, capacidade e política de estoque, considerando lotes, validade e restrições produtivas.
- **Análise de incerteza**: usar intervalos de previsão e simular cenários de demanda alta, base e baixa.

---

## 🎥 Vídeo Explicativo e Simulação

![Vídeo demonstrando o Problema de Previsão de Demanda em uma indústria alimentícia – Séries Temporais com ARIMA, SARIMA e suas variações.](Link do Vídeo no Youtube)](https://youtu.be/XXXXXXXXX)

