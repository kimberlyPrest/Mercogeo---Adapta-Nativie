# Fase 1 — Fundação mensurável e primeiro fluxo palpável

## Resultado

Entregar uma central utilizável para cadastrar uma demanda real, qualificá-la, registrar a ficha técnica do serviço-piloto e produzir uma **prévia de proposta sem preço**, enquanto baseline, catálogo, regras e fontes são homologados. Nenhum cálculo financeiro de planilha de teste será ativado como regra comercial.

## Inclui

- escolha e registro da família-piloto;
- mapeamento de 2–3 propostas reais;
- cadastro da oportunidade e checklist de aptidão;
- ficha técnica versionada;
- anexos, pendências, responsáveis e estados;
- captura de timestamps e tempo ativo;
- inventário e homologação inicial de catálogo, fontes, BDI, SLA, alçadas e arredondamento;
- auditoria de VOB e OMIE;
- template inicial de proposta, gerando prévia sem preço.

## Não inclui

Cálculo comercial ativo, BDI automático, aprovação de preço, integração real, IA ou envio ao cliente.

## Critérios de aceite

- **CA-1-01:** existe decisão registrada da família-piloto, com responsável e justificativa.
- **CA-1-02:** pelo menos dois casos representativos possuem fluxo reconstruído da demanda à proposta, com etapas, atores, entradas e saídas validados pela Mercogeo.
- **CA-1-03:** uma oportunidade pode ser cadastrada com cliente, serviço, local, responsáveis, prazo e evidências; o recebimento original fica associado a evento verificável, e tentativa de retrodatação exige justificativa e aparece na auditoria.
- **CA-1-04:** o checklist impede marcar a demanda como apta quando um campo obrigatório está ausente e informa exatamente a pendência.
- **CA-1-05:** a ficha técnica preserva versão, unidade, origem, autor e histórico de cada alteração relevante.
- **CA-1-06:** o sistema registra recebimento, aptidão, pronta, envio, início, fim, pausa justificada e tempo ativo por etapa; o esforço pronta→enviada e a completude dos registros são revisados semanalmente por responsável nomeado.
- **CA-1-07:** o baseline “antes” é congelado antes do uso de dimensionamento/preço e informa amostra, período, fonte, critério de confiabilidade, inclusão, exclusão, classe de complexidade, regra estatística, decomposição do tempo e marcos recebida→apta→pronta→enviada. Se insuficiente, registra “inconclusivo”; se a parcela endereçável não sustentar -50%, a inviabilidade é levada ao check humano antes da Fase 2.
- **CA-1-08:** catálogo inicial separa rascunho, homologado e inativo e identifica dono, fonte e vigência.
- **CA-1-09:** BDI, ISS, margem, SLA, alçadas e regras de arredondamento possuem decisão homologada ou estado explicitamente bloqueado; o SLA da família-piloto é obrigatório para liberar a Fase 2.
- **CA-1-10:** auditoria de VOB e OMIE registra cobertura, fonte de verdade, forma de acesso, campos e decisão integrar, importar ou não usar.
- **CA-1-11:** a prévia documental deriva de um modelo real fornecido e aprovado pela Mercogeo, usa somente dados da oportunidade/ficha e sai marcada “SEM PREÇO — NÃO ENVIAR”; sem modelo real, permanece bloqueada e nenhum template é inventado.
- **CA-1-12:** um usuário sem permissão não consegue homologar catálogo, alterar regras, aprovar ou exportar dados restritos.
- **CA-1-13:** backup, restauração e exportação estruturada são demonstrados antes de o sistema receber dados operacionais como fonte primária.
- **CA-1-14:** a trilha crítica resiste a tentativa de edição ou exclusão por usuário administrativo e mantém ator, data e antes/depois.
- **CA-1-15:** política de retenção define categorias, prazos, descarte e exceções legais; um teste demonstra expiração ou anonimização sem remover evidências financeiras obrigatórias.
- **CA-1-16:** política de identidade cobre senha ou SSO, sessão, tentativas, recuperação e revogação de acesso; desligamento simulado invalida a sessão e bloqueia novo acesso.
- **CA-1-17:** responsáveis e datas de decisão dos bloqueios críticos ficam registrados; atraso aciona escalonamento e a ordem de corte definida no PRD, sem remover controles essenciais.

## Tasks

| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência esperada | Pré-condições | Leva | Status |
|---|---|---|---|---|---|---|---|---|---|
| T1.1 | Configurar papéis e acesso mínimo | Produto | SPEC-1-001 | CA-1-12 | RED-001/GREEN-001 | log de autorização | escopo aprovado | A | ☐ |
| T1.2 | Implementar trilha crítica, retenção e revogação | Produto | SPEC-1-001 | CA-1-14/15/16 | RED-002/GREEN-002/REG-001 | logs/política/sessão | T1.1 | B | ☐ |
| T1.3 | Implementar cadastro e recebimento verificável | Comercial | SPEC-1-002 | CA-1-03 | RED-003/GREEN-003 | registro/auditoria | T1.1 | B | ☐ |
| T1.4 | Implementar checklist e aptidão | Comercial | SPEC-1-002 | CA-1-01/04 | RED-004/GREEN-004 | checklist/decisão piloto | T1.3 | C | ☐ |
| T1.5 | Implementar ficha técnica versionada | Engenharia | SPEC-1-003 | CA-1-02/05 | RED-005/GREEN-005 | ficha v1/v2 | T1.3 | C | ☐ |
| T1.6 | Instrumentar marcos e tempo | Gestão de dados | SPEC-1-004 | CA-1-06 | RED-006/GREEN-006 | timeline | T1.3 | C | ☐ |
| T1.7 | Congelar baseline comparável | Gestão de dados | SPEC-1-004 | CA-1-07 | RED-007/GREEN-007 | relatório/amostra | T1.4,T1.5,T1.6 | D | ☐ |
| T1.8 | Cadastrar catálogo | Engenharia | SPEC-1-005 | CA-1-08 | RED-008/GREEN-008 | catálogo versionado | T1.4 | D | ☐ |
| T1.9 | Homologar regras e SLA | Engenharia | SPEC-1-005 | CA-1-09 | RED-009/GREEN-009 | ata/estados | T1.8 | E | ☐ |
| T1.10 | Registrar gates e cortes | Engenharia | SPEC-1-005 | CA-1-17 | RED-010/GREEN-010 | ledger | T1.9 | F | ☐ |
| T1.11 | Auditar VOB/OMIE | Dados | SPEC-1-006 | CA-1-10 | RED-011/GREEN-011 | matriz de auditoria | T1.1 | B | ☐ |
| T1.12 | Demonstrar backup/restauração/exportação | Dados | SPEC-1-006 | CA-1-13 | RED-012/GREEN-012 | recibo/arquivo | T1.1 | B | ☐ |
| T1.13 | Obter/aprovar modelo real | Comercial | SPEC-1-007 | CA-1-11 | RED-013/GREEN-013 | modelo ou bloqueio | T1.5 | D | ☐ |
| T1.14 | Gerar prévia sem preço | Comercial | SPEC-1-007 | CA-1-11 | RED-014/GREEN-014 | PDF/negação envio | T1.7,T1.13 | E | ☐ |
| T1.15 | Validar regressão integrada | Produto | SPEC-1-001 | CA-1-12/14/15/16 | REG-001/002 | roteiro/logs | T1.2,T1.4,T1.7,T1.10,T1.12,T1.14 | G | ☐ |
| T1.16 | Revisar qualidade do tempo | Gestão de dados | SPEC-1-004 | CA-1-06/07 | REG-003 | relatório semanal | T1.6,T1.7 | E | ☐ |
| T1.17 | Consolidar recibo/handoff | Consultor | SPEC-1-006 | CA-1-01..17 | REG-004 | manifesto | T1.10,T1.14,T1.15,T1.16,T1.11 | H | ☐ |

## Roteiro de regressão

- **REG-001:** repetir negação por papel, alteração de auditoria, retenção/anonimização e revogação.
- **REG-002:** confirmar que atualização de catálogo não altera estado aprovado.
- **REG-003:** revisar completude dos marcos e divergências amostrais.
- **REG-004:** consolidar recibos dos CA-1-01..17, cada um aprovado ou bloqueado com dono/data/evidência.
