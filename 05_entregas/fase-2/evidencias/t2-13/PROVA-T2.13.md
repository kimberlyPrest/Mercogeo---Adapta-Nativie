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

Correção em `getErrorMessage` (`src/lib/pocketbase/errors.ts`): leitura de
`error.response.error` e `error.response.message` antes do fallback do SDK; field-errors nativos
preservados; deduplicação de partes; fallback genérico somente sem corpo legível (regra 5 da SPEC).

```
✓ errors.test.ts (7 tests)
Test Files  1 passed (1) — Tests  7 passed (7)
```

## QA SKIP

- 0.0.72: setup ✓, estática ✓, build ✓, integrações ✓ — etapa de testes pulada pela plataforma (`ran: false`).
- 0.0.73: reexecução com build persistido — mesmo resultado (`ran: false`).
- Limitação registrada: o QA da plataforma não executou a suíte vitest; o GREEN ficou provado
  localmente com o mesmo SDK.

## Pré-verificação no preview — errata de setup

**Correção à versão anterior desta evidência:** a identificação do item de catálogo como “sintético
geotecnia, id `im6n9uakjgnzycu`” estava errada. A consulta autenticada ao preview confirmou que
`im6n9uakjgnzycu` é um item preexistente chamado `teste`, família `Teste`, tipo `servico`, estado
`inativo` — não foi criado na sessão de teste. A composição `COMP-T213-01` v1 (`hzk2wr5ce9dd56y`)
foi criada vinculada a esse item e o servidor lhe atribuiu família `Teste` (HTTP 201).

O teste duplicado na tela da Biblioteca devolveu HTTP 409 e o DOM exibiu o texto real do servidor:
**"Código já existe para esta família; revisão cria nova versão via /revise."** A mensagem foi lida
duas vezes. Isso demonstra a apresentação da resposta de negócio 409 da T2.13 nesse registro de
família `Teste`; não demonstra criação de um novo item de geotecnia nem revalida o passo 4 da T2.3
para a composição geotecnia. A descrição anterior exagerava o que o setup provava.

## Gate humano e acesso à tela

O champion informou que tentou pelos itens do menu CRM (`Clientes`, `Propostas`, `Projetos`). No
preview verificado, essas rotas não oferecem a Biblioteca técnica: `Clientes` mostra botão “Novo
Cliente” que abre modal sem campos; `Propostas` não tem formulário e o link “Nova Demanda Técnica”
retorna a `/dashboard`; `Projetos` mostra somente títulos/link de retorno. A tela técnica está em
`/painel-tecnico`, mas não aparece no menu lateral. Portanto, a tentativa pelo menu não constitui o
teste humano da T2.13; **o teste humano continua pendente**.

Na UI da Biblioteca, o campo `catalog_item_id` é digitado manualmente e a lista de catálogo não
exibe IDs. Para o ensaio correto de duplicidade da família geotecnia, a leitura da API encontrou o
item de teste existente `krkue1xg6fiwlfe` ("Composicao sintetica T2.3 teste humano", família
`geotecnia`, rascunho) e a composição existente `COMP-TESTE-01` v1 (`26ljaq5sixv5unr`, família
`geotecnia`). A revalidação humana do passo 4 da T2.3 exige repetir a duplicidade com esse par, ou
outro setup geotecnia claramente identificado, pela rota técnica direta.

**Escopo:** as páginas/clientes e projetos como cadastro comercial estão fora da Fase 2 conforme
fase.md; não foram alteradas aqui. As lacunas de navegação por papel e extração em páginas por
módulo pertencem às T2.14/T2.15, ainda não iniciadas.

## Matriz critério → prova

| Critério | Prova | Resultado |
|---|---|---|
| CA-2-11 — erro de negócio mostra motivo real | RED-P2-006A | reproduzido na 0.0.71 (2 falhas/7) |
| CA-2-11 — erro de negócio mostra motivo real | GREEN-P2-006A | 7/7 local; 409 real exibiu motivo no DOM do preview |
| Teste humano da T2.13 | pendente | champion ainda não executou o ensaio via Biblioteca técnica |
| Revalidação do passo 4 da T2.3 | pendente | setup anterior usou família `Teste`; não vale como prova geotecnia |

## Recorte implementado

Somente `src/lib/pocketbase/errors.ts` (correção) + `src/lib/pocketbase/errors.test.ts` (suíte
nova). Sem migration, sem hook e sem mudança de regra. Menu lateral e páginas por módulo permanecem
nas tasks T2.14/T2.15; cadastro comercial de Clientes/Projetos é fora de escopo nesta fase.