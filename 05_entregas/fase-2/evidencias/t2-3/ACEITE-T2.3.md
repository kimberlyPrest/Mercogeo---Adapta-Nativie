# ACEITE-T2.3 — Revalidar criação do rascunho e mensagem de duplicidade

> Fechamento documental · 2026-10-20 · Fase 2 · SPEC-2-002 · CA-2-01/10 · Prova RED/GREEN-P2-002A

## Confirmação humana (fonte do aceite)

- **Champion:** Paulo Romeiro (dono).
- **Confirmação explícita (2026-10-20, 15:06 −03:00):** "Confirmo o aceite próprio da T2.3: rascunho persistido e duplicidade com motivo real, sem novo registro".
- **Base do fechamento:** aceite próprio do champion. Nenhum novo teste de API ou de tela foi executado para este fechamento e nenhum novo registro foi gravado.
- **Nota:** o aceite da T2.13 (2026-10-19, 15:37) é confirmação separada; este recibo trata exclusivamente da T2.3.

## Separação das fontes de evidência

### 1. Fonte histórica (provas originais da task)

- **RED/GREEN-P2-002A** (implementação T2.3, versões Skip 0.0.65–0.0.69): 16/16 provas PASS; criação de rascunho HTTP 201; duplicata bloqueada com HTTP 409 `code_duplicated` e motivo real exibido.
- **Duplicidade geotecnia (prova registrada):** `05_entregas/fase-2/evidencias/t2-13/PROVA-T2.13.md` — composição COMP-TESTE-01 v1 (id `26ljaq5sixv5unr`), catálogo `krkue1xg6fiwlfe`; o 409 exibe "Código já existe para esta família; revisão cria nova versão via /revise." e não existe segunda versão gravada.
- **Nota de debug (fonte Skip):** `06_notas/debug/debug-2026-10-19-t2-13-menu-placeholder.md` confirma GET 200 com uma única v1 (sem duplicação de registro).
- **QA Skip 0.0.72–0.0.73:** setup/estática/build/integrações PASS conforme recibo da T2.13. Limitação registrada: `test.ran:false` significa suíte vitest **PULADA** pela plataforma, não PASS; o GREEN local + prova no preview compensam (limitação conhecida do runtime Skip).
- **Errata preservada:** a composição COMP-T213-01 (família "Teste", item antigo inativo) NÃO serve como prova geotecnia — retificação já registrada em d92f4455.

### 2. Reexecução local nesta rodada (2026-10-20, 15:07)

- `npx vitest run` (vitest 3.2.7) em `work/t2-13` → `errors.test.ts` **7/7 PASS**.
- `src/lib/pocketbase/errors.ts` no Skip (versão 0.0.73 / hash 2e9a06d, inalterada) relido e confirmado: `getErrorMessage` mantém a leitura de `error.response.error`/`error.response.message` antes do fallback.
- **Escopo desta reexecução:** valida APENAS o helper de erro (mensagens de negócio). **Não** constitui teste completo da T2.3, **não** é build/QA fresco, **não** é novo teste de API ou de tela.

### 3. Aprovação humana (aceite próprio)

- A confirmação do champion em 2026-10-20 (15:06 −03:00) comprova a persistência do rascunho e a duplicidade com motivo real, sem novo registro — base suficiente para o fechamento documental, sem repetição de gravação.

## Escopo do fechamento

- **Exclusivamente documental:** nenhum código implementado, nenhum schema/permissão alterado, nenhuma composição homologada ou criada, nenhuma SPEC editada.
- **Gate de cálculo operacional permanece BLOQUEADO** (0/4 dependências BLK-1..4 resolvidas; recibo GREEN-P2-001 segue válido).
- Estado no Skip **não alterado** nesta rodada (reconciliação do estado Skip fica a cargo do processo principal); `pending .skip.config.json` fora do escopo.
- T2.14/T2.30 **não** marcadas concluídas; demais tasks intocadas.

## Arquivos atualizados (commit único em main, 2026-10-20)

| Arquivo | Alteração |
|---|---|
| `04_fase-atual/fase.md` | somente célula Status da linha T2.3 → concluída 2026-10-20 com aceite próprio + ponteiro deste recibo |
| `STATUS.md` | "T2.3 permanece em teste humano" → concluída com aceite próprio; próxima ação = apresentar recorte da T2.14 e aguardar autorização específica; gate real e percentual preservados |
| `changelog.md` | append do fechamento datado 2026-10-20 (CHANGELOG.md legado intocado) |
| `05_entregas/fase-2/evidencias/t2-3/ACEITE-T2.3.md` | este recibo |

## Próximos passos

1. **T2.14** (encontrar módulos reais no menu conforme o papel): apresentar recorte e aguardar autorização específica do champion — não iniciar sem pedido explícito. Pré-condições documentais: T2.30 (decisão de UX aprovada pela Kim em 20/10; conferência visual por seção antes de alterar telas) e T2.13 (concluída).
2. Gate real de cálculo operacional segue condicionado a BLK-1..4 (T2.24–T2.29, donos Mercogeo).

## Limitações

- Suíte vitest pulada pelo QA do Skip (`test.ran:false`) nas versões 0.0.72–0.0.73 — limitação de plataforma, não aprovação de testes.
- Reexecução local desta rodada cobre somente o helper de erro.
- Nenhum build/QA fresco foi executado nesta rodada (fechamento só de docs; código Skip permanece 0.0.73/2e9a06d).