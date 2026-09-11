# Roteiro de validação TDD — Mercogeo Fase 1

Dados sintéticos por padrão; casos reais somente com autorização, minimização e responsável. Cada execução gera log/captura/recibo.

| ID | RED — antes | GREEN — esperado | REGRESSÃO |
|---|---|---|---|
| RED-001/GREEN-001 | usuário sem papel tenta homologar | negar e registrar ator/ação | repetir após papel |
| RED-002/GREEN-002 | alterar auditoria/sessão desligada | negar/auditar e invalidar sessão | retenção/exportação |
| RED-003/GREEN-003 | recebimento ausente/retrodatação | bloquear ou justificar auditado | revisar timeline |
| RED-004/GREEN-004 | aptidão sem campo | apontar pendência e bloquear | completar campo |
| RED-005/GREEN-005 | parâmetro sem versão | versionar origem/autor | abrir v1/v2 |
| RED-006/GREEN-006 | marcos ausentes | timeline completa | revisão semanal |
| RED-007/GREEN-007 | baseline contaminado | congelar antes do preço | recalcular |
| RED-008/GREEN-008 | catálogo sem fonte | bloquear ativação | homologar fixture |
| RED-009/GREEN-009 | preço sem SLA | bloquear com dono/data | liberar após aprovação |
| RED-010/GREEN-010 | gate sem dono/data | escalar e registrar corte | revisar ledger |
| RED-011/GREEN-011 | fonte externa incompleta | registrar decisão | repetir leitura |
| RED-012/GREEN-012 | backup inválido | falhar sem corromper; exportar | restaurar válido |
| RED-013/GREEN-013 | sem modelo real | bloquear e gerar recibo | aprovar modelo |
| RED-014/GREEN-014 | prévia tenta envio | marcar NÃO ENVIAR e negar | gerar nova |
| REG-001 | repetir controles de acesso/auditoria/retenção | passar sem regressão | relatório |
| REG-002 | atualizar catálogo após aprovado | aprovado permanece imutável | comparar memória |
| REG-003 | tempo incompleto | divergências identificadas | reprocessar |
| REG-004 | recibo incompleto | consolidação bloqueia | manifesto |

Fixtures mínimas: F1 demanda completa, F2 incompleta, F3 catálogo sem homologação, F4 usuário sem permissão, F5 modelo de proposta sem preço. Nenhuma fixture autoriza produção, envio externo, integração ou custo não homologado.
