# ACEITE-T2.34 — Entender e preparar prontidão sem digitar IDs

- **Task:** T2.34 · SPEC-2-001 · critério UX-F2-001 (proposto) · prova UX-001-UI
- **Champion/validador:** Paulo Romeiro · **Data do aceite:** 2026-10-29
- **Versão:** Skip 0.0.143/f685e0f (desenvolvimento; produção não publicada)

## Escopo entregue

- Seção Prontidão (`/painel-tecnico?secao=prontidao`) mantém painel de leitura (badge APROVADO/INVALIDADO/BLOQUEADO, família, detalhe, bloqueios com chave/motivo/dono/data).
- Formulário de assinatura: os dois inputs de ID PocketBase de 15 caracteres foram substituídos por seletores por rótulo — **SLA homologado** (`pilot_params` com `param_type=sla` e `decision=homologado`; rótulo família — valor unidade · fonte) e **baseline congelado** (`baseline_snapshots`, lista autorizada existente, restrita aos registros do próprio usuário; rótulo família — janela · congelado em).
- Estados do contrato UX: carregando, vazio com causa e próximo passo (“Homologue em Administração → Regras e SLA do piloto…”), falha; Comercial continua vendo o painel sem formulário (permissão `approveReadiness` inalterada).
- `approveReadiness` e payload **idênticos campo a campo** (prova de unidade); backend revalida como antes. Sem endpoint, migration, schema ou permissão nova. Sem seletor de fixture estruturada no gate (proibição da SPEC respeitada). Evidências de recuperação/recibo F1 seguem referência textual.

## Matriz esperado × obtido (UX-001-UI)

| # | Cenário | Esperado | Obtido | Resultado |
|---|---|---|---|---|
| 1 | Carregar a seção Prontidão como Engenharia | Painel + formulário renderizam sem erro | 1º teste: crash (TDZ na derivação das opções); corrigido em 0.0.143; reteste do champion: “Funcionou” | PASS (após correção) |
| 2 | Seletor de SLA homologado | Opções rotuladas por família/valor/unidade/fonte, sem ID | Prova de unidade: rótulo contém família/valor/unidade/fonte e não contém o ID | PASS |
| 3 | Seletor de baseline congelado | Apenas baselines do próprio usuário (regra existente) | Opções = lista autorizada carregada; rótulo sem ID | PASS |
| 4 | Estado vazio honesto | Sem SLA homologado → dica com causa e próximo passo | “Nenhum parâmetro de SLA homologado. Homologue em Administração → Regras e SLA…” | PASS |
| 5 | Payload do approveReadiness | Mesmos campos do contrato vigente | Teste de unidade: chaves e valores idênticos campo a campo | PASS |
| 6 | Sem seletor de fixture no gate | Ausência no diff | Confirmado na revisão do diff | PASS |

## Verificações automáticas

- QA Skip 0.0.143/f685e0f: setup, análise estática, build e integrações **PASS**; suíte da plataforma pulada (`ran:false`).
- Regressão local do zero: **153/153 em 9 arquivos** (exit 0).
- Prova de unidade T2.34 (`readinessOptions.test.ts`): **6/6**.

## Teste humano

- 1ª rodada (15:19): **falhou** — “Deu erro ao carregar a seção prontidão”. Causa raiz: derivação `slaOptions` usava o estado `pilotParams` antes da declaração (TDZ, ReferenceError no primeiro render; nenhum request de readiness nos logs do servidor). Correções 0.0.142 (derivação movida; QA reprovou por declaração emendada em uma linha) e 0.0.143 (QA PASS).
- 2ª rodada (15:33): **aprovada** — “Funcionou”. O clique em “Assinar prontidão” não foi exercitado; o código de envio não foi alterado nesta task (payload idêntico, prova de unidade).

## Limites e pendências fora da task

- Baseline: somente registros criados pelo próprio usuário aparecem (regra de acesso existente, sem ampliação).
- Fix do 409 amigável para item de catálogo já composto (T2.17) segue pronto e pendente de aplicação.
- DÚVIDA de produto do ciclo de vida das unidades (e033ba6a) segue aberta para decisão.
