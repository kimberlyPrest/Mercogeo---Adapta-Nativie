# ACEITE T2.16 — Escolher unidades e dimensões por nome no cadastro técnico

**Task:** T2.16 · SPEC-2-007 · CA-2-12 / UX-F2-007  
**Data do aceite:** 2026-10-27  
**Champion:** Paulo Romeiro  
**Versão:** Skip 0.0.86 · `08b6742`  
**Produção:** não publicada  
**Preview:** `https://login-crm-merco-geopolimeros-3076d--preview.goskip.app` · rota `/unidades`

## Resultado

**ACEITA pelo champion.** Em 2026-10-27, após o roteiro de teste no preview, Paulo confirmou: "Fiz o teste e funcionou".

## Evidências por critério

| Critério da task | Evidência | Resultado |
|---|---|---|
| Engenharia cadastra unidade com dimensão | `POST /backend/v1/units` cria registro em `rascunho` com código, nome e dimensão da lista fechada (`area`, `massa`, `comprimento`, `volume`, `massa/area`, `tempo`, `adimensional`); validação por campo espelha o hook (código `[a-z0-9/]` ≤20, nome ≤120). Champion criou `m2`/`Metro quadrado`/`Área`. | PASSOU |
| Engenharia homologa unidade | `POST /backend/v1/units/homologate` exige unidade em rascunho, registra `homologated_by`/`homologated_at` e audita. Champion homologou `m2`. | PASSOU |
| Seletor distingue rascunho/homologada/inativa | Lista `GET /backend/v1/units` expõe estado; UI exibe badge distinta por estado (RASCUNHO/HOMOLOGADO/INATIVO) e motivo/data quando aplicável. | PASSOU |
| Inativação com justificativa | `POST /backend/v1/units/deactivate` exige `reason`; UI bloqueia sem justificativa; unidade inativa permanece na lista com o motivo visível, sem apagar. | PASSOU |
| Código único com motivo real | Tentativa de código duplicado retorna 409 com motivo legível (`code_duplicated`), sem novo registro; índice único `idx_units_code` no banco. | PASSOU |
| Comercial não cria (403) | Hook nega com `forbiddenError` para papel fora de engenharia/admin e audita a rejeição; UI esconde formulário e ações para papel sem permissão. | PASSOU (server-side; UI por permissão) |
| Servidor rejeita uso não homologado | **Limite declarado no recorte:** a rejeição de *uso* de unidade não homologada em composição é provada na T2.17, que cria o vínculo unidade↔composição. Nesta task, a garantia é que a consulta de unidades expõe o estado e o CRUD direto é negado (`listRule`/`viewRule`/`createRule`/`updateRule`/`deleteRule` = null, confirmado na coleção `pbc_586599074`). | PARCIAL — conclusão na T2.17 |
| UX-007-UN (estados honestos) | Estados separados de carregando, vazio, falha com retry e sucesso; mensagens no campo com foco no primeiro problema; formulário nunca limpo em falha. | PASSOU |
| Menu | **Sem item de menu novo**, por decisão explícita do champion (a T2.36 é dona do índice administrativo; a SPEC-2-006 exige recorte próprio para extrações adicionais). Acesso pela rota direta `/unidades`. | PASSOU (decisão registrada) |
| Migration | `0050_create_units` aplicada e confirmada na instância (coleção `pbc_586599074`); aditiva, com down-migration que remove apenas a coleção nova. Nenhuma coleção existente alterada. | PASSOU |
| Build e QA | Skip 0.0.86/`08b6742`: setup, análise estática, build e integrações PASS; suíte da plataforma pulada (`ran:false`). | PASSOU com suíte do Skip pulada |
| Regressão | Vitest local revalidado do zero no fechamento: **140/140 em 9 arquivos** — `unitForm` 26 (novos), `compositionRows` 42, `compositionDraft` 8, `techSheetForm` 17, `navigation` 11, `opportunityList` 9, `permissions` 12, `compositionCatalog` 8, `errors` 7. | PASSOU |
| Escopo e produção | Nenhuma coleção, hook ou permissão existente alterada; nenhum endpoint de composição/catálogo modificado. Produção não publicada. | PASSOU |

### Limites de observabilidade

- A verificação HTTP direta do preview continua bloqueada pelo proxy do ambiente; o caminho real é sustentado pelo teste humano do champion.
- A suíte de testes da plataforma Skip não executou (`ran:false`); a cobertura declarada é o Vitest local, rodado no fechamento sobre as mesmas fontes gravadas no Skip.

## Recorte entregue

- Coleção `units` (código único, nome, dimensão, estado, motivo de inativação, autor/homologador/timestamps) com CRUD direto negado.
- Hooks server-side: criar (rascunho), homologar (só de rascunho), inativar (justificativa obrigatória, sem apagar) e listar (autenticado, filtro por estado).
- Service `src/services/units.ts` e página `/unidades` com validação por campo, foco no primeiro erro e estados honestos.
- Rota em `App.tsx` sem item de menu (decisão do champion, registrada).

## Fora do recorte (próximas tasks)

- Vínculo unidade↔composição e rejeição de uso não homologado — T2.17.
- Conversão entre unidades — exige emenda homologada (fora da fase).

**Veredito:** T2.16 concluída após confirmação do teste humano. O gate de cálculo operacional da Fase 2 segue bloqueado; esta aceitação não libera uso com dados reais.
