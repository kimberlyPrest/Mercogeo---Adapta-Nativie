# RECIBO T1.17 — Fase 1 Mercogeo (REG-004)

- **Data:** 2026-10-03
- **Elaborado por:** Merco IA, assistente do champion Paulo Romeiro, sob autorização de 2026-10-03 14:11 ("Sim, pode implementar a T1.17")
- **Prova:** REG-004 — manifesto de evidências CA-1-01..17 e status
- **Fechamento:** recibo testado e aprovado pelo champion em 2026-10-03 14:29 ("Testei o recibo da T1.17 e aprovou"); T1.17 concluída com bloqueios justificados

## Escopo e método

Este recibo consolida a rastreabilidade dos 17 critérios de aceite da Fase 1. Cada CA está **DEMONSTRADO** (com evidência verificável: task, QA, migrations e teste humano) ou **BLOQUEADO** (com dono, data de abertura e prova exigida). Nenhuma prova simulada é declarada como real. Fontes: `CHANGELOG.md`, `05_entregas/fase-1/` (matrizes, roteiro TDD, STATUS-FECHAMENTO) e `04_fase-atual/specs/`.

Task documental: nenhum código, migration ou coleção foi alterado.

## Manifesto CA-1-01..17

| CA | Resultado exigido | SPEC | Task(s) | Prova | QA | Status |
|---|---|---|---|---|---|---|
| CA-1-01 | Demanda real registrada com recebimento verificável e checklist | 002 | T1.4 | GREEN-004 (RED/GREEN-003/004) | 0.0.13 | ✅ demonstrado |
| CA-1-02 | Ficha técnica reúne parâmetros, documentos e pendências | 003 | T1.5 | GREEN-005 (RED/GREEN-005) | 0.0.21 | ✅ demonstrado |
| CA-1-03 | Cadastro de oportunidade + recebimento verificável | 002 | T1.3 | GREEN-003 | 0.0.7 | ✅ demonstrado |
| CA-1-04 | Classificação de aptidão auditável | 002 | T1.4 | GREEN-004 | 0.0.13 | ✅ demonstrado |
| CA-1-05 | Ficha versionada sem reentrada (v1/v2, autor, origem) | 003 | T1.5 | GREEN-005 | 0.0.21 | ✅ demonstrado |
| CA-1-06 | Marcos + tempo ativo medidos | 004 | T1.6, T1.16 | GREEN-006 + REG-003 | 0.0.23 / 0.0.58 | ✅ demonstrado |
| CA-1-07 | Baseline congelado e comparável | 004 | T1.7 | GREEN-007 | 0.0.29 | ✅ demonstrado |
| CA-1-08 | Catálogo com estados, dono, fonte e vigência | 005 | T1.8 | GREEN-008 | 0.0.32 | ✅ demonstrado |
| CA-1-09 | Regras do piloto e SLA homologados (estrutura neutra) | 005 | T1.9 | GREEN-009 | 0.0.35 | ✅ demonstrado (estrutura) — valores reais pendem da Mercogeo |
| CA-1-10 | Auditoria VOBI/OMIE + decisão de fonte | 006 | T1.11 | GREEN-011 | 0.0.40 | ✅ demonstrado |
| CA-1-11 | Modelo real aprovado + prévia SEM PREÇO com envio negado | 007 | T1.13, T1.14 | GREEN-013/014 | 0.0.53 / 0.0.54 | ✅ demonstrado |
| CA-1-12 | Papéis e acesso mínimo; negação auditada | 001 | T1.1, T1.15 | GREEN-001 + REG-001 | 0.0.4 / 0.0.55 | ✅ demonstrado |
| CA-1-13 | Backup, restauração real e exportação | 006 | T1.12 | GREEN-012 (parcial) | 0.0.46 | ⚠️ PARCIAL — bloqueado (ver Bloqueios) |
| CA-1-14 | Trilha crítica protegida (imutável) | 001 | T1.2, T1.15 | GREEN-002 + REG-001 | 0.0.6 / 0.0.55 | ✅ demonstrado |
| CA-1-15 | Retenção de auditoria (365 dias) | 001 | T1.2 | GREEN-002 | 0.0.6 | ✅ demonstrado |
| CA-1-16 | Revogação de sessão | 001 | T1.2, T1.15 | GREEN-002 + REG-001 | 0.0.6 / 0.0.55 | ✅ demonstrado |
| CA-1-17 | Gates com dono, prazo, escalonamento e cortes | 005 | T1.10 | GREEN-010 | 0.0.38 | ✅ demonstrado |

**Resumo:** 16 demonstrados · 1 parcial/bloqueado (CA-1-13) · nenhuma simulação declarada como prova real.

## Bloqueios (com dono e data)

| ID | Bloqueio | Dono | Aberto | Prova exigida para destravar |
|---|---|---|---|---|
| BLK-1 | CA-1-13 — recuperação real em instância isolada não demonstrada (T1.12 provou backup/export/hash/falha segura; restauração com comparação antes/depois de registros permanece simulada) | Dados | 2026-09-30 (ressalva Kim) | Backup completo (dados, anexos, configuração) + restauração em instância isolada com comparação de conteúdo antes/depois |
| BLK-2 | Homologação real de piloto/SLA sem evidência (estrutura T1.9 neutra; nenhum valor real homologado) | Engenharia | 2026-09-30 | Decisão de piloto + SLA homologados com ata/evidência |
| BLK-3 | Baseline/parecer de comparabilidade sem prova final (T1.7 congelou estrutura; comparabilidade com dados reais pendente) | Engenharia | 2026-09-30 | Baseline congelado sobre dados reais ou parecer explícito de limitação |
| BLK-4 | Família do modelo Poliureia/geotecnia sem decisão (T1.15 achou family=geotecnia nos dois modelos aprovados, inclusive no registro nomeado Poliureia) | Comercial + Engenharia | 2026-09-30 | Resolução ou exclusão justificada do modelo |

## Handoff para a Fase 2 (o que a T2.1 herda)

- A T2.1 (SPEC-2-001, prova GREEN-P2-001) consome exatamente os bloqueios BLK-1..4: recibo de prontidão com vínculos verificáveis, não texto autodeclarado.
- **Gate de cálculo operacional: FECHADO** até BLK-1..4 resolvidos. Trabalho documental e desenvolvimento isolado com massa sintética podem avançar (ex.: T2.3).
- Referências: `05_entregas/fase-1/STATUS-FECHAMENTO.md` (decisão Kim, 30/09) e `04_fase-atual/specs/spec-2-001.md`.
- Achado preservado: o sistema externo é **VOBI** (documentos grafam VOB) — correção do dono de 2026-09-15; implementação e interface usam VOBI.

## Verificação deste recibo

- **Método:** conferência cruzada de cada linha contra `CHANGELOG.md`, `05_entregas/fase-1/fase-1.md`, `matriz-tasks-fase-1.md`, `matriz-specs-fases.md` e as 7 SPECs arquivadas — todas as referências existem no repo em 2026-10-03.
- Sem código alterado nesta task; sem migration; QA de build não aplicável.
- **Limitação:** os logs de QA (códigos HTTP por prova) vivem no histórico do SKIP (versões 0.0.4–0.0.58); este recibo referencia os registros canônicos do repositório.

## Status do fechamento

- Fase 1: encerrada administrativamente com ressalvas (Kim, 30/09) — decisão preservada; fechamento definitivo pendente da validação da consultora.
- T1.17: recibo entregue, testado e aprovado pelo champion (2026-10-03 14:29); task concluída com bloqueios justificados (BLK-1..4 registrados com dono e data).
