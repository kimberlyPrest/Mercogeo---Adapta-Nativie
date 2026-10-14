# Fase 2 — Dimensionamento e catálogo homologado

## Resultado

Transformar a ficha técnica do serviço-piloto em quantitativos e recursos reproduzíveis, mantendo a decisão de engenharia humana e exibindo a memória de cálculo.

## Inclui

- biblioteca versionada de serviços, recursos e composições;
- dimensionamento assistido;
- validação de unidades, campos e vigência;
- ajustes técnicos justificados;
- clonagem controlada de casos;
- área de trabalho por módulo, sem indicadores fictícios (expansão 14/10);
- unidades, vínculo ficha → composição, editor estruturado de fórmula e fixture executada na homologação (expansão 14/10);
- solução técnica com várias composições, quantitativos consolidados por recurso, painel de pendências e exportação da memória (expansão 14/10);
- tasks explícitas, com dono, para destravar BLK-1..4 e aprovar o gate da família (expansão 14/10).

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
- **CA-2-11:** toda função entregue nas Fases 1 e 2 é alcançável pelo menu lateral em rota própria conforme o papel; nenhuma tela exibe indicador numérico sem fonte server-side; erros de negócio exibem o motivo real retornado pelo servidor.
- **CA-2-12:** Engenharia monta entradas, unidades, faixas, vínculo com a ficha e fórmula pela interface, sem editar JSON; unidade não homologada, dimensão incompatível ou valor fora da faixa é bloqueado no servidor indicando o campo.
- **CA-2-13:** composição só é homologada após o servidor executar a fixture assinada na versão exata e o resultado ficar dentro da tolerância; divergência é exibida e auditada.
- **CA-2-14:** uma oportunidade possui solução técnica com duas ou mais composições justificadas, e o sistema exibe quantitativos por item e consolidados por recurso e unidade, rastreáveis até a parcela, sem custo ou preço.
- **CA-2-15:** painel lista toda pendência que impede confirmar ou congelar (tipo, campo, responsável, data); confirmação ou congelamento com pendência aberta é negado com a lista.
- **CA-2-16:** memória de dimensionamento é exportada em JSON e CSV com hash verificável e recibo de auditoria, respeitando o acesso à oportunidade.

## Demonstração visível

Executar uma fixture homologada e uma oportunidade real com solução de várias composições, explicar cada parcela e o consolidado por recurso, demonstrar bloqueios por dado ausente, unidade incompatível e regra inativa no painel de pendências e exportar a memória com hash.

## Fora desta fase

- Custos, catálogo de custos, BDI, preço, cenários, margem e alçadas — Fase 3.
- Documento de proposta com preço (PDF/editável), aprovação comercial e envio — Fase 4.
- Conectores VOBI/OMIE, IA assistiva e painel K1–K3 — Fase 5.
- Conversão automática entre unidades e funções de fórmula além de soma, subtração, multiplicação e divisão — exige emenda homologada.
- Cadastro comercial de Clientes/Projetos como CRM — fora do programa (escopo, item 1).
- Uso de dados reais ou cálculo operacional antes da aprovação do gate da família (T2.29).

## Expansão de 14/10/2026

Kim autorizou ampliar a Fase 2 depois da análise de coerência. Entram 3 SPECs (2-006 a 2-008), 6 critérios (CA-2-11 a CA-2-16) e 17 tasks (T2.13 a T2.29). Nenhum critério anterior foi alterado. As dependências de T2.6, T2.11 e T2.12 foram ampliadas para incluir as novas provas. Execução: uma task por vez; as levas mostram a ordem de dependência, não autorizam execução em lote. Tasks documentais (T2.24 a T2.28) são feitas pelos donos da Mercogeo, com os templates A–D.

## Tasks

| ID | Task | Dono | SPEC | Critério | Subseção | Recorte da prova | Evidência esperada | Pré-condições | Leva | Ponto de parada | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|
| T2.1 | Consolidar prontidão e contratos reais | Consultor | SPEC-2-001 | RN-21/RN-22/CA-1-13 | Fechamento de dependências | GREEN-P2-001 | recibo e homologações | nenhuma | A | GREEN + regressão → teste humano explícito | ✅ concluída 2026-10-03 — recibo de prontidão GREEN-P2-001 entregue e aprovado (0/4 dependências resolvidas; gate bloqueado) |
| T2.2 | Exibir e proteger gate de prontidão por família | Produto | SPEC-2-001 | Pré-condições F2 | Dados, fluxo e regras | RED/GREEN/REG-P2-001 | logs gate e papéis | T2.1 | B | GREEN + regressão → teste humano explícito | ✅ concluída 2026-10-03 — provas RED/GREEN/REG-P2-001 10/10 PASS via API real + revalidação 6/6; invalidação real provada (0046); teste humano no preview aprovado (badge INVALIDADO + motivo RN-21; formulário ausente para Comercial com 403 server-side); QA 0.0.59–0.0.64 |
| T2.3 | Criar rascunho versionado de composição | Produto | SPEC-2-002 | CA-2-01/10 | Dados e contrato | RED/GREEN-P2-002A | versões e negação por papel | nenhuma | A | GREEN + regressão → teste humano explícito | em teste humano — passos 1–3 aprovados; revalidar passo 4 após T2.13 (correção de 0.0.69 revertida em 0.0.71) |
| T2.4 | Homologar e filtrar versões utilizáveis | Engenharia | SPEC-2-002 | CA-2-01/02/10 | Estados e ações | GREEN-P2-002B/REG-P2-002 | catálogo e assinatura | T2.1, T2.3 | B | GREEN + regressão → teste humano explícito | bloqueada |
| T2.5 | Demonstrar aritmética e bloqueios com massa sintética | Produto | SPEC-2-003 | CA-2-03/04 | Aritmética e segurança | RED/GREEN-P2-003A | suite precisão JSVM e memória sintética | T2.3 | B | GREEN + regressão → teste humano explícito | bloqueada |
| T2.6 | Dimensionar fixture homologada com snapshot | Engenharia | SPEC-2-003 | CA-2-03/04 | Fluxo | GREEN-P2-003B | fixture e memória reproduzível | T2.2, T2.4, T2.5, T2.19, T2.29 | F | GREEN + regressão → teste humano explícito | bloqueada |
| T2.7 | Confirmar solução técnica e provar concorrência | Engenharia | SPEC-2-003 | CA-2-05 | Fluxo | GREEN-P2-003B/REG-P2-003 | assinatura e logs conflito/403 | T2.6 | G | GREEN + regressão → teste humano explícito | bloqueada |
| T2.8 | Aplicar ajuste técnico preservando original | Engenharia | SPEC-2-004 | CA-2-06 | Dados e regras | RED/GREEN-P2-004A | original e novo valor auditados | T2.7 | H | GREEN + regressão → teste humano explícito | bloqueada |
| T2.9 | Congelar resultado e provar invariância | Engenharia | SPEC-2-004 | CA-2-07 | Dados e regras | GREEN-P2-004A/REG-P2-004 | snapshot v1/v2 e comparação | T2.8 | I | GREEN + regressão → teste humano explícito | bloqueada |
| T2.10 | Clonar rascunho com reconfirmações e idempotência | Produto | SPEC-2-004 | CA-2-08 | Dados e regras | GREEN-P2-004B/REG-P2-004 | IDs, pendências e conflito | T2.9 | J | GREEN + regressão → teste humano explícito | bloqueada |
| T2.11 | Demonstrar oportunidade real e revisão técnica | Engenharia | SPEC-2-005 | CA-2-09 | Fluxo de validação | GREEN-P2-005 | memória, captura e declaração | T2.10, T2.22, T2.29 | K | GREEN + regressão → teste humano explícito | bloqueada |
| T2.12 | Consolidar regressão e recibo de aceite F2 | Consultor | SPEC-2-005 | CA-2-01..16 | Matriz do aceite | RED/REG-P2-005 | manifesto e aceite humano | T2.11, T2.15, T2.23 | L | GREEN + regressão → teste humano explícito | bloqueada |
| T2.13 | Restaurar motivo real dos erros de negócio com teste | Produto | SPEC-2-006 | CA-2-11 | Fluxo e regras (5) | RED/GREEN-P2-006A | teste + captura do 409 | nenhuma | A | GREEN + regressão → teste humano explícito | pendente |
| T2.14 | Menu lateral por papel com módulos reais e sem indicadores fictícios | Produto | SPEC-2-006 | CA-2-11 | Fluxo e regras (1, 2, 4) | RED/GREEN-P2-006B | capturas por papel | T2.13 | B | GREEN + regressão → teste humano explícito | bloqueada |
| T2.15 | Extrair seções do painel técnico em páginas por módulo | Produto | SPEC-2-006 | CA-2-11 | Fluxo e regras (3) | REG-P2-006 | mapa de equivalência + regressão | T2.14 | C | GREEN + regressão → teste humano explícito | bloqueada |
| T2.16 | Cadastrar e homologar unidades com dimensão | Produto | SPEC-2-007 | CA-2-12 | Fluxo e regras (1) | RED-P2-007A (unidade/papel) | unidades e negações | T2.3 | B | GREEN + regressão → teste humano explícito | bloqueada |
| T2.17 | Mapear entradas da composição a parâmetros da ficha com faixa | Produto | SPEC-2-007 | CA-2-12 | Fluxo e regras (2, 6) | RED-P2-007A (faixa) | mapeamento e bloqueios | T2.16 | C | GREEN + regressão → teste humano explícito | bloqueada |
| T2.18 | Montar fórmula pelo editor estruturado com validação dimensional | Produto | SPEC-2-007 | CA-2-12 | Fluxo e regras (3, 4) | RED/GREEN-P2-007A | AST + memória sintética | T2.5, T2.17 | D | GREEN + regressão → teste humano explícito | bloqueada |
| T2.19 | Executar fixture assinada como condição de homologação | Produto | SPEC-2-007 | CA-2-13 | Fluxo e regras (5) | RED/GREEN-P2-007B, REG-P2-007 | relatório de fixture + auditoria | T2.4, T2.18 | E | GREEN + regressão → teste humano explícito | bloqueada |
| T2.20 | Montar solução técnica com várias composições justificadas | Produto | SPEC-2-008 | CA-2-14 | Fluxo e regras (1, 2) | RED/GREEN-P2-008A (itens) | solução e memória por item | T2.5, T2.18 | E | GREEN + regressão → teste humano explícito | bloqueada |
| T2.21 | Consolidar quantitativos por recurso e unidade | Produto | SPEC-2-008 | CA-2-14 | Fluxo e regras (2) | GREEN-P2-008A (consolidação) | consolidado rastreável | T2.20 | F | GREEN + regressão → teste humano explícito | bloqueada |
| T2.22 | Painel de pendências que bloqueia confirmação e congelamento | Produto | SPEC-2-008 | CA-2-15 | Fluxo e regras (3, 4) | RED/GREEN-P2-008B | painel + 409 listado | T2.7, T2.21 | H | GREEN + regressão → teste humano explícito | bloqueada |
| T2.23 | Exportar memória de dimensionamento com hash e recibo | Produto | SPEC-2-008 | CA-2-16 | Fluxo e regras (5) | GREEN-P2-008C, REG-P2-008 | arquivos, hash e recibo | T2.9, T2.21 | J | GREEN + regressão → teste humano explícito | bloqueada |
| T2.24 | Decidir família-piloto e resolver modelo Poliureia/geotecnia (BLK-4) | Comercial | SPEC-2-001 | RN-01/RN-21 | Fechamento de dependências | GREEN-P2-001 (família) | Template D parte 1 assinado | nenhuma | A | evidência anexada → aceite explícito do dono | pendente |
| T2.25 | Homologar SLA da família-piloto no sistema (BLK-2) | Engenharia | SPEC-2-001 | RN-21 | Fechamento de dependências | GREEN-P2-001 (SLA) | Template A + parâmetro SLA homologado | T2.24 | B | evidência anexada → aceite explícito do dono | bloqueada |
| T2.26 | Congelar baseline ou registrar parecer de limitação (BLK-3) | Engenharia | SPEC-2-001 | RN-22 | Fechamento de dependências | GREEN-P2-001 (baseline) | Template B + baseline/parecer | T2.24 | B | evidência anexada → aceite explícito do dono | bloqueada |
| T2.27 | Demonstrar recuperação real em instância isolada (BLK-1) | Dados | SPEC-2-001 | CA-1-13 | Fechamento de dependências | GREEN-P2-001 (recuperação) | Template C + comparação antes/depois | nenhuma | A | evidência anexada → aceite explícito do dono | pendente |
| T2.28 | Assinar contrato e fixture real da primeira composição (BLK-4) | Engenharia | SPEC-2-001 | RN-02/CA-2-03 | Homologação do cálculo | GREEN-P2-001 (fixture) | Template D parte 2 assinado | T2.24 | B | evidência anexada → aceite explícito do dono | bloqueada |
| T2.29 | Aprovar gate de prontidão da família com vínculos verificáveis | Engenharia | SPEC-2-001 | RN-21/RN-22/CA-1-13 | Dados, fluxo e regras | GREEN-P2-001 (aprovação) | aprovação auditada no gate | T2.2, T2.25, T2.26, T2.27, T2.28 | C | GREEN + regressão → teste humano explícito | bloqueada |
