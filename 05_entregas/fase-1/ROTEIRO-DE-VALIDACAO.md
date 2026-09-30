# Roteiro de validação TDD — Mercogeo F1

Dados sintéticos por padrão; casos reais exigem autorização e minimização.

- RED/GREEN-001: papel sem permissão tenta homologar → negação auditada.
- RED/GREEN-002: alteração de auditoria, retenção e sessão revogada → bloqueio/expiração auditados.
- RED/GREEN-003: recebimento ausente/retrodatado → bloqueio ou justificativa auditada.
- RED/GREEN-004: campo obrigatório ausente → aptidão bloqueada.
- RED/GREEN-005: alteração de parâmetro → nova versão com autor/origem.
- RED/GREEN-006: marcos → timeline recebida/apta/pronta/enviada e tempo ativo.
- RED/GREEN-007: baseline → congelado antes do preço, estratificado e comparável.
- RED/GREEN-008: catálogo sem fonte → não ativa.
- RED/GREEN-009: regra/SLA ausente → gate bloqueado com dono/data.
- RED/GREEN-010: bloqueio sem dono → escalonamento e corte.
- RED/GREEN-011: VOB/OMIE incompleto → decisão de fonte registrada.
- RED/GREEN-012: backup inválido/válido → falha segura/restauração comprovada.
- RED/GREEN-013: sem modelo real → bloqueio explícito.
- RED/GREEN-014: prévia sem preço → envio negado.
- REG-001..004: repetir controles, imutabilidade, qualidade do tempo e recibo CA-1-01..17.
