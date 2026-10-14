# Matriz de rastreabilidade — Mercogeo

| Fonte/decisão | Tratamento | Requisitos | Fase | Evidência esperada |
|---|---|---|---|---|
| Direção Kim 11/09: inteligência técnico-comercial | Núcleo do produto | RF-01–RF-28 | F1–F5 | fluxo completo demanda apta→proposta enviada, com marco intermediário pronta para envio |
| Overview: -50% tempo | K1 central | RF-01, RF-22–RF-24; RN-11 | F1, F4, F5 | baseline e comparação recebida→enviada; decomposição recebida→apta→pronta→enviada |
| Overview: -50% horas | K2 complementar | RF-23, RF-24; RN-12 | F1, F5 | tempo ativo por etapa e pessoa |
| Overview: ≥90% no SLA | K3 complementar | RF-04, RF-23, RF-24; RN-13 | F1, F4, F5 | SLA versionado e painel |
| Margem estimada×realizada | K4 secundário condicionado + proxies | RF-14–RF-16, RF-24, RF-26–RF-27; RN-14, RN-19 | F3, F5 | custo realizado homologado ou K4 inconclusivo; proxies sem falsa equivalência |
| AC-004 planilhas TESTE/BDI divergente | Não automatizar sem homologação | RF-06, RF-11, RF-13; RN-01–05 | F1–F3 | catálogo, fontes e fixtures aprovados |
| AC-005 processo real não demonstrado | Mapear casos reais | RF-01–RF-05 | F1 | 2–3 fluxos validados |
| AC-006 etapas humanas dominantes | Instrumentar e gerar documento completo | RF-18, RF-23 | F1, F4, F5 | decomposição de tempo e documento pronto |
| AC-007 regras mínimas ausentes | Estado bloqueado e decisão explícita | RF-04, RF-13, RF-16; RN-02–03 | F1, F3 | SLA, ISS, margem, alçada e arredondamento |
| AC-008 excesso de escopo | Piloto em uma família | RN-01; fora de escopo 1–10 | F1–F5 | decisão de piloto e expansão só na F5 |
| AC-009 VOB/OMIE | Auditar antes de duplicar/integrar | RF-26–RF-27; RN-15 | F1, F5 | decisão de fonte e reconciliação |
| AC-010 portais e formatos | Documento completo; portal fora | RF-18–RF-19 | F4 | PDF/editável e fronteira mensurada |
| AC-011 risco de subpreço | Governança, alçada e imutabilidade | RF-11–RF-16; RN-05, RN-08–10 | F1–F3 | histórico, aprovação e memória de cálculo |
| Segurança e dados de clientes | Acesso mínimo e auditoria | RNF-01–RNF-02, RNF-07–RNF-12 | F1–F5 | testes negativos, backup, logs e segredos |
| IA apenas assistiva | Sugestão revisável | RF-28; RN-16 | F5 | origem, confirmação e prova negativa de ação |

## Cobertura por fase

| Fase | RFs dominantes | CAs |
|---|---|---|
| F1 | RF-01–RF-06, RF-18–RF-19 (prévia parcial), RF-23, RF-26 | CA-1-01–CA-1-17 |
| F2 | RF-05–RF-10, RF-21; RNF-05, RNF-08 | CA-2-01–CA-2-16 |
| F3 | RF-11–RF-16 | CA-3-01–CA-3-11 |
| F4 | RF-17–RF-22, RF-25 | CA-4-01–CA-4-12 |
| F5 | RF-23–RF-28 | CA-5-01–CA-5-12 |


## Fase 2 — pacote ativo

Consultar `04_fase-atual/fase.md` (tabela Tasks) e as SPECs: 29 tasks, 8 SPECs, CA-2-01..16 (expansão 14/10/2026). Fase 1 concluída administrativamente com ressalvas BLK-1..4.

| CA | SPEC | Tasks |
|---|---|---|
| CA-2-01/02/10 | SPEC-2-002 | T2.3, T2.4 |
| CA-2-03/04/05 | SPEC-2-003 | T2.5, T2.6, T2.7 |
| CA-2-06/07/08 | SPEC-2-004 | T2.8, T2.9, T2.10 |
| CA-2-09 + aceite | SPEC-2-005 | T2.11, T2.12 |
| CA-2-11 | SPEC-2-006 | T2.13, T2.14, T2.15 |
| CA-2-12/13 | SPEC-2-007 | T2.16–T2.19 |
| CA-2-14/15/16 | SPEC-2-008 | T2.20–T2.23 |
| RN-21/RN-22/CA-1-13 (gate) | SPEC-2-001 | T2.1, T2.2, T2.24–T2.29 |
