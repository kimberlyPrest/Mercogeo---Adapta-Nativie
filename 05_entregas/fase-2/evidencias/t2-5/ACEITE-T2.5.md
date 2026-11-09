# Aceite — T2.5 Demonstrar cálculo decimal seguro com exemplos sintéticos

- **SPEC:** SPEC-2-003 · CA-2-03/04 · RED/GREEN-P2-003A · decisão D-T2.5 (09/11/2026)
- **Versão:** Skip 0.0.150 (`095b88a`), projeto "Projeto CRM-MERCO"
- **Entrega:** motor decimal (texto/inteiros, sem `Number`/`BigInt`/`eval`), validação de AST (add/sub/mul/div; profundidade ≤ 16; ≤ 256 nós), assinatura dimensional de unidades, arredondamento canônico (`half-up`, `half-even`, `down`, `up`; `normal` = `half-up`), divisão com 30 casas internas e bit de inexatidão; rota `GET /backend/v1/dimensioning/selftest` (Engenharia/Admin; 29 fixtures sintéticas fixas: 14 GREEN, 15 RED; sem persistência) e página de diagnóstico em Administração → Provas técnicas.

## Provas

| Prova | Onde | Esperado | Obtido |
|---|---|---|---|
| Testes do motor (mesmo bloco de código do hook) | `src/lib/decimalEngine.test.ts` (vitest, local) | 45/45 | 45/45 PASS |
| QA da plataforma | Skip `apply_changes` v0.0.150 | setup/estática/build/integrações PASS | PASS; suíte Skip `ran:false` (como nas versões anteriores) |
| Rota registrada no runtime real | chamada sem sessão ao backend | 401 (rota existe) | 401; rota inexistente = 404 |
| Logs do backend após aplicar | Skip Cloud, nível ≥ warn | nenhum erro | nenhum |
| GREEN-P2-003A (`10.25 m2 × 0.20 kg/m2 = 2.05 kg`) e RED-P2-003A no goja | página "Prova do cálculo decimal" | 29/29 casos | teste humano do champion |

## Aceite

Registrado pela Kim em 09/11/2026: "a T2.5 já está testada, Paulo não precisa retestar". Fonte do aceite: declaração da consultora sobre o teste do champion; esta consultoria não presenciou o teste. O cenário "calcular sem gate" do RED-P2-003A foi movido para a T2.6 pela D-T2.5.

## Limites

Não é cálculo real, não grava resultado, não abre o gate e não homologa domínio. A extração do motor para módulo compartilhado é parte da T2.18 (correção C3).
