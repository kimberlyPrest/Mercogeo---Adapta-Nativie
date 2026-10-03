# Evidências T2.2 — Gate de prontidão por família (RED/GREEN/REG-P2-001)

- **Data:** 2026-10-03 · **Versões QA:** 0.0.59, 0.0.60, 0.0.61 (setup, análise estática, build, integrações e testes — todos passaram)
- **Migrations:** 0044 (phase2_readiness, CRUD direto negado), 0045 (usuários sintéticos de prova), 0046 (cleanup das fixtures)
- **Runner real:** vitest 3.x (`pnpm test`) — substituiu o placeholder; suíte `src/lib/auth/permissions.test.ts` (permissões approveReadiness)

## Provas via API real (10/10 PASS)

| Prova | Resultado | Evidência |
|---|---|---|
| GET readiness autenticado | 200, gate bloqueado | log da rodada 1 |
| RED: aprovar sem prova | 409 com 2 pendências (motivo/dono/data) | rodada 2 |
| RED: vínculos inexistentes | 409 | rodada 2 |
| RED: SLA de outra família | 409 — gate não muda de família | rodada 2 |
| REG: Comercial assina | 403 | rodada 2 |
| GREEN: aprovar com vínculos | 200, família geotecnia, assinatura auditada | rodada 2 |
| GET pós-aprovação | 200 aprovado/geotecnia | rodada 2 |
| CRUD direto na coleção | 403 | rodada 2 |
| GET sem sessão | 401 | rodada 2 |
| POST sem sessão | 401 | rodada 2 |

## Invalidação real (migration 0046)

A deleção do SLA referenciado provou a invalidação: GET retornou `invalidado` com o motivo "Vínculo deixou de ser válido: RN-21" e o registro anterior preservado.

## Debug registrado

- 409 de negócio via `e.json` (padrão T1.12) — `conflictError` nativo não atende o contrato do card.

## Estado final

Gate de cálculo operacional: **BLOQUEADO** (registro de prova marcado como invalidado após cleanup — correto: as provas reais BLK-1..4 continuam pendentes).
