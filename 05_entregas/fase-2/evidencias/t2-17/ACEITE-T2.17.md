# ACEITE-T2.17 — Ligar entradas da composição aos parâmetros da ficha

- **Task:** T2.17 (SPEC-2-007; CA-2-12; UX-F2-007)
- **Champion/validador:** Paulo Romeiro
- **Data do aceite:** 2026-10-29
- **Versões Skip:** 0.0.88/f92c967 (implementação) → 0.0.89/5eef482 (restauração do campo Fonte) → 0.0.138/90e7e4f (entrada manual sem contexto) → 0.0.139/b9d55f8 (dica de unidades homologadas; versão corrente no aceite)
- **Pré-condições:** T2.16 e T2.33 concluídas (27/10).

## O que foi entregue

- **Server-side (`composition_versions.js`, create e revise):** vínculo opcional `sheet_param` {nome, unidade, origem, mín, máx} por insumo; rejeições específicas `sheet_unit_mismatch` (unidade do vínculo diverge do insumo), `sheet_range_invalid` (limites não decimais ou invertidos) e `unit_not_homologado` (saída e insumos) — prova server-side da regra declarada na T2.16 (RED-P2-007A).
- **Frontend (Biblioteca):** coluna "Parâmetro da ficha (opcional)" na tabela de insumos; seletor por nome com parâmetros reais da ficha via `?oportunidade=<id>`; entrada manual nome/unidade com aviso honesto quando não há contexto (0.0.138); dica "Homologadas: …" sob a unidade de saída e dica de código homologado no insumo (0.0.139). Sem editor de fórmula (T2.18), sem fixture estruturada (T2.19), sem conversão de unidade e sem cálculo.

## Verificação automática

- Vitest local: **153/153 em 9 arquivos** (13 casos novos do vínculo), revalidado durante o ciclo.
- QA Skip 0.0.139: setup/estática/build/integrações **PASS**; suíte da plataforma pulada (`ran:false`).

## Teste humano (2026-10-29, 4 rodadas de debug)

1. **Rodada 1 — seletor vazio:** causa raiz: lista só carregava com `?oportunidade=`; corrigido com entrada manual + aviso (0.0.138). Debug: `06_notas/debug/debug-2026-10-28-t2-17-parametros-vazios.md`.
2. **Rodada 2 — "unidade não homologada":** regra server-side correta; UI não exibia os códigos homologados; corrigido com a dica (0.0.139).
3. **Rodada 3 — bloqueio de dados:** o `m2` testado era a unidade inativada na T2.16; comportamento correto. Expôs conflito de design da T2.16 (código inativo fica permanentemente indisponível) — **DÚVIDA de produto registrada** no changelog (commit e033ba6a) e na seção Emendas de `04_fase-atual/fase.md`; o teste prosseguiu com a unidade homologada existente, por decisão do champion.
4. **Rodada 4 — "Value must be unique":** causa raiz demonstrada: índice único `catalog_item_id+version` sem pré-checagem no hook; o item de catálogo usado já tinha composição. Comportamento de dados correto, mensagem genérica; **fix preparado** (409 `catalog_item_already_composed`) e pendente de aplicação por queda do conector Skip — registrado como pendência pós-aceite.

## Confirmações do champion

- Negativas confirmadas: unidade do vínculo divergente; faixa invertida; unidade não homologada (saída e insumo); item de catálogo já composto (400 genérico, mensagem a melhorar).
- **Caminho feliz confirmado:** "Consegui criar um rascunho após mudar o item do catalogo e digitar numero na composição." (13:36)
- **Papel Comercial confirmado:** "Confirmado, comercial não cria" (13:42) — criação negada ao Comercial.

## Limites declarados

- Sem editor de fórmula, sem fixture estruturada, sem conversão de unidade, sem cálculo; gate de cálculo operacional permanece bloqueado.
- A releitura do vínculo salvo continua impossível (mesma emenda de leitura por ID de `composition_versions` registrada na T2.33).
- Pendências pós-aceite (não reabrem a task): fix do 409 amigável (`work/t2-17/hook_fix_v1.js`, pronto e validado sintaticamente); DÚVIDA de produto do ciclo de vida das unidades.
