# Histórico operacional

## 2026-10-20 — Jornada e UX da Fase 2

Kim autorizou a revisão documental e o commit. Preservados IDs, evidências e aceites T2.1/T2.2/T2.13 (conclusão T2.13 sincronizada em f533682); T2.3 continua separada. T2.30–36 detalham experiência. Reordenados fixture antes da homologação e guard antes de confirmar/congelar; GREEN-P2-008B atribuída a T2.7. T2.33 não pressupõe seletor de caso ainda inexistente; T2.29 conserva schema atual, com contrato real como evidência documental e validação complementar nos fluxos de cálculo/composição. Administração por índice contextual aprovada no CA-2-11. Nenhum software, integração ou cálculo real implementado por esta revisão.

Histórico anterior preservado em [CHANGELOG.md](CHANGELOG.md). Novos registros devem ser anexados neste arquivo.

## 2026-10-20 — Aceite próprio da T2.3

Champion (Paulo) confirmou o aceite próprio da T2.3: rascunho persistido e duplicidade com motivo real, sem novo registro. Fechamento exclusivamente documental — sem implementação de código, homologação ou criação de composições; gate de cálculo operacional permanece bloqueado. Provas: RED/GREEN-P2-002A (duplicidade geotecnia COMP-TESTE-01 v1 id26ljaq5sixv5unr, catálogo krkue1xg6fiwlfe; 409 com motivo real e uma única versão) em `05_entregas/fase-2/evidencias/t2-13/PROVA-T2.13.md` e nota `06_notas/debug/debug-2026-10-19-t2-13-menu-placeholder.md` (GET 200 com uma única v1). Recibo: `05_entregas/fase-2/evidencias/t2-3/ACEITE-T2.3.md`.

## 2026-10-21 — Conclusão T2.14

- 2026-10-21 · Paulo Romeiro · Task T2.14 concluída: teste humano aprovado nos cinco cenários de navegação por papel, acesso contextual às 14 funções existentes, URLs legadas e mobile. Skip 0.0.74/5c9a014: setup/estática/build/integrações PASS; suíte do Skip pulada (`ran:false`); Vitest local 16/16 dentro das limitações documentadas. Preview: GET sem sessão 401, leitura autenticada 200, Comercial sem criação/homologação (403), duplicidade geotecnia HTTP 409 com motivo real, sem nova composição/versão e com evento de rejeição em `audit_logs`; gate de cálculo permanece bloqueado. Recibo `05_entregas/fase-2/evidencias/t2-14/ACEITE-T2.14.md`.

## 2026-10-21 — Aprendizado T2.14

Verificação rápida de navegação client-side pode observar o foco do destino anterior antes do paint. Evidência consolidada em `05_entregas/fase-2/evidencias/t2-14/PROVAS-T2.14.md`: uma varredura inicial foi inconsistente; navegação isolada após render estável confirmou 14/14. Candidato reutilizável em `06_notas/aprendizado-continuo/AP-2026-10-21-1052-foco-client-side-estavel.md`: aguardar estabilidade e verificar cada âncora isoladamente; não inferir PASS de snapshot imediato.

## 2026-10-22 — Debug T2.15

- 2026-10-22 · Paulo Romeiro · DEBUG task T2.15: criação de rascunho retornou 400 “Informe o item do catálogo da composição.” → causa raiz confirmada: o formulário extraído aceitava texto livre para `catalog_item_id`, enquanto o endpoint exige o ID real de um registro de catálogo com formato de 15 caracteres minúsculos; logs não guardavam o corpo, portanto o valor enviado não foi inferido. Corrigido em Skip 0.0.79/f0b31fa com seleção dos registros via `getCatalogItems` existente e bloqueio de envio sem seleção válida. QA: setup/estática/build/integrações PASS; suíte Skip pulada (`ran:false`); Vitest focado 8/8 e regressão local 12/12; preview mostrou opções e seleção sem submissão. Nenhum registro criado, produção não publicada. Reteste humano pendente. Debug: `06_notas/debug/debug-2026-10-22-t2-15-id-catalogo.md`.

## 2026-10-22 — Conclusão T2.15

- 2026-10-22 · Paulo Romeiro · Task T2.15 concluída após confirmação explícita do teste humano (“Testado, funcionou”). Biblioteca em rota própria `/biblioteca`; menu e URL legada preservados; listagem/criação usam serviços existentes; seleção válida de item do catálogo corrigida em Skip 0.0.79/f0b31fa. QA Skip: setup/estática/build/integrações PASS, testes da plataforma pulados (`ran:false`). Vitest local repetido: catálogo 8/8, navegação/rascunho 12/12, mensagens PocketBase 7/7. Logs não confirmaram novo HTTP 201 após o reteste; não se afirma código HTTP ou versão de registro. Recibo `05_entregas/fase-2/evidencias/t2-15/ACEITE-T2.15.md`; verificação `artifacts/t2-15/VERIFICACAO-T2.15.md`. Produção não publicada; gate de cálculo operacional continua bloqueado.

## 2026-10-22 — DÚVIDA de escopo T2.5 (bloqueio pré-implementação)

- 2026-10-22 · Análise solicitada por Paulo Romeiro · A T2.5 depende apenas da T2.3 concluída, mas exige validar aritmética decimal no JSVM e demonstrar a fixture sintética `10.25 m2 × 0.20 kg/m2 = 2.05 kg` antes das dependências do cálculo real. O único fluxo especificado de cálculo real (`/backend/v1/dimensioning/calculate`) exige gate aberto, oportunidade apta, ficha válida e composição homologada; T2.5 não depende dessas tarefas. No Skip 0.0.79/f0b31fa não existem motor aritmético, endpoint de cálculo/simulação nem coleção `dimensioning_runs`; hooks JSVM executam em goja, sem Node, e o projeto não contém runner de teste no JSVM. **DÚVIDA para consultoria:** confirmar se a task se limita a módulo decimal puro + harness/rota de teste isolada para validar o runtime goja, sem UI/persistência/endpoint de produto/cálculo real, ou emendar a SPEC para criar simulação pré-gate via endpoint/UI definindo persistência, auditoria e isolamento de dados. Contrato de rounding também precisa ser reconciliado: SPEC-2-003 usa `half-up`/`half-even`/`down`; SPEC-2-002 e o hook atual aceitam `normal`/`up`/`down`, sem mapeamento documentado. Confirmar se unidade incompatível é teste de T2.5 ou pertence às tasks de dimensões/unidades. Recibo da análise: `artifacts/t2-5/ANALISE-T2.5.md`. Não se alterou código, SPEC, migration, schema, configuração ou ambiente; nenhuma implementação iniciada.
