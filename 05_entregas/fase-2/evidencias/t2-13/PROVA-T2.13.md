# PROVA T2.13 — Restaurar motivo real dos erros de negócio (RED/GREEN-P2-006A)

**Data:** 2026-10-19 · **Task:** T2.13 (SPEC-2-006, CA-2-11 recorte 5) · **Versões:** 0.0.72–0.0.73
**Autorizada por:** Paulo Romeiro ("Sim, pode implementar a T2.13", 2026-10-19 10:32)

## RED-P2-006A (baseline v0.0.71, antes da correção)

Suíte nova `src/lib/pocketbase/errors.test.ts` executada localmente contra o `errors.ts` da 0.0.71
(SDK pocketbase 0.26.9, mesma versão do projeto; vitest 3.2.7):

```
FAIL  RED-P2-006A: 409 com corpo {error} retorna o motivo real
AssertionError: expected 'Something went wrong.' to contain 'Código já existe'
FAIL  lê {error} e {message} juntos e junta os dois motivos
AssertionError: expected 'Motivo B' to contain 'Motivo A'
Test Files  1 failed (1) — Tests  2 failed | 5 passed (7)
```

Reproduz o sintoma do chamado: o 409 de negócio voltava como mensagem genérica.

## GREEN-P2-006A (após correção)

Correção mínima em `getErrorMessage` (src/lib/pocketbase/errors.ts): leitura de
`error.response.error` e `error.response.message` antes do fallback do SDK; field-errors nativos
preservados; deduplicação de partes; fallback genérico somente sem corpo legível (regra 5 da SPEC).

```
✓ errors.test.ts (7 tests)
Test Files  1 passed (1) — Tests  7 passed (7)
```

## QA SKIP

- 0.0.72: setup ✓, estática ✓, build ✓, integrações ✓ — etapa de testes pulada pela plataforma (`ran: false`).
- 0.0.73: reexecução com build persistido — mesmo resultado (`ran: false`).
- Limitação registrada: o QA da plataforma não executa a suíte vitest deste projeto; o GREEN fica
  provado localmente com o mesmo SDK e o comportamento provado no preview real (abaixo).

## Prova no preview (comportamento real)

Login qa.engenharia@mercogeo.com.br → /painel-tecnico → seção "Biblioteca de composições".
Setup: item de catálogo sintético (geotecnia, tipo composicao, id `im6n9uakjgnzycu`) e composição
v1 `COMP-T213-01` (id `hzk2wr5ce9dd56y`, HTTP 201). Submissão do formulário com o MESMO código:

- Alerta exibido (`[role=alert]`, texto lido do DOM duas vezes após o submit):
  **"Código já existe para esta família; revisão cria nova versão via /revise."**
- Sem "Something went wrong." — motivo real do servidor (corpo do 409 do hook
  `composition_versions.js`: `{error, reason: "code_duplicated"}`).
- Lista permanece com uma única versão (sem duplicata).
- Confirmação visual final do alerta em quadro fica para o teste humano do champion (a captura da
  sessão do assistente enquadrou a seção parcialmente; a prova de texto do DOM está registrada acima).

## Matriz critério → prova

| Critério | Prova | Resultado |
|---|---|---|
| CA-2-11 (erros de negócio exibem o motivo real) | RED-P2-006A | falha documentada na 0.0.71 (2/7) |
| CA-2-11 (erros de negócio exibem o motivo real) | GREEN-P2-006A | 7/7 local + 409 com motivo real no preview (DOM) |

## Recorte

Somente `src/lib/pocketbase/errors.ts` (correção) + `src/lib/pocketbase/errors.test.ts` (suíte nova).
Sem migration, sem hook, sem mudança de regra. Menu lateral e páginas por módulo permanecem nas
tasks T2.14/T2.15.