# ACEITE T2.33 — Editar composição e recursos por linhas e seletores

**Task:** T2.33 · SPEC-2-002 · CA-2-01/10 / UX-F2-002  
**Data do aceite:** 2026-10-27  
**Champion:** Paulo Romeiro  
**Versão:** Skip 0.0.83 · `ddb9e8c`  
**Produção:** não publicada  
**Preview:** `https://login-crm-merco-geopolimeros-3076d--preview.goskip.app`

## Resultado

**ACEITA pelo champion, com escopo reduzido explicitamente autorizado.** Em 2026-10-27, diante da análise read-only que apontou que "reabrir composição" exige endpoint de leitura por ID inexistente, Paulo escolheu a **opção 1**: entregar tabelas e seletores imediatamente e deixar "reabrir" para uma emenda de API. Após o roteiro de teste no preview, respondeu: "O teste funcionou."

**Esta aceitação não fecha o critério integral da task.** O critério escrito pede "criar/**reabrir** composição"; o recorte entregue cobre criar, com catálogo por nome, recursos em tabela e entradas rotuladas. Reabrir permanece pendente de emenda e não é declarado cumprido aqui.

## Evidências por critério

| Critério da task | Evidência | Resultado |
|---|---|---|
| Catálogo por nome/código | `select` alimentado por `getCatalogItems()`; nenhum campo aceita ID digitado. Já resolvido na T2.15 e preservado. | PASSOU |
| Recursos em tabela | `CompositionResourceTable`: uma linha por recurso, com colunas Recurso / Unidade / Coeficiente / Fonte-versão e ações adicionar/remover. | PASSOU |
| Recurso escolhido por seletor, sem ID | `select` por rótulo `nome · família · unidade · estado` — o ID interno vai por baixo. Teste garante que o rótulo **não** contém o ID. | PASSOU |
| Entradas rotuladas | `CompositionInputTable`: colunas Insumo / Unidade / Obrigatório / Mínimo / Máximo, com linha por insumo. | PASSOU |
| Sem pipe/ID/JSON | Os dois `textarea` com separador pipe foram removidos; nenhum campo técnico exposto. Verificado no arquivo entregue: zero ocorrências de `inputs_text`, `resources_text` e `textarea`. | PASSOU |
| Fonte preservada | Campo `source` mantido e validado (≤200), inalterado em relação ao contrato anterior. | PASSOU |
| Validações atuais de `fixture_ref` preservadas | Campo mantido obrigatório, ≤500, com rótulo "Caso de referência (referência documental assinada)" e ajuda explicando que o sistema não escolhe nem cria a referência. | PASSOU |
| Estado sem referência explica bloqueio e conserva campos | Validação local bloqueia o POST com mensagem no campo; `afterCompositionSaved` só é chamado após resposta de sucesso, então negação do servidor nunca limpa o formulário. | PASSOU |
| Não cadastrar referência fictícia | Nenhum valor é preenchido automaticamente em `fixture_ref`; sem referência, não há envio. | PASSOU |
| Não afirmar rascunho salvo quando a API negar | Mensagem de sucesso emitida apenas no caminho posterior ao 201; erro do servidor vai para bloco distinto com `getErrorMessage` (motivo real do corpo). | PASSOU |
| **Reabrir composição salva** | **NÃO ENTREGUE.** O contrato atual não tem leitura individual de `composition_versions`: `viewRule: null` e o hook expõe apenas `GET /compositions` (lista resumida), `POST /compositions` e `POST /compositions/revise`. Cumprir exige endpoint novo, e a SPEC-2-002 determina que demanda de endpoint novo sai da minuta e exige SPEC explícita. | PENDENTE — exige emenda |
| Papel autorizado | Formulário renderizado apenas para Engenharia/Admin (permissão local + checagem server-side `checkPermission`); Comercial vê somente a listagem. Regra do servidor intocada. | PASSOU |
| Build e QA | Skip 0.0.83/`ddb9e8c`: setup, análise estática, build e integrações PASS; suíte da plataforma pulada (`ran:false`). | PASSOU com suíte do Skip pulada |
| Regressão | Vitest local revalidado do zero no fechamento: **114/114 em 8 arquivos** — `compositionRows` 42, `compositionDraft` 8, `techSheetForm` 17, `navigation` 11, `opportunityList` 9, `permissions` 12, `compositionCatalog` 8, `errors` 7. | PASSOU |
| Escopo e produção | Nenhuma coleção, campo, migration, hook ou permissão criada ou alterada; nenhum endpoint novo. Produção não publicada. | PASSOU |

### Limites de observabilidade

- A verificação HTTP direta do preview continua bloqueada pelo proxy do ambiente; o caminho real é sustentado pelo teste humano do champion.
- A suíte de testes da plataforma Skip não executou (`ran:false`); a cobertura declarada é o Vitest local, rodado no fechamento sobre as mesmas fontes gravadas no Skip (diferença observada apenas de formatação aplicada por `oxfmt`).

## Recorte entregue

- Insumos em tabela de linhas com rótulos e colunas opcionais homologadas (`required`/`min`/`max`), sem pipe.
- Recursos em tabela com seleção por nome no catálogo; unidade e fonte sugeridas do catálogo quando o campo está vazio, sempre editáveis.
- Validação por campo espelhando os limites do hook `composition_versions.js`: código `[A-Za-z0-9_-]` ≤64, unidade ≤40, fonte ≤200, precisão/tolerância ≤40, coeficiente decimal textual, 1–50 linhas, vigência com início ≤ fim, `fixture_ref` obrigatório ≤500.
- Mensagem na célula/coluna e foco no primeiro problema em ordem de leitura; nada é enviado quando a validação local falha.
- `formula_ast` continua sendo o objeto mínimo já existente; o editor é T2.18.

## Pendência aberta (não é defeito)

**DÚVIDA para a consultoria:** a T2.33 exige "reabrir composição", mas `composition_versions` não possui leitura individual (`viewRule: null`, sem rota GET por ID). É necessário emendar a SPEC-2-002 com uma rota de leitura autenticada por ID, no mesmo recorte de papel da listagem, e decidir em qual task ela é entregue. Alternativa: reduzir formalmente o critério da T2.33 a criar + listar e mover "reabrir" para a task da emenda.

**Veredito:** T2.33 aceita no recorte autorizado (opção 1) após confirmação do teste humano. O critério integral da task não está fechado por causa de "reabrir". O gate de cálculo operacional da Fase 2 segue bloqueado; esta aceitação não homologa composição nem libera uso com dados reais.
