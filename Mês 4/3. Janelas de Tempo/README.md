🚚 Problema de Roteirização de Veículos com Janelas de Tempo (VRPTW) - Distribuição Urbana
📌 Descrição do Problema

Este repositório contém uma instância real do Problema de Roteirização de Veículos com Janelas de Tempo (VRPTW) para um cenário de distribuição urbana.
Contexto Operacional

A operação consiste em um centro de distribuição (CD) que realiza entregas diárias para um conjunto de clientes georreferenciados. Cada cliente possui características específicas que devem ser respeitadas durante o planejamento das rotas.
📊 Características da Instância
Elemento	Descrição
Depósito	1 centro de distribuição (coordenadas: -38.484229, -3.868207)
Clientes	56 clientes distribuídos na região metropolitana
Frota	Veículos homogêneos com capacidade de 1.000 kg
Turno	Início às 07:30 (minuto 450)
Dados Reais	Matrizes de distância e tempo obtidas via OpenRouteService (ORS)
🎯 Restrições do Problema

Cada cliente i possui:

    Demanda q_i (em kg) - quantidade a ser entregue

    Janela de tempo [e_i, l_i] (em minutos) - período para início do atendimento

    Tempo de serviço s_i (minutos) - tempo necessário para descarregamento

Restrições operacionais:

    ✅ Cada cliente deve ser atendido exatamente uma vez

    ✅ A soma das demandas em cada rota não pode exceder a capacidade do veículo

    ✅ O atendimento a cada cliente deve iniciar dentro de sua janela de tempo

    ✅ Veículos podem aguardar (ociosos) caso cheguem antes do início da janela

    ✅ Todas as rotas iniciam e terminam no depósito

📈 Objetivo

Minimizar a distância total percorrida pela frota, que é utilizada como proxy do custo operacional (combustível, desgaste, quilometragem e tempo de utilização do ativo).
