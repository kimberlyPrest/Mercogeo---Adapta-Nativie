# PRD — Central de Engenharia de Propostas Mercogeo

**Estado:** aprovado pela consultora e CSM/cliente; Fase 1 em documentação  
**Data:** 2026-09-11  
**Empresa:** Merco Geopolímeros Engenharia e Consultoria Ltda.  
**Processo crítico:** inteligência técnico-comercial para dimensionamento, precificação e geração de propostas.

## 1. Problema

A Mercogeo transforma demandas técnicas em propostas por meio de conhecimento concentrado em poucas pessoas, planilhas de teste, composições extensas e conferências manuais. O processo disputa tempo com visitas e decisões de engenharia, não possui baseline confiável e não produz hoje uma comparação sistemática entre margem estimada e realizada.

## 2. Objetivo do produto

Criar uma **Central de Engenharia de Propostas Técnico-Comerciais** que estruture a oportunidade, preserve o julgamento técnico humano, apoie o dimensionamento, calcule custos e preço com regras homologadas, governe aprovações e gere propostas completas, versionadas e rastreáveis.

O produto deverá reduzir o tempo e o esforço humano entre uma demanda apta para orçamento e uma proposta aprovada e pronta para envio, sem automatizar fórmulas, custos ou decisões técnicas não homologadas.

## 3. Usuários

- Comercial técnico: registra a demanda, acompanha pendências e conduz o envio.
- Engenharia/orçamentista: qualifica tecnicamente, dimensiona e valida composições.
- Financeiro/administrativo: mantém custos, impostos e parâmetros autorizados.
- Aprovador: decide exceções de preço, desconto e margem.
- Gestão: acompanha prazo, esforço, SLA, versões e resultados.

## 4. Jornada-alvo

Entrada da demanda → qualificação mínima → ficha técnica → seleção humana da solução → dimensionamento assistido → composição de custos → precificação e cenários → aprovação → geração do documento → revisão → proposta pronta para envio → registro do desfecho.

A medição contratual principal encerra em **proposta enviada**, conforme o briefing. O sistema também medirá **proposta aprovada e pronta para envio** como marco operacional, isolando o tempo interno do tempo gasto em portais de terceiros. O preenchimento automático nesses portais não integra o piloto.

## 5. Resultados e métricas

### K1 — Tempo demanda recebida → proposta enviada
- **Fórmula contratual:** média do tempo corrido entre o primeiro registro verificável do recebimento da demanda e o registro do envio da proposta ao cliente.
- **Métricas operacionais complementares:** demanda recebida→apta, apta→pronta para envio e pronta→enviada, para distinguir qualificação, processamento interno e esforço de portal.
- **Regra de comparabilidade:** baseline e resultado devem usar a mesma fronteira, a mesma definição de calendário e classes equivalentes; qualquer mudança de método será mostrada separadamente, nunca combinada na redução percentual.
- **Baseline:** medido na Fase 1 com amostra retrospectiva confiável ou medição prospectiva.
- **Meta:** redução de pelo menos 50% no serviço-piloto, comparando amostras equivalentes.

### K2 — Horas humanas por proposta
- **Fórmula:** soma do tempo ativo registrado nas etapas de qualificação técnica, dimensionamento, composição, precificação, redação e revisão.
- **Baseline:** Fase 1.
- **Meta:** redução de pelo menos 50% no serviço-piloto, condicionada à suficiência da amostra.

### K3 — Propostas dentro do SLA
- **Fórmula:** propostas enviadas dentro do SLA homologado ÷ todas as propostas elegíveis do período cujo SLA venceu ou que já foram enviadas.
- **Elegível:** demanda da família-piloto que atingiu o checklist de aptidão; cancelamentos pelo cliente antes do vencimento só podem ser excluídos por motivo auditável e permanecem visíveis no painel.
- **Baseline e SLA:** Fase 1.
- **Meta:** pelo menos 90%.

### K4 — Margem estimada versus realizada
- Indicador secundário, não bloqueador do núcleo inicial.
- Só será calculado quando existir fonte de custo realizado homologada, fechamento da obra e definição da fórmula do desvio.
- Meta candidata de desvio inferior a 10%, sujeita à homologação do denominador, da janela e da fonte.
- Enquanto K4 não for mensurável, o painel exibirá os proxies: diferença entre preço calculado e valor aprovado, percentual de propostas com custo vencido/excepcionado e frequência de revisão das premissas; proxies não serão apresentados como margem realizada.

## 6. Escopo do piloto

O piloto será executado sobre **uma família de serviço escolhida e homologada pela Mercogeo**. Geotecnia e poliureia são candidatas; nenhuma será presumida sem decisão dos responsáveis.

Inclui:
- baseline e instrumentação;
- cadastro estruturado da demanda e ficha técnica;
- catálogo versionado de recursos e composições homologadas;
- dimensionamento assistido, sem decisão autônoma de engenharia;
- custo direto, BDI, preço e cenários;
- alçadas e aprovações;
- proposta completa em PDF e versão editável;
- histórico, clonagem controlada, alertas e painel mínimo;
- preparação da conexão com VOB/OMIE sem assumir API.

## 7. Fora do escopo

- CRM completo de aquisição, marketing e prospecção;
- automação de visitas técnicas;
- gestão da execução da obra, compras, estoque, faturamento ou financeiro completo;
- envio ou preenchimento automático em SAP Ariba, Mercado Eletrônico e portais de clientes;
- substituição automática de VOB ou OMIE;
- decisão autônoma de solução técnica, margem, desconto ou aprovação;
- automação de planilhas, BDI e custos não homologados;
- cálculo de margem realizada sem fonte de custo real aprovada;
- Merco Tape e preparação operacional de obras.

## 8. Princípios

1. Humano decide a solução técnica e exceções comerciais.
2. Toda saída financeira deve apontar para a versão dos dados e regras utilizadas.
3. Proposta emitida é imutável; alteração gera nova versão.
4. Fórmula não homologada não executa silenciosamente.
5. Ausência de dado obrigatório vira pendência, não valor presumido.
6. IA, quando usada, apenas sugere preenchimento ou texto a partir de dados aprovados e exige revisão humana.

## 9. Dependências controladas

- escolha da família-piloto;
- 2–3 casos reais ou propostas históricas representativas;
- homologação de composições, custos, BDI, ISS, margem e alçadas;
- definição do SLA e da fonte de cada custo;
- decisão sobre o papel de VOB e OMIE;
- fonte de custo realizado para K4, quando aplicável.

A falta dessas dependências limita a ativação das regras correspondentes, mas não autoriza o sistema a inventá-las.

## 10. Riscos

- automatizar erro de planilha em escala;
- amostra insuficiente para provar redução de 50%;
- duplicidade com VOB/OMIE;
- documento pronto não reduzir o tempo gasto em portais externos;
- baixa adoção por sobrecarga do time;
- margem realizada continuar indisponível.

## 11. Estratégia de entrega em quatro meses

- **Semanas 1–3:** Fase 1, baseline prospectivo iniciado, fluxo real, família-piloto e prévia documental.
- **Semanas 4–7:** Fase 2, catálogo homologado e dimensionamento.
- **Semanas 8–11:** Fase 3, custos, preço, cenários e alçadas.
- **Semanas 12–14:** Fase 4, documento completo, aprovação e envio.
- **Semanas 15–16:** Fase 5, medição, estabilização e integrações/importações que tenham contrato homologado.

A homologação da família-piloto é o caminho crítico. Se atrasar, a ordem de corte é: **RF-28 assistência por IA → RF-15 múltiplos cenários além do cenário-base → integrações em tempo real, preservando importação controlada → motivo de perda analítico além do registro mínimo**. Não se cortam baseline, catálogo homologado, memória de cálculo, aprovação, documento completo, segurança ou auditoria.

A Mercogeo deverá nomear responsáveis e reservar uma sessão semanal de homologação. Um bloqueio sem dono ou sem data de decisão é escalado no check da fase e impede ativar a regra afetada.

## 12. Critério de conclusão do ciclo

O ciclo estará funcionalmente concluído quando uma oportunidade real da família-piloto percorrer, com trilha de auditoria, da demanda apta à proposta enviada, mantendo também o marco de proposta aprovada e pronta para envio; os cálculos puderem ser reproduzidos a partir das versões homologadas; e K1–K3 puderem ser calculados com baseline comparável. K4 poderá permanecer inconclusivo se sua fonte externa não for homologada, sem ser apresentado como atingido.
