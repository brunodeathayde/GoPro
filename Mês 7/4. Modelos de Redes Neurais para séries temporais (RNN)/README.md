# 🏖️ Previsão de Demanda Hoteleira no Litoral do Ceará — Redes Neurais Recorrentes (RNN)

## 📌 Descrição do Problema

Este repositório apresenta uma instância didática de **previsão diária da demanda de hospedagem em uma rede de hotéis no litoral do Ceará**. O problema está relacionado ao planejamento e ao dimensionamento da capacidade dos estabelecimentos: estimar quantos hóspedes estarão hospedados em cada unidade e como essa demanda varia entre destinos, dias da semana, períodos de férias e datas turísticas.

A previsão de hóspedes pode apoiar a definição de escalas de recepcionistas, camareiras, equipes de limpeza, cozinha, manutenção e recreação; o planejamento de alimentos, bebidas, enxoval e materiais de consumo; a organização de check-ins e check-outs; e a antecipação de períodos de alta ocupação. Essas decisões são particularmente relevantes para destinos com perfis diferentes, como Fortaleza, Porto das Dunas (Aquiraz) e Jericoacoara.

O estudo utiliza **Modelos de Redes Neurais Recorrentes (Recurrent Neural Networks — RNN)**, capazes de aprender dependências temporais a partir de sequências de observações. Podem ser avaliadas arquiteturas recorrentes simples (*SimpleRNN*), **LSTM** (*Long Short-Term Memory*) e **GRU** (*Gated Recurrent Unit*), tanto em modelos individuais por hotel quanto em um modelo global para a rede.

---

## 🎯 Enunciado do Problema

Desenvolver, ajustar e avaliar modelos de previsão de séries temporais para estimar a quantidade diária de **hóspedes hospedados** em cada um dos três estabelecimentos da rede. Os resultados devem apoiar perguntas de planejamento como:

- Qual é a demanda esperada de hóspedes em cada hotel para os próximos 1, 7, 14 ou 28 dias?
- Quais são os padrões semanais e anuais de cada estabelecimento? Os fins de semana diferem dos dias úteis?
- Como férias escolares, feriados, Carnaval, Réveillon e eventos turísticos influenciam a demanda?
- A série de cada hotel apresenta sazonalidades e níveis de demanda distintos?
- O uso de reservas confirmadas com antecedência melhora a previsão em comparação com modelos que utilizam apenas o histórico da demanda?
- Como converter as previsões em decisões de dimensionamento de equipes, quartos, alimentação, limpeza e demais serviços?

O desafio consiste em comparar arquiteturas (SimpleRNN, LSTM e GRU), tamanhos de janela, número de unidades recorrentes, camadas, funções de ativação, regularização (*dropout*) e variáveis de entrada. A configuração escolhida deve ser justificada pelo desempenho no conjunto de teste, pela estabilidade temporal e pela utilidade operacional das previsões.

### Variável-alvo e interpretação operacional

A variável-alvo é **`Hospedes_Hospedados`**, que representa o número de hóspedes presentes no hotel em determinado dia. É uma medida de carga operacional diária e pode apoiar o planejamento de serviços que variam com a quantidade de pessoas hospedadas.

A planilha também apresenta indicadores auxiliares, como `Hospedes_Checkin`, `Hospedes_Checkout`, `Quartos_Ocupados` e `Taxa_Ocupacao`. Eles ajudam a interpretar a operação, mas não devem ser usados como preditores contemporâneos da variável-alvo quando seus valores reais ainda não forem conhecidos no instante em que a previsão será produzida.

---

## 🌍 Dados da Instância

A instância está disponível em **`Instancia_Previsao_Demanda_Hoteis_Ceara_RNN.xlsx`** e contém **1.096 observações diárias por hotel**, de **01/01/2023 a 31/12/2025**, totalizando **3.288 observações hotel-dia**. A base oferece os formatos amplo e longo, características dos hotéis, variáveis de calendário, dicionário de dados e um painel com estatísticas descritivas e gráfico de demanda mensal.

### Hotéis da instância

| Identificador | Estabelecimento | Município / destino | Perfil ilustrativo | Quartos | Capacidade de hóspedes |
| :---: | :--- | :--- | :--- | ---: | ---: |
| `H01` | Hotel Oceano Fortaleza | Fortaleza | Hotel urbano, lazer e negócios | 140 | 360 |
| `H02` | Resort Dunas Portuária | Aquiraz — Porto das Dunas | Resort voltado a famílias e lazer | 125 | 320 |
| `H03` | Pousada Jericoacoara Azul | Jijoca de Jericoacoara | Hospedagem de praia e natureza | 85 | 210 |

As capacidades são parâmetros sintéticos utilizados na geração da instância. Não correspondem a empreendimentos reais.

### Amostra dos dados diários

A tabela abaixo apresenta os primeiros registros da série sintética. O valor-alvo é a quantidade de hóspedes hospedados em cada hotel:

| Data | Dia da semana | Hotel Oceano Fortaleza | Resort Dunas Portuária | Pousada Jericoacoara Azul | Total de hóspedes |
| :---: | :--- | ---: | ---: | ---: | ---: |
| 01/01/2023 | Domingo | 284 | 284 | 188 | 756 |
| 02/01/2023 | Segunda-feira | 260 | 269 | 186 | 715 |
| 03/01/2023 | Terça-feira | 219 | 211 | 140 | 570 |
| 04/01/2023 | Quarta-feira | 205 | 243 | 152 | 600 |
| 05/01/2023 | Quinta-feira | 221 | 226 | 150 | 597 |

### Estatísticas descritivas do período

| Hotel | Média (hóspedes/dia) | Mínimo diário | Máximo diário | Média de ocupação dos quartos | Total de hóspedes-dia |
| :--- | ---: | ---: | ---: | ---: | ---: |
| Hotel Oceano Fortaleza | 202,6 | 145 | 303 | 61,6% | 222.031 |
| Resort Dunas Portuária | 186,5 | 119 | 294 | 62,2% | 204.422 |
| Pousada Jericoacoara Azul | 133,6 | 83 | 193 | 69,9% | 146.456 |

A ocupação média é calculada pela relação entre quartos ocupados e número total de quartos. Por isso, a pousada de menor porte pode apresentar maior percentual médio de ocupação, mesmo com menor quantidade absoluta de hóspedes.

### Padrões embutidos na instância

- **Sazonalidade semanal**: a demanda foi construída para apresentar aumento nos fins de semana, com intensidade diferente entre os hotéis.
- **Sazonalidade anual**: há elevações em janeiro, julho e no fim de dezembro, representando períodos de férias e maior procura turística.
- **Feriados e períodos festivos**: feriados nacionais e estaduais, Carnaval e Réveillon são representados por indicadores binários.
- **Férias escolares**: janeiro, julho e a segunda quinzena de dezembro recebem um indicador de período de férias.
- **Eventos locais**: algumas datas de julho e agosto foram marcadas como eventos turísticos simulados. Elas não representam o calendário oficial de eventos.
- **Variáveis exógenas**: reservas confirmadas com 14 dias de antecedência, chuva e temperatura máxima foram incluídas para permitir experimentos com informação adicional.
- **Heterogeneidade entre hotéis**: os estabelecimentos apresentam capacidades, níveis médios de demanda e intensidades sazonais diferentes.

### Organização do arquivo Excel

- **`Leia_Me`**: objetivo, período, divisão treino/teste, variável-alvo, cuidados de uso e orientação de importação.
- **`Cadastro_Hoteis`**: identificador, município, perfil, número de quartos e capacidade de hóspedes de cada hotel.
- **`Calendario`**: uma linha por dia, com dia da semana, mês, feriados, férias, Carnaval, Réveillon, eventos simulados e variáveis climáticas.
- **`Serie_Diaria`**: formato amplo, com uma linha por data, demanda e reservas de cada hotel e total diário. É útil para visualizações e comparação entre unidades.
- **`Dados_Longos`**: formato longo, com uma linha por hotel e data. Inclui a variável-alvo, indicadores operacionais, reservas, calendário, clima e identificação do conjunto. É a aba recomendada para importar no Python e construir as sequências de entrada da RNN.
- **`Dicionario`**: descrição das variáveis, interpretação e alertas sobre o uso de cada atributo.
- **`Painel`**: médias, mínimos, máximos, totais por hotel e gráfico da média mensal de hóspedes hospedados.

---

## 🧠 Preparação dos dados para modelos RNN

Uma RNN recebe sequências temporais, e não apenas linhas independentes. Uma configuração inicial é utilizar uma janela de **28 dias** para prever a demanda do último dia da sequência. Recomenda-se testar janelas de 7, 14, 28 e 56 dias.

### Variáveis de entrada sugeridas

Para uma previsão diária, podem ser utilizadas:

| Variável | Papel no modelo | Observação |
| :--- | :--- | :--- |
| `Hospedes_Lag1` | Histórico da demanda | Hóspedes observados no dia anterior. |
| `Hospedes_Lag7` | Histórico sazonal | Hóspedes observados sete dias antes. |
| `Reservas_Confirmadas_D14` | Variável exógena | Reservas conhecidas 14 dias antes da hospedagem. |
| `Dia_Semana_Sin`, `Dia_Semana_Cos` | Calendário cíclico | Representação do ciclo semanal. |
| `Dia_Ano_Sin`, `Dia_Ano_Cos` | Calendário cíclico | Representação do ciclo anual. |
| `Fim_De_Semana` | Calendário | Indicador binário de sábado/domingo. |
| `Feriado`, `Ferias_Escolares` | Calendário | Variáveis conhecidas antecipadamente. |
| `Carnaval`, `Reveillon` | Eventos sazonais | Indicadores de períodos turísticos. |
| `Evento_Local_Simulado` | Evento | Variável ilustrativa, que deve ser substituída por um calendário real. |

A identificação do hotel pode ser tratada por modelos independentes ou codificada por *one-hot encoding*/*embedding* em um modelo global.

---

## 📏 Métricas de avaliação das previsões

- **MAE (Mean Absolute Error)**: erro absoluto médio em hóspedes/dia, de interpretação operacional direta.
- **RMSE (Root Mean Squared Error)**: penaliza mais fortemente erros elevados, importante em períodos de pico.
- **WAPE (Weighted Absolute Percentage Error)**: soma dos erros absolutos dividida pela soma dos valores observados, em porcentagem; permite comparar hotéis com escalas de demanda diferentes.
- **Viés (*bias*)**: média de `previsto − observado`; valores positivos indicam superestimação e valores negativos indicam subestimação sistemática.
- **Erro em períodos de pico**: avaliar separadamente férias, feriados e eventos, pois erros nesses períodos podem comprometer o dimensionamento da operação.

Compare as redes neurais com uma **previsão ingênua sazonal**: utilizar para cada dia o valor observado no mesmo dia da semana anterior (`t−7`). A comparação deve ser feita separadamente para cada hotel e, adicionalmente, para a rede como um todo. Recomenda-se apresentar gráficos de observado versus previsto e resíduos ao longo do tempo.

---

## 📚 Referências Bibliográficas

- Elman, J. L. (1990). *Finding Structure in Time*. **Cognitive Science, 14**(2), 179–211.
- Hochreiter, S., & Schmidhuber, J. (1997). *Long Short-Term Memory*. **Neural Computation, 9**(8), 1735–1780.
- Cho, K., van Merriënboer, B., Gulcehre, C., Bahdanau, D., Bougares, F., Schwenk, H., & Bengio, Y. (2014). *Learning Phrase Representations using RNN Encoder–Decoder for Statistical Machine Translation*. arXiv:1406.1078.
- Documentação do TensorFlow — *Time series forecasting*: https://www.tensorflow.org/tutorials/structured_data/time_series
- Documentação do Keras — camadas recorrentes: https://keras.io/api/layers/recurrent_layers/
- Hyndman, R. J., & Athanasopoulos, G. *Forecasting: Principles and Practice* — capítulos sobre validação temporal e avaliação de previsões. Disponível em: https://otexts.com/fpp3/

---

## 🚀 Possíveis Extensões

- **Comparação de arquiteturas**: SimpleRNN, LSTM e GRU, com diferentes números de unidades e camadas.
- **Ajuste de hiperparâmetros**: tamanho da janela, número de neurônios, *dropout*, taxa de aprendizado, tamanho do lote e número de épocas.
- **Validação temporal deslizante (*rolling-origin*)**: repetir os experimentos com diferentes datas de corte para avaliar a robustez.
- **Modelo global para a rede**: combinar dados dos três hotéis, incluindo identificador do hotel por codificação categórica ou *embedding*.
- **Previsão multi-horizonte**: estimar simultaneamente os próximos 7, 14 ou 28 dias, em vez de apenas um dia à frente.
- **Variáveis externas reais**: integrar reservas efetivas, cancelamentos, tarifas, eventos, feriados municipais e previsões meteorológicas.
- **Demanda por serviço**: ampliar a previsão para check-ins, check-outs, quartos a limpar, refeições e consumo de enxoval.
- **Previsão probabilística**: utilizar *ensembles*, *dropout* em inferência ou funções de perda quantílicas para produzir cenários e margens de segurança.
- **Dimensionamento de equipes**: transformar a previsão de hóspedes em necessidades estimadas de mão de obra por setor, mediante parâmetros operacionais (por exemplo, tempo médio de atendimento ou quartos limpos por camareira).
- **Comparação com modelos tradicionais**: avaliar RNN/LSTM/GRU frente a médias móveis, suavização exponencial, SARIMA, Prophet e métodos de aprendizado de máquina.

---

## 🎥 Material Explicativo e Simulação

Sugestão de atividade: importar a aba `Dados_Longos`, selecionar um hotel, construir janelas de 28 dias, ajustar uma GRU ou LSTM e avaliar as previsões para 2025. Em seguida, repetir o experimento para os outros hotéis, comparar os resultados com a previsão ingênua sazonal e elaborar uma recomendação de planejamento de equipes e serviços para os próximos 14 dias.

![Vídeo explicativo sobre Redes Neurais e previsão de demanda diária](Link do vídeo no YouTube)(https://youtu.be/XXXXXXXXX)