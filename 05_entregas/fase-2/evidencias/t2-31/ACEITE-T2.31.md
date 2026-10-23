# ACEITE T2.31 — Criar e retomar demanda na lista de oportunidades

**Task:** T2.31 · SPEC-2-006 · CA-2-11 / UX-F2-006  
**Data do aceite:** 2026-10-23  
**Champion:** Paulo Romeiro  
**Versão:** Skip 0.0.80 · `423a270`  
**Produção:** não publicada  
**Preview:** `https://login-crm-merco-geopolimeros-3076d--preview.goskip.app`

## Resultado

**ACEITA pelo champion.** Após receber o roteiro de teste humano em 2026-10-23, Paulo respondeu: “O teste da t2.31 foram bem sucedidos.” A mensagem é posterior ao roteiro, refere-se ao teste executado e confirma o fluxo entregue.

## Evidências por critério

| Critério da task | Evidência | Resultado |
|---|---|---|
| Nova demanda abre formulário real | `/demandas` → botão “Nova demanda” abre formulário com os campos do contrato existente; `createOpportunity` envia ao endpoint `/backend/v1/opportunities` já existente. Confirmação humana do fluxo de criação. | PASSOU — confirmação explícita do champion |
| Salvar abre detalhe persistido | Após o POST, a página relê o registro por ID (`getOne` em `opportunities`) e exibe os campos devolvidos pelo servidor, incluindo `received_at` gerado server-side. Não monta a tela a partir do formulário local. | PASSOU |
| Lista e busca usam registros autorizados | Lista vem de `getOpportunities` (regra de listagem do servidor por responsável); a busca é filtro local sobre esse conjunto, sem nova consulta nem ampliação de acesso. `filterOpportunities` não muta a lista. | PASSOU |
| Filtros existentes efetivos | Busca cobre cliente, contato, e-mail, origem, família, local, data e situação; ignora acentos e caixa; exige que todos os termos combinem. 9 testes locais cobrem vazio, múltiplos campos, acento/caixa, sem-resultado e não-mutação. | PASSOU |
| Vazio, falha e carregamento distintos | `describeOpportunityEmptyState` separa `loading`, `error`, `empty`, `no-results` e `ready`; a página renderiza mensagem e ação próprias para cada um, inclusive “Tentar novamente” na falha. Coberto por teste local. | PASSOU |
| Voltar preserva contexto | O retorno do detalhe mantém o termo de busca aplicado e devolve o foco ao campo de busca; seleção só é aceita para ID presente na lista autorizada (`resolveOpportunityId`). Coberto por teste local e confirmado no teste humano. | PASSOU |
| Não há CRM novo | Nenhuma coleção, migration, schema ou regra de permissão criada. `src/pages/Clientes.tsx`/`Projetos.tsx` seguem fora da navegação; os atalhos CRM continuam redirecionando ao dashboard. | PASSOU |
| Build e QA | QA Skip 0.0.80: setup, análise estática, build e integrações PASS; plataforma pulou a suíte (`ran:false`). Regressão local repetida no fechamento: `opportunityList` 9/9, `navigation` 11/11, `permissions` 12/12, `compositionCatalog` 8/8, `errors` 7/7 — 47/47. | PASSOU com suíte do Skip pulada |
| Escopo e produção | Nenhum endpoint, hook ou migration novo; `App.tsx`/`navigation.ts` apenas acrescentam a rota `/demandas` e o redirecionamento de `?secao=demanda`. Status Skip: produção não publicada. | PASSOU |

### Limites de observabilidade

- A checagem HTTP direta do preview falhou por bloqueio do proxy do ambiente (403 em `/`, `/demandas` e `/biblioteca`), inclusive em rotas já existentes; por isso o caminho real é sustentado pela confirmação do champion, não por código HTTP observado nesta sessão.
- A busca cobre as demandas carregadas pela consulta atual (limite de 50 por página). Varrer todo o histórico exigiria paginação/filtro server-side e não faz parte deste recorte.

## Recorte entregue

- Página própria `/demandas` com lista das demandas autorizadas e busca local.
- Ação “Nova demanda” criando pelo endpoint existente; ao salvar, abre o detalhe persistido lido do servidor.
- Retorno do detalhe preservando o termo de busca e o foco.
- Estados separados de carregamento, falha, lista vazia e busca sem resultado.
- Item “Oportunidades” do menu aponta para a rota nova; `?secao=demanda` redireciona para ela; item permanece marcado.

**Veredito:** T2.31 concluída após confirmação do teste humano. O gate de cálculo operacional da Fase 2 segue bloqueado; esta aceitação não homologa composição nem libera uso com dados reais.
