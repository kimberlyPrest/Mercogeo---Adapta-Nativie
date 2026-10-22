# ACEITE T2.15 — Biblioteca em página própria

**Task:** T2.15 · SPEC-2-006 · CA-2-11 / UX-F2-006  
**Data do aceite:** 2026-10-22  
**Champion:** Paulo Romeiro  
**Versão:** Skip 0.0.79 · `f0b31fa`  
**Produção:** não publicada  
**Preview:** `https://login-crm-merco-geopolimeros-3076d--preview.goskip.app`

## Resultado

**ACEITA pelo champion.** Após receber o roteiro da correção de `catalog_item_id`, Paulo confirmou: “Testado, funcionou.” Essa mensagem é posterior ao roteiro e confirma o reteste humano do fluxo corrigido. Em testes humanos anteriores, o champion também confirmou navegação para `/biblioteca`, atualização/consulta, preservação de campos com cancelamento/saída, URL legada e leitura Comercial.

## Evidências por critério

| Critério/fluxo | Evidência | Resultado |
|---|---|---|
| Biblioteca em rota própria protegida | Configuração Skip lista `/biblioteca` → `CompositionLibrary`; preview autenticado Engenharia mostrou menu/títulos. Confirmação humana anterior incluiu URL e foco. | PASSOU |
| URL legada e outras seções | Testes locais focados de navegação (10/10) cobrem `/painel-tecnico?secao=biblioteca` → `/biblioteca` e preservação das outras URLs; champion confirmou os cenários no preview. | PASSOU |
| Consulta, atualização e estados | A página usa `getCompositions` já existente e diferencia carregamento, falha, vazio e dados; champion confirmou recarregar/atualizar e consultar. | PASSOU |
| Continuidade do formulário e saída | Estado compartilhado entre rotas; confirmação antes de abandonar campos não salvos. Testes locais focados de rascunho (2/2); champion confirmou navegar, manter, cancelar e sair. | PASSOU |
| Leitura por papel | Guardas existentes preservadas. Champion confirmou Comercial somente leitura; Engenharia viu formulário na rota própria. | PASSOU |
| Seleção do item de catálogo e criação | Correção v0.0.79 usa `getCatalogItems` existente, lista nome/família/tipo/status/ID e só envia um ID carregado e validado. 8 testes locais cobrem ID existente, valor digitado/falso, catálogo vazio/carregando/erro. Preview mostrou três itens e permitiu selecionar; em seguida o champion confirmou que o reteste “funcionou”. | PASSOU — confirmação explícita do champion |
| Erro de duplicidade e mensagens de negócio | Helpers/contrato de 400/409 preservados; suíte local `errors.test.ts` (SDK PocketBase 0.26.9) 7/7 passou neste fechamento. Prova anterior de 409 real sem duplicata consta em `../t2-13/PROVA-T2.13.md` e aceite T2.3. Não foi repetida escrita. | PASSOU — regressão |
| Build e QA | QA Skip v0.0.79: setup, análise estática, build e integrações PASS; plataforma pulou a suíte (`ran:false`). Vitest local repetido: 8/8 catálogo, 12/12 navegação/rascunho, 7/7 mensagens PocketBase. | PASSOU com suíte do Skip pulada |
| Escopo e produção | Sem endpoint, hook, migration, schema ou regra de permissão nova; status Skip confirma build dev em `f0b31fa` e produção não publicada. | PASSOU |

### Limite de observabilidade

Os logs consultados no fechamento incluíam os POSTs 400 anteriores, mas não expuseram um POST 201 após o reteste confirmado por Paulo. A aceitação do fluxo de criação se baseia na confirmação explícita do champion; não se declara aqui código HTTP, número da versão gerada nem ID do registro.

## Recorte entregue

- Biblioteca extraída para rota própria; menu lateral e título contextualizados.
- URL legada redireciona para `/biblioteca`; outras seções continuam no painel técnico.
- Consulta de versões e criação usam os serviços existentes.
- Campo relacional de catálogo tornou-se seleção de itens reais; erro/carregamento/lista vazia bloqueiam criação.
- “Reabrir” significa localizar/consultar rascunho salvo; edição de versão existente não foi incluída.
- Sem alteração de dados pela automação, sem homologação e sem publicação em produção.

**Veredito:** T2.15 concluída após confirmação do teste humano. O gate de cálculo operacional da Fase 2 segue bloqueado pelas dependências de domínio já registradas; esta aceitação não homologa composição nem libera uso real.
