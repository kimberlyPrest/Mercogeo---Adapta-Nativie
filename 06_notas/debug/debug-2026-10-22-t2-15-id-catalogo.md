# Debug Summary — T2.15: item do catálogo na criação

- Task: T2.15 — Abrir Biblioteca em página própria preservando o contrato (SPEC-2-006).
- Sintoma relatado: ao enviar o formulário, a API retornou “Informe o item do catálogo da composição.” Navegação, consulta, preservação do preenchimento e leitura Comercial foram reportadas como corretas.
- Evidência de reprodução: logs do Skip registram quatro `POST /backend/v1/compositions` com HTTP 400 e a mesma mensagem. O corpo do POST não é incluído nos logs, portanto não é possível afirmar qual valor específico foi enviado.
- Causa raiz confirmada: o formulário usava texto livre para `catalog_item_id` e encaminhava o valor sem verificar sua correspondência com um registro do catálogo. O hook `pocketbase/hooks/composition_versions.js` valida existência do registro e o padrão `^[a-z0-9]{15}$`; a coleção `catalog_items` gera IDs nesse formato.
- Correção mínima: `src/pages/CompositionLibrary.tsx` consulta `getCatalogItems` do serviço existente e apresenta uma seleção com nome, família, tipo, status e ID. O helper `src/lib/compositionCatalog.ts` envia apenas o ID de um item carregado que atende ao formato. O botão fica bloqueado enquanto a consulta carrega, falha, retorna vazia ou não há seleção válida. Sem novo endpoint, hook, migration, schema ou regra de permissão.

## Verificações

- RED: um validador de formato isolado aceita `fakefakefakefak`, demonstrando que regex sem associação ao resultado da consulta é insuficiente.
- GREEN local: Vitest 3.2.4, `compositionCatalog.test.ts` 8/8, com stub limitado ao tipo `CatalogItemRecord`; 12/12 testes focados de navegação/continuidade do rascunho também passaram.
- Skip 0.0.79 (`f0b31fa`): setup PASS, análise estática PASS, build PASS, integrações PASS; suíte Skip pulada (`ran:false`, não classificada como PASS).
- Preview autenticado Engenharia: lista de catálogo apresentou opções com identificação completa; uma opção foi selecionada e o ID ficou visível no seletor. O formulário não foi submetido; não foi criada composição.
- Produção não publicada. O teste de persistência real permanece pendente de reteste humano.

## Gate

Estado: aguardando teste humano. No preview, selecionar item de catálogo que pertença à massa sintética aprovada, preencher somente dados de teste isolados e enviar uma vez. Confirmar sucesso retornado pelo servidor e versão na lista. Não usar item ou dados reais, não homologar e não inventar item/ID/fixture. Se não houver massa sintética válida e autorizada, não enviar; informar a ausência. Se falhar, registrar a mensagem exata sem repetir escrita.
