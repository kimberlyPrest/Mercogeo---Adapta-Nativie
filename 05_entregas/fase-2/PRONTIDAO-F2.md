# Prontidão da Fase 2 — Mercogeo (GREEN-P2-001)

- **Data:** 2026-10-03
- **Elaborado por:** Merco IA, assistente do champion Paulo Romeiro, sob autorização de 2026-10-03 15:10 ("Sim, pode implementar a T2.1")
- **Prova:** GREEN-P2-001 — recibo de prontidão e fontes
- **SPEC:** `04_fase-atual/specs/spec-2-001.md` · **Handoff recebido:** `05_entregas/fase-1/RECIBO-T1.17.md` (BLK-1..4)
- **Gate de cálculo operacional:** 🔒 **BLOQUEADO** — nenhuma pendência resolvida ainda; nada é ativação, nenhuma prova simulada é declarada real

## Contrato

Recibo de prontidão que distingue **autorização documental** (Kim, 30/09), **prova técnica** e **homologação real**. Cada dependência tem status, prova exigida, dono e vínculo verificável — nunca texto autodeclarado. Este registro **não** encerra a T1.17 nem comprova os CAs faltantes da Fase 1: ele estrutura onde essas provas devem chegar.

## Painel de prontidão

| Dependência | Origem | Status | Prova exigida | Dono | Vínculo verificável |
|---|---|---|---|---|---|
| RN-21 · decisão piloto/SLA | BLK-2 | ⬜ PENDENTE | Decisão de piloto + SLA homologados com ata/evidência (template A) | Engenharia | `05_entregas/fase-2/templates/TEMPLATE-A-piloto-sla.md` · estrutura T1.9 (QA 0.0.35) |
| RN-22 · baseline comparável | BLK-3 | ⬜ PENDENTE | Baseline congelado sobre dados reais (T1.7) ou parecer explícito de limitação (template B) | Engenharia | `05_entregas/fase-2/templates/TEMPLATE-B-baseline-parecer.md` · baseline T1.7 (QA 0.0.29) |
| CA-1-13 · recuperação real | BLK-1 | ⬜ PENDENTE | Backup completo (dados, anexos, configuração) + restauração em instância isolada + comparação antes/depois (template C) | Dados | `05_entregas/fase-2/templates/TEMPLATE-C-recuperacao-real.md` · backup T1.12 (QA 0.0.46) |
| Família-piloto e fixture | BLK-4 | ⬜ PENDENTE | Resolução ou exclusão justificada do modelo Poliureia/geotecnia + fixture assinada (template D) | Comercial + Engenharia | `05_entregas/fase-2/templates/TEMPLATE-D-familia-fixture.md` · achado T1.15 (family=geotecnia nos 2 modelos) |

**Resumo:** 0/4 resolvidas · 4 pendentes com dono e prova exigida · gate permanece fechado até todas chegarem.

## Regras do registro (SPEC-2-001)

- Gate é **específico da família aprovada** — não escolher família pelo parâmetro mais recente; aprovação perde validade se mudar piloto/SLA ou versão referenciada, e o registro anterior é preservado.
- Só Engenharia/Admin assina prontidão; vínculos apontam para registros verificáveis.
- Prova técnica ≠ homologação real ≠ autorização documental — as três colunas ficam explícitas quando cada prova chegar.
- Sem importar dados reais nem ativar cálculo enquanto o gate estiver fechado; desenvolvimento isolado com massa sintética pode avançar (T2.3).

## Como registrar a chegada de cada prova

1. O responsável preenche o template correspondente (A–D) com a evidência real (arquivo, ata, log ou recibo).
2. O vínculo é conferido contra o registro citado (QA/migration do changelog).
3. A linha correspondente do painel passa a PREENCHIDA com o vínculo — **nada é marcado resolvido sem evidência**.
4. Com as 4 provadas, a aprovação formal (`POST /backend/v1/dimensioning/readiness/approve`, T2.2) assina o gate por família — T2.1 concluída só entrega o recibo e os templates, não a aprovação.

## Verificação

- Conferência cruzada: cada vínculo aponta para prova existente no repo (recibo T1.17, changelog, matrizes, SPEC-2-001).
- Task documental: sem código, sem migration; QA de build não aplicável.
- Sem tokens, senhas ou dados pessoais (LGPD).
