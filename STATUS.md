# STATUS — Mercogeo

> Atualizado em 2026-10-23 · Consultoria Adapta

- **Fase 1:** concluída administrativamente com ressalvas (Kim, 30/09); T1.17 concluída em 2026-10-03 — recibo REG-004 aprovado no teste humano: 16/17 CAs demonstrados, CA-1-13 parcial/bloqueado (BLK-1..4 com dono e data). Fase 1: 17/17 tasks. Fechamento definitivo da fase pendente da validação da consultora.
- **Fase atual:** 2 — Dimensionamento e catálogo homologado.
- **Estado F2:** 6/29 tasks da tabela principal concluídas (T2.1, T2.2, T2.3, T2.13, T2.14, T2.15). T2.3 concluída em 2026-10-20 (`05_entregas/fase-2/evidencias/t2-3/ACEITE-T2.3.md`); T2.14 em 2026-10-21; T2.15 em 2026-10-22 após “Testado, funcionou” (`05_entregas/fase-2/evidencias/t2-15/ACEITE-T2.15.md`). Skip 0.0.79/f0b31fa: setup/estática/build/integrações PASS; suíte do Skip pulada (`ran:false`); Vitest local 27/27. Produção não publicada.
- **Decisão do champion (2026-10-23):** pular a T2.5 e a SPEC-2-003 neste ciclo. A DÚVIDA registrada em 22/10 (mecanismo de prova da aritmética sintética no JSVM e reconciliação de arredondamento) permanece em aberto para a consultoria, mas não bloqueia a sequência escolhida.
- **Task ativa (aguardando autorização):** **T2.31 — Criar e retomar demanda na lista de oportunidades** (SPEC-2-006; CA-2-11/UX-F2-006; pré-condição T2.15 concluída). É a primeira task da jornada principal cujo contrato não depende da T2.5: a T2.16 e demais tasks da SPEC-2-007 herdariam essa dependência; T2.4/T2.6/T2.7 seguem com pré-condições abertas. Análise read-only em `artifacts/t2-31/ANALISE-T2.31.md`; nenhum código alterado e nenhuma implementação iniciada.
- **Lacunas identificadas para a T2.31:** a área atual tem formulário e lista, mas não possui busca/filtro, não abre a demanda em detalhe persistido, não tem ação “Nova demanda” nem retorno preservando contexto. Esses são os pontos do recorte.
- **Prontidão F2:** recibo GREEN-P2-001 aprovado (`05_entregas/fase-2/PRONTIDAO-F2.md`), porém 0/4 dependências de domínio (BLK-1..4) resolvidas; gate de cálculo operacional segue **BLOQUEADO**.
- **Em paralelo, com a Mercogeo:** T2.24 (família-piloto, Comercial) e T2.27 (recuperação real, Dados) — documentais, com templates D e C.
- **Ressalvas F1:** CA-1-13 sem recuperação real (BLK-1); piloto/SLA sem homologação real (BLK-2); baseline/parecer pendente (BLK-3); família Poliureia/geotecnia sem decisão (BLK-4). Ver `05_entregas/fase-1/RECIBO-T1.17.md` e `05_entregas/fase-2/PRONTIDAO-F2.md`.
- **Limite:** nenhuma operação de cálculo real antes do gate de prontidão da família e das homologações/fixtures exigidas. Esta atualização não publica a aplicação.
