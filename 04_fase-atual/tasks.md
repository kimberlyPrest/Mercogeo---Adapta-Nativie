# As 17 tasks abaixo são o conjunto canônico operacional. A coluna Leva explicita independência por onda; pré-condições apontam apenas para tasks de levas anteriores.

| ID | Task | Dono | SPEC | Critério | Recorte da prova | Evidência esperada | Pré-condições | Leva | Status |
|---|---|---|---|---|---|---|---|---|---|
| T1.1 | Configurar papéis e acesso mínimo | Produto | SPEC-1-001 | CA-1-12: acesso sem permissão é negado | RED-001/GREEN-001 | log de autorização + captura | escopo aprovado | A | ✅ concluída |
| T1.2 | Implementar trilha crítica, retenção e revogação de sessão | Produto | SPEC-1-001 | CA-1-14, CA-1-15 e CA-1-16 | RED-002/GREEN-002/REG-001 | log antes/depois + política/teste de retenção + sessão invalidada | T1.1 | B | ✅ concluída |
| T1.3 | Implementar cadastro e evento de recebimento verificável | Comercial | SPEC-1-002 | CA-1-03 | RED-003/GREEN-003 | registro da demanda + auditoria | T1.1 | B | ✅ concluída |
| T1.4 | Implementar checklist, estados e classificação de aptidão | Comercial | SPEC-1-002 | CA-1-01, CA-1-04 | RED-004/GREEN-004 | checklist completo/incompleto + decisão piloto | T1.3 | C | ✅ concluída |
| T1.5 | Implementar ficha técnica versionada e anexos | Engenharia | SPEC-1-003 | CA-1-02 e CA-1-05 | RED-005/GREEN-005 | ficha v1/v2 + anexos vinculados | T1.3 | C | ✅ concluída |
| T1.6 | Instrumentar marcos e tempo ativo | Gestão de dados | SPEC-1-004 | CA-1-06 | RED-006/GREEN-006 | timeline e revisão semanal | T1.3 | C | ✅ concluída |
| T1.7 | Congelar baseline comparável | Gestão de dados | SPEC-1-004 | CA-1-07 | RED-007/GREEN-007 | relatório baseline + amostra | T1.4,T1.5,T1.6 | D | ✅ concluída |
| T1.8 | Cadastrar catálogo em estados e responsáveis | Engenharia | SPEC-1-005 | CA-1-08 | RED-008/GREEN-008 | registro rascunho/homologado/inativo | T1.4 | D | ✅ concluída |
| T1.9 | Homologar regras do piloto e SLA | Engenharia | SPEC-1-005 | CA-1-09 | RED-009/GREEN-009 | ata de homologação + estados | T1.8 | E | ✅ concluída |
| T1.10 | Registrar gates, donos, prazos e cortes | Engenharia | SPEC-1-005 | CA-1-17 | RED-010/GREEN-010 | ledger de gates e escalonamento | T1.9 | F | ☐ |
| T1.11 | Auditar VOB/OMIE e decisão de fonte | Dados | SPEC-1-006 | CA-1-10 | RED-011/GREEN-011 | matriz de auditoria | T1.1 | B | ☐ |
| T1.12 | Demonstrar backup, restauração e exportação | Dados | SPEC-1-006 | CA-1-13 | RED-012/GREEN-012 | recibo de restauração + arquivo exportado | T1.1 | B | ☐ |
| T1.13 | Obter e aprovar modelo real de proposta | Comercial | SPEC-1-007 | CA-1-11 | RED-013/GREEN-013 | modelo aprovado OU recibo de bloqueio com dono/data | T1.5 | D | ☐ |
| T1.14 | Gerar prévia sem preço e prova negativa de envio | Comercial | SPEC-1-007 | CA-1-11 | RED-014/GREEN-014 | PDF/prévia + tentativa de envio negada | T1.7,T1.13 | E | ☐ |
| T1.15 | Validar regressão integrada da Fase 1 | Produto | SPEC-1-001 | CA-1-12, CA-1-14, CA-1-15 e CA-1-16 | REG-001/REG-002 | roteiro integrado e logs | T1.2,T1.4,T1.7,T1.10,T1.12,T1.14 | G | ☐ |
| T1.16 | Revisar qualidade dos registros de tempo | Gestão de dados | SPEC-1-004 | CA-1-06 e CA-1-07 | REG-003 | relatório semanal assinado | T1.6,T1.7 | E | ☐ |
| T1.17 | Consolidar recibo da Fase 1 e handoff | Consultor | SPEC-1-006 | Todos CA-1-01..17 demonstrados ou bloqueados com dono | REG-004 | manifesto de evidências e status | T1.10,T1.14,T1.15,T1.16,T1.11 | H | ☐ |
