# Fase 2 — Dimensionamento e catálogo homologado

## Resultado

Transformar a ficha técnica do serviço-piloto em quantitativos e recursos reproduzíveis, mantendo a decisão de engenharia humana e exibindo a memória de cálculo.

## Inclui

- biblioteca versionada de serviços, recursos e composições;
- dimensionamento assistido;
- validação de unidades, campos e vigência;
- ajustes técnicos justificados;
- clonagem controlada de casos.

## Critérios de aceite

- **CA-2-01:** cada composição ativa possui código, unidade, coeficientes, fonte, versão, vigência, dono e aprovação.
- **CA-2-02:** composição em rascunho, inativa ou vencida não pode integrar resultado aprovado.
- **CA-2-03:** para fixture homologada, o sistema reproduz o resultado esperado dentro da tolerância definida e apresenta a memória de cálculo.
- **CA-2-04:** unidade incompatível, entrada ausente ou coeficiente inválido bloqueia o cálculo e identifica a causa.
- **CA-2-05:** a seleção da solução e das composições exige confirmação do responsável técnico e fica auditada.
- **CA-2-06:** ajuste manual preserva valor calculado, novo valor, justificativa, autor e data.
- **CA-2-07:** mudança de versão da composição não altera orçamento já congelado.
- **CA-2-08:** clonagem cria novo rascunho e exige reconfirmação de custos vencidos, documentos, prazos e premissas.
- **CA-2-09:** pelo menos uma proposta real percorre ficha → dimensionamento → revisão técnica; a prova inclui registro de tela, memória calculada pelo sistema e declaração do responsável de que a planilha foi usada apenas como referência de conferência, não como calculadora de produção.
- **CA-2-10:** usuário não autorizado não consegue criar, homologar, inativar ou alterar composição.

## Demonstração visível

Executar uma fixture homologada e uma oportunidade real, explicar cada parcela do resultado e demonstrar bloqueios por dado ausente e regra inativa.

## Tasks

| ID | Task | Dono | SPEC | Critério | Subseção | Recorte da prova | Evidência esperada | Pré-condições | Leva | Ponto de parada | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| T2.1 | Consolidar prontidão e contratos reais | Consultor | SPEC-2-001 | RN-21/RN-22/CA-1-13 | Fechamento de dependências | GREEN-P2-001 | recibo e homologações | autorização documental | A | GREEN + regressão → teste humano explícito | pendente |
| T2.2 | Exibir e proteger gate de prontidão por família | Produto | SPEC-2-001 | Pré-condições F2 | Dados, fluxo e regras | RED/GREEN/REG-P2-001 | logs gate e papéis | T2.1 | B | GREEN + regressão → teste humano explícito | bloqueada |
| T2.3 | Criar rascunho versionado de composição | Produto | SPEC-2-002 | CA-2-01/10 | Dados e contrato | RED/GREEN-P2-002A | versões e negação por papel | desenvolvimento isolado; contrato sintético | A | GREEN + regressão → teste humano explícito | pendente |
| T2.4 | Homologar e filtrar versões utilizáveis | Engenharia | SPEC-2-002 | CA-2-01/02/10 | Estados e ações | GREEN-P2-002B/REG-P2-002 | catálogo e assinatura | T2.1,T2.3 | B | GREEN + regressão → teste humano explícito | bloqueada |
| T2.5 | Demonstrar aritmética e bloqueios com massa sintética | Produto | SPEC-2-003 | CA-2-03/04 | Aritmética e segurança | RED/GREEN-P2-003A | suite precisão JSVM e memória sintética | T2.3; runner real | B | GREEN + regressão → teste humano explícito | bloqueada |
| T2.6 | Dimensionar fixture homologada com snapshot | Engenharia | SPEC-2-003 | CA-2-03/04 | Fluxo | GREEN-P2-003B | fixture e memória reproduzível | T2.2,T2.4,T2.5 | C | GREEN + regressão → teste humano explícito | bloqueada |
| T2.7 | Confirmar solução técnica e provar concorrência | Engenharia | SPEC-2-003 | CA-2-05 | Fluxo | GREEN-P2-003B/REG-P2-003 | assinatura e logs conflito/403 | T2.6 | D | GREEN + regressão → teste humano explícito | bloqueada |
| T2.8 | Aplicar ajuste técnico preservando original | Engenharia | SPEC-2-004 | CA-2-06 | Dados e regras | RED/GREEN-P2-004A | original e novo valor auditados | T2.7 | E | GREEN + regressão → teste humano explícito | bloqueada |
| T2.9 | Congelar resultado e provar invariância | Engenharia | SPEC-2-004 | CA-2-07 | Dados e regras | GREEN-P2-004A/REG-P2-004 | snapshot v1/v2 e comparação | T2.8 | F | GREEN + regressão → teste humano explícito | bloqueada |
| T2.10 | Clonar rascunho com reconfirmações e idempotência | Produto | SPEC-2-004 | CA-2-08 | Dados e regras | GREEN-P2-004B/REG-P2-004 | IDs, pendências e conflito | T2.9 | G | GREEN + regressão → teste humano explícito | bloqueada |
| T2.11 | Demonstrar oportunidade real e revisão técnica | Engenharia | SPEC-2-005 | CA-2-09 | Fluxo de validação | GREEN-P2-005 | memória, captura e declaração | T2.10; piloto/fixture reais homologados | H | GREEN + regressão → teste humano explícito | bloqueada |
| T2.12 | Consolidar regressão e recibo de aceite F2 | Consultor | SPEC-2-005 | CA-2-01..10 | Matriz do aceite | RED/REG-P2-005 | manifesto e aceite humano | T2.11 | I | GREEN + regressão → teste humano explícito | bloqueada |
