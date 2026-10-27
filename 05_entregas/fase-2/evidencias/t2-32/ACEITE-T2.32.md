# ACEITE T2.32 — Preencher e revisar ficha em contexto da oportunidade

**Task:** T2.32 · SPEC-2-006 · CA-2-11 / UX-F2-006  
**Data do aceite:** 2026-10-27  
**Champion:** Paulo Romeiro  
**Versão:** Skip 0.0.82 · `8bfdeef` (implementação em 0.0.81/`ae4cc54`, corrigida em 0.0.82)  
**Produção:** não publicada  
**Preview:** `https://login-crm-merco-geopolimeros-3076d--preview.goskip.app`

## Resultado

**ACEITA pelo champion.** Em 2026-10-27, Paulo informou que os itens 1–8 do roteiro funcionaram e que o item 9 falhou. Após a correção em 0.0.82, respondeu: “Agora deu certo”. A aprovação cobre o roteiro completo executado no preview.

## Evidências por critério

| Critério da task | Evidência | Resultado |
|---|---|---|
| Dados/campos existentes com rótulos, unidades e origem | Formulário sobre os quatro campos do contrato (`name`/`value`/`unit`/`origin`), cada um com rótulo próprio e unidade/origem explícitas; cabeçalho identifica cliente, família, local, data e situação da demanda. | PASSOU |
| Anexos autorizados | Mesmo `createTechSheet` multipart existente, com limite de 10 arquivos (schema); download por `techSheetFileUrl` com token de sessão. Nenhuma regra de acesso nova. | PASSOU |
| Histórico | Lista de versões com parâmetros, pendências, observações e anexos, alimentada por `getTechSheets`; a versão recém-salva é destacada como “salva agora”. | PASSOU |
| Erros no campo | Validação de apresentação espelhando o hook `tech_sheet_create.js` (obrigatórios, 120/200/40/120, nome repetido, ≤50 parâmetros, ≤50 pendências, observações ≤2000, ≤10 anexos). Mensagem junto ao campo, `aria-invalid`/`aria-describedby`, foco no primeiro inválido. Coberto por 17 testes. | PASSOU |
| Falha preserva preenchimento | O `catch` de envio não reinicia os campos; apenas a validação local bloqueia o POST e mantém os valores. Confirmado no teste humano (itens 6 e 7). | PASSOU |
| Salvar reabre versão correta | Após o POST, o histórico é relido do servidor e a versão devolvida é destacada; recarregar a página mantém o histórico (itens 4 e 5 do roteiro). | PASSOU |
| Sem JSON ou ID digitado | A página só aceita contexto por `?oportunidade=<id>` validado (`resolveOpportunityContext`) ou seleção por nome de cliente; nenhum campo técnico exposto. | PASSOU |
| Acesso restrito ao responsável (item 9) | **Falhou na 0.0.81** e foi corrigido na 0.0.82: o PocketBase responde 404 (não 403) quando `viewRule` barra o registro, e o código só tratava 403 como permissão — a negação caía em erro genérico. Novo estado `unavailable` explica a restrição sem exibir dado algum. Champion confirmou: “Agora deu certo”. | PASSOU após correção |
| Build e QA | Skip 0.0.82/`8bfdeef`: setup, análise estática, build e integrações PASS; suíte da plataforma pulada (`ran:false`). Vitest local no fechamento: 64/64 (techSheetForm 17, opportunityList 9, navigation 11, permissions 12, compositionCatalog 8, errors 7). | PASSOU com suíte do Skip pulada |
| Escopo e produção | Nenhuma coleção, campo, migration, hook ou permissão criada ou alterada. `App.tsx` e `navigation.ts` apenas acrescentam a rota `/ficha` e o redirecionamento de `?secao=ficha`. Produção não publicada. | PASSOU |

### Limites de observabilidade

- A verificação HTTP direta do preview continua bloqueada pelo proxy do ambiente (403 inclusive em rotas preexistentes); o caminho real é sustentado pelo teste humano.
- O item 9 foi provado pela confirmação do champion após a correção, não por captura de código HTTP observada nesta sessão.

## Recorte entregue

- Página própria `/ficha` com a ficha técnica em contexto explícito da demanda.
- Contexto por rótulo: vinda do detalhe de `/demandas` ou seleção pelo nome do cliente, com busca.
- Validação por campo espelhando o servidor, com foco no primeiro inválido e valores preservados.
- Histórico por versão com destaque da versão recém-salva; anexos com o mesmo contrato.
- Estados separados: carregando, sem contexto, vazio, falha real, acesso indisponível e sucesso.
- Item “Ficha técnica” do menu aponta para `/ficha`; `?secao=ficha` redireciona.

**Veredito:** T2.32 concluída após confirmação do teste humano, com correção registrada do item 9. O gate de cálculo operacional da Fase 2 segue bloqueado; esta aceitação não homologa composição nem libera uso com dados reais.
