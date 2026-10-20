# PROVA T2.13 — Restaurar motivo real dos erros de negócio (RED/GREEN-P2-006A)

**Data:** 2026-10-19 · **Task:** T2.13 (SPEC-2-006, CA-2-11 recorte 5) · **Versões:** 0.0.72–0.0.73  
**Autorizada por:** Paulo Romeiro ("Sim, pode implementar a T2.13", 2026-10-19 10:32)

## RED-P2-006A (baseline v0.0.71, antes da correção)

Suíte nova `src/lib/pocketbase/errors.test.ts` executada localmente contra o `errors.ts` da 0.0.71 (SDK PocketBase 0.26.9, mesma versão do projeto; Vitest 3.2.7):

```
FAIL  RED-P2-006A: 409 com corpo {error} retorna o motivo real
AssertionError: expected 'Something went wrong.' to contain 'Código já existe'
FAIL  lê {error} e {message} juntos e junta os dois motivos
AssertionError: expected 'Motivo B' to contain 'Motivo A'
Test Files  1 failed (1) — Tests  2 failed | 5 passed (7)
```

Reproduz o sintoma original: o 409 de negócio voltava como mensagem genérica.

## GREEN-P2-006A (após correção)

Correção em `getErrorMessage` (`src/lib/pocketbase/errors.ts`): leitura de `error.response.error` e `error.response.message` antes do fallback; field-errors nativos preservados; deduplicação de partes; fallback genérico somente sem corpo legível (regra 5 da SPEC).

```
✓ errors.test.ts (7 tests)
Test Files  1 passed (1) — Tests 7 passed (7)
```

## QA SKIP

- 0.0.72: setup ✓, estática ✓, build ✓, integrações ✓ — testes pulados pela plataforma (`ran: false`).
- 0.0.73: reexecução com build persistido — mesmo resultado (`ran: false`).
- Limitação registrada: QA da plataforma não executou Vitest; GREEN provado localmente com o mesmo SDK. Reexecução independente em 2026-10-20: `npx vitest run` — 7/7 PASS.

## Pré-verificação no preview — errata de setup

A identificação anterior do item como "sintético geotecnia, id `im6n9uakjgnzycu`" estava errada. Consulta autenticada ao preview confirmou que `im6n9uakjgnzycu` é item preexistente `teste`, família `Teste`, tipo `servico`, estado `inativo`. A composição `COMP-T213-01` v1 (`hzk2wr5ce9dd56y`) foi criada vinculada a esse item e o servidor lhe atribuiu família `Teste` (HTTP 201); essa prova antiga não demonstra setup geotecnia.

A prova válida de duplicidade em geotecnia usou o item existente `krkue1xg6fiwlfe` e código `COMP-TESTE-01`, cuja v1 (`26ljaq5sixv5unr`) permaneceu única. A tela da Biblioteca mostrou o motivo real do servidor: **"Código já existe para esta família; revisão cria nova versão via /revise."** A resposta HTTP 409 foi negada sem gravar segunda versão.

## Gate humano e acesso à tela

O champion inicialmente tentou pelo menu `Clientes / Propostas / Projetos`, que não oferece o fluxo técnico. Depois, Paulo confirmou explicitamente: **"Abri /painel-tecnico e vi o alerta esperado."** A confirmação é posterior ao roteiro e aprova o teste humano da T2.13.

Na Biblioteca, `catalog_item_id` é digitado manualmente e a lista não mostra os IDs; isso não foi alterado por esta task. Cadastro comercial de Clientes/Projetos segue fora do escopo da Fase 2; menu e extração de módulos pertencem às T2.14/T2.15.

## Matriz critério → prova

| Critério | Prova | Resultado |
|---|---|---|
| CA-2-11 recorte da T2.13 — erro de negócio mostra motivo real | RED-P2-006A | reproduzido na 0.0.71 (2 falhas/7) |
| CA-2-11 recorte da T2.13 — erro de negócio mostra motivo real | GREEN-P2-006A + preview | suíte local 7/7; 409 exibiu motivo real e não criou duplicata |
| Teste humano da T2.13 | confirmação explícita do champion após o roteiro | PASSOU — alertou o motivo esperado em `/painel-tecnico` |
| Revalidação do passo 4 da T2.3 | mesmo cenário de duplicidade geotecnia, sem segunda versão | prova técnica/humana pertinente; fechamento da T2.3 segue separado |

## Recorte implementado

Somente `src/lib/pocketbase/errors.ts` (correção) + `src/lib/pocketbase/errors.test.ts` (suíte nova). Sem migration, hook ou mudança de regra. Homologação de composição é separada e não foi implementada nesta task.
