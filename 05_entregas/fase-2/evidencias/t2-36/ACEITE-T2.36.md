# ACEITE-T2.36 — Organizar entrada administrativa e evidências existentes

- **Task:** T2.36 · SPEC-2-006 · critérios CA-2-11; UX-F2-006 · prova REG-P2-006 + UX-006-ADM
- **Champion/validador:** Paulo Romeiro · **Data do aceite:** 2026-10-29
- **Versão:** Skip 0.0.147/41c68e4 (desenvolvimento; produção não publicada)

## Escopo entregue

- Página `/administracao` (`AdminIndex.tsx`) — índice administrativo com **11 destinos**: os 10 da SPEC (Catálogo, Regras e SLA do piloto, Baseline, Backup e exportação, Auditoria VOBI/OMIE, Gates e cortes, Modelos de proposta, Prévia sem preço, Qualidade do tempo, Marcos e tempo) **+ Unidades e dimensões** (decisão do champion; a T2.16 deixou a rota `/unidades` sem item de menu aguardando este índice).
- Cada destino abre a **seção existente** por entrada contextual (`/painel-tecnico?secao=<id>` — âncoras já implementadas — ou `/unidades`): nenhuma seção foi extraída ou redesenhada; nenhuma linha do painel legado foi alterada.
- Menu lateral: entrada “Índice da administração” sob o rótulo “Administração e evidências”; os 14 itens existentes preservados; item ativo marcado em `/administracao` e `/unidades`; títulos de página corretos.
- Home `/dashboard`: card destacado para o índice; cards existentes preservados (decisão do champion).
- Sem endpoint, migration, schema ou permissão nova; leitura segue `viewDashboard` (todos os papéis com painel); mutações continuam negadas no servidor; URLs antigas (`/painel-tecnico?secao=<id>`) intactas.

## Matriz esperado × obtido (UX-006-ADM / REG-P2-006)

| # | Cenário | Esperado | Obtido | Resultado |
|---|---|---|---|---|
| 1 | Índice lista destinos autorizados | Os 10 da SPEC + Unidades, sem destino inventado | Teste de unidade: ids exatos em ordem; rótulos idênticos às seções existentes | PASS |
| 2 | Entrada contextual abre seção real | Cada card abre `/painel-tecnico?secao=<id>` ou `/unidades` | Teste de unidade das URLs + teste humano (cliques em Catálogo/Baseline/Unidades) | PASS |
| 3 | Não extrair nem redesenhar | Diff não move seções do painel legado | Diff revisado: Dashboard.tsx intocado | PASS |
| 4 | Não ampliar acesso | Nenhuma permissão nova; servidor é a autoridade | Diff sem mudança de permissão; `sectionsForRole` intacto; falha fechada sem papel (teste) | PASS |
| 5 | Estados honestos + contrato UX | Estado vazio com papel; foco visível; sem rolagem horizontal | `role="status"` no estado vazio; foco outline; teste humano mobile/teclado | PASS |
| 6 | Menu e home organizados | Índice acessível pelo menu e pela home sem duplicar listas | Entrada no menu + card na home; itens antigos preservados; teste humano | PASS |

## Verificações automáticas

- QA Skip 0.0.147/41c68e4: setup, análise estática, build e integrações **PASS**; suíte da plataforma pulada (`ran:false`).
- Regressão local do zero: **165/165 em 10 arquivos** (exit 0) — navigation 17 (11 existentes + 6 novos da T2.36: destinos exatos, URLs contextuais, rótulos idênticos, descrições, papéis, URL estável).

## Teste humano

- Roteiro entregue em 29/10 (índice, destinos, item ativo, home, Comercial, mobile/teclado). Champion: **“Funcionou”**. Escopo alterado (navegação/organização) integralmente coberto pelo roteiro; não há ação de servidor nova nesta task.

## Limites e pendências fora da task

- O índice navega; não altera permissões nem conteúdo das seções — extração/redesenho das telas administrativas continua exigindo recorte próprio.
- Fix do 409 amigável para item de catálogo já composto (T2.17) segue pronto e pendente de aplicação.
- DÚVIDA de produto do ciclo de vida das unidades (e033ba6a) segue aberta para decisão.
