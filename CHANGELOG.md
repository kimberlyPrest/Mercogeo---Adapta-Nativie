# Changelog — Mercogeo

## 2026-09-12

- Publicado escopo definitivo e roadmap em cinco fases.
- Publicadas 7 SPECs da Fase 1 com critérios de aceite e roteiro TDD.
- Publicadas 17 tasks T1.1–T1.17 com donos, levas, pré-condições, evidências e status.
- Matriz CA→SPEC→task→prova publicada.
- 2026-09-11 · Paulo Romeiro · Task T1.1 concluída: papéis e autorização mínima implementados no SKIP; QA 0.0.4 passou em setup, análise estática, build, integrações e testes; teste humano de login, papel e negação por permissão aprovado.
- 2026-09-11 · Paulo Romeiro · Task T1.2 concluída: trilha de auditoria protegida, retenção de 365 dias e revogação server-side implementadas no SKIP; QA 0.0.6 passou; migration 0003 aplicada; auth-refresh, checagem de permissão e revogação autenticadas retornaram HTTP 200; teste humano aprovado.
- 2026-09-11 · Paulo Romeiro · Task T1.3 concluída: cadastro de oportunidade e recebimento verificável implementados no SKIP; QA 0.0.7 passou; migration 0004 aplicada; criação autenticada retornou HTTP 201, entradas inválidas HTTP 400, acesso sem sessão HTTP 401; teste humano aprovado.
- 2026-09-11 · Paulo Romeiro · Task T1.4 concluída: checklist, estados e aptidão server-side implementados; exceções restritas a Engenharia/Admin; migration 0005 aplicada; QA 0.0.13 passou; avaliação autenticada HTTP 200; listagem e cards detalhados validados; teste humano aprovado.
- 2026-09-11 · Paulo Romeiro · DEBUG task T1.4: rota parametrizada e apresentação incompleta → rota fixa de aptidão, listagem persistida e checklist/card detalhados → corrigido.
- 2026-09-12 · Paulo Romeiro · Task T1.5 concluída: ficha técnica versionada com parâmetros (nome/valor/unidade/origem), pendências, anexos protegidos e histórico imutável; migrations 0006 e 0007 aplicadas; QA 0.0.21 passou; GREEN comprovado via API real (v1 criada, alteração gerou v2 server-side, multipart com anexo salvo, histórico listado); teste humano aprovado.
- 2026-09-12 · Paulo Romeiro · DEBUG task T1.5: multipart em rota customizada e campo JSON lido como bytes brutos via record.get → upload nativo do PocketBase + validação server-side via getString/JSON.parse → corrigido.
- 2026-09-15 · Paulo Romeiro · Task T1.6 concluída: marcos recebida→apta→pronta→enviada com timestamps server-side e tempo ativo por etapa com pausa justificada; migration 0009 aplicada; QA 0.0.23 passou; GREEN via API real (received e apt automáticos, sequência validada, duplicados negados, tempo único em andamento, pausa sem justificativa negada, 401 sem sessão); teste humano aprovado.
- 2026-09-15 · Paulo Romeiro · DEBUG task T1.6: demandas apta criadas antes da instrumentação não tinham eventos → migration 0011 retroalimentou recebida/apta com os timestamps server-side originais → corrigido (QA 0.0.24).
