# Fase 2 — Dimensionamento e catálogo homologado

## Resultado

Transformar a ficha técnica do serviço-piloto em quantitativos e recursos reproduzíveis, mantendo a decisão de engenharia humana e exibindo a memória de cálculo.

## Inclui

- biblioteca versionada de serviços, recursos e composições;
- dimensionamento assistido;
- validação de unidades, campos e vigência;
- ajustes técnicos com trilha de auditoria;
- gate de prontidão por família antes do uso real.

## Fora de escopo

- preço, faturamento e envio de propostas;
- integrações externas produtivas;
- IA generativa;
- assinatura eletrônica.

## SPECs da fase

- SPEC-2-001 — Prontidão por família (gate).
- SPEC-2-002 — Biblioteca versionada de composições.
- SPEC-2-003 — Motor de cálculo decimal.
- SPEC-2-004 — Memória de cálculo e ajustes.
- SPEC-2-005 — Validação da jornada.
- SPEC-2-006 — Navegação e áreas.
- SPEC-2-007 — Composição com unidades e parâmetros da ficha.
- SPEC-2-008 — Guardas de pendência.

## Emenda de jornada e UX — 20/10/2026

Kim aprovou a reformulação documental e sua publicação em 20/10. As tasks T2.1–T2.29 preservam IDs e histórico; T2.30–T2.36 detalham UX. Foco: demanda → ficha → solução/quantitativos → revisão. Preço, CRM, IA, envio e integrações produtivas permanecem fora da fase.

CA-2-11 é alterado explicitamente somente no recorte administrativo: superfícies centrais extraídas; funções administrativas existentes acessíveis por índice contextual, sem perda de função/controle. Não exigir extrair todo painel em uma sessão. Extrações adicionais exigem recorte próprio. Critérios UX-F2-001..008 e cenários estão nos aditivos de cada SPEC, no contrato de experiência e no roteiro de validação.

Próxima sequência: T2.3, T2.14, T2.15, T2.31 e T2.32 concluídas. T2.32 foi aceita pelo champion em 2026-10-27 ("Agora deu certo" após correção do item 9); recibo em `05_entregas/fase-2/evidencias/t2-32/ACEITE-T2.32.md`. As superfícies centrais de Oportunidades e Ficha estão extraídas; a T2.33 foi aceita em 2026-10-27 no recorte autorizado de tabelas e seletores (reabrir pendente de emenda de leitura por ID). A T2.16 (unidades e dimensões) foi concluída em 2026-10-27; permanecem a T2.36 (índice administrativo, pré-condição T2.14 satisfeita) e a T2.34 (prontidão por rótulos, pré-condição T2.15). A T2.17 (vínculo entrada↔parâmetro) foi concluída em 2026-10-29 com quatro rodadas de teste humano; permanecem no corredor sem a T2.5 a T2.34 (prontidão por rótulos, pré-condição T2.15) e a T2.36 (índice administrativo, pré-condição T2.14). Apresentar análise e aguardar pedido/autorização explícitos. Uma task por vez e teste humano explícito antes de avançar. A T2.5 permanece pulada por decisão do champion, com a DÚVIDA de consultoria registrada.

T2.29 conserva somente vínculos suportados pelo gate existente; T2.28 é evidência documental obrigatória. Fixture executada/assinada na versão exata também é exigida pelos contratos de composição/cálculo, não inventada como campo de phase2_readiness. A aprovação do gate não dispensa homologação da composição. Gate de domínio pode usar UI existente sem esperar redesign T2.34.

Consultas seguras necessárias para seletores devem ser inventariadas antes do recorte. Se ausentes, parar e registrar necessidade de SPEC de dados/permissão; não criar acesso irrestrito nem inventar endpoint. Sem casos estruturados ainda, T2.33 preserva validação e referência documental vigente; seletor de composition_fixtures só em T2.19/T2.4.

## Critérios de aceite

- CA-2-01 Fixture estruturada registrada por família com versão e dono.
- CA-2-02 Gate consulta fixture vigente e nega sem registro.
- CA-2-03 Aritmética decimal determinística com política de arredondamento explícita.
- CA-2-04 Rejeição de unidade incompatível e divisão por zero com motivo.
- CA-2-05 Rascunho de composição persiste e duplicidade é negada com motivo real.
- CA-2-06 Dimensionamento assistido executa composição homologada com memória.
- CA-2-07 Memória registra entradas, saídas e decisões humanas.
- CA-2-08 Memória navegável por versão e demanda.
- CA-2-09 Ajustes pós-cálculo exigem justificativa e trilha.
- CA-2-10 Exportação fiel da memória.
- CA-2-11 Navegação por papel sem placeholders.
- CA-2-12 Composição valida unidades homologadas e parâmetros da ficha.
- CA-2-13 Dimensionamento por passos com guard.
- CA-2-14 Solução com várias composições por demanda.
- CA-2-15 Pendências bloqueiam confirmação/congelamento.
- CA-2-16 Baseline congelado com parecer.

## Demonstração visível

- Biblioteca com versões, estados e papéis.
- Ficha técnica com pendências explicadas.
- Dimensionamento com memória e ajustes justificados.
- Gate com bloqueios por família.

## Fora desta fase

- Preço, faturamento, envio de propostas, CRM, IA generativa e integrações produtivas.

## Expansão de 14/10/2026

Aprovada pelo champion: unificação de superfícies por demanda (Oportunidades, Ficha, Biblioteca, Prontidão) preservando IDs de tasks e provas; T2.30–T2.36 detalham navegação e UX. Nenhum software novo aprovado por esta expansão.

## Resultado observável aprovado para planejamento

O champion valida cada task com teste humano no preview antes do fechamento; autorização é task a task.

## Limites, dependências e segurança

- Nenhum cálculo real antes do gate aberto com fixture e homologações.
- Papéis: Engenharia cria/homologa; Comercial lê; Admin administra.
- Nenhum segredo no repositório; credenciais fora do código.

## Fluxo e recuperação

- Demanda → ficha → composição → gate → dimensionamento → memória → ajustes → exportação.
- Cada etapa preserva estados anteriores; recuperação por versão.

## Critério adicional para aprovação

Tarefa só fecha com teste humano confirmado pelo champion e registro em changelog.

## TDD da emenda (aprovado para planejamento, não executado)

- RED-P2-002A duplicidade com motivo real (executada na T2.13).
- RED-P2-003A unidade incompatível (pendente T2.5).
- RED-P2-006A/B navegação e mensagens (executadas T2.13/T2.14).
- RED-P2-007A/B unidade, faixa e caso de referência (T2.16/T2.17/T2.19).
- RED-P2-008A/B itens e pendências (T2.20/T2.22).

## Checklist de liberação (pré-implementação)

- [x] Contrato e SPECs publicados.
- [x] Emenda de jornada e UX aprovada.
- [ ] Gate de prontidão com dados reais.
- [ ] Fixture estruturada registrada.

## Risco e rollback

- Migrations aditivas; rollback por versão do Skip.
- Nenhuma coleção existente alterada sem emenda.

### Regras de integração e precedência desta revisão

- Tabela de Tasks prevalece sobre seções descritivas.
- Emendas registram DÚVIDAs com dono e data.
- Extrações adicionais exigem recorte próprio.

## Tasks

| ID | Task | Tipo | SPEC | Critérios | Contrato | Prova | Evidência | Pré-condições | Estado |
|---|---|---|---|---|---|---|---|---|---|
| T2.1 | Publicar baseline do contrato F2 | Consultor | — | — | — | — | — | — | concluída |
| T2.2 | Aprovar plano de tarefas F2 | Consultor | — | — | — | — | — | — | concluída |
| T2.3 | Reconciliar rascunho de composição | Produto | SPEC-2-002 | CA-2-05 | — | — | — | — | concluída 2026-10-20 |
| T2.4 | Fixture estruturada para o gate | Produto | SPEC-2-001 | CA-2-01/02 | — | — | — | T2.19 | bloqueada até concluir pré-condições; uma task por vez |
| T2.5 | Demonstrar cálculo decimal seguro com exemplos sintéticos | Produto | SPEC-2-003 | CA-2-03/04 | Execução no runtime real reproduz valores/limites do contrato e rejeita AST inválido, unidade incompatível e divisão por zero; apresentação da memória distingue simulação de aprovação. | RED/GREEN-P2-003A | evidencias/T2.5/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.3 | bloqueada até concluir pré-condições; uma task por vez (pulada por decisão do champion em 2026-10-23, com DÚVIDA de consultoria registrada) |
| T2.6 | Painel de dimensionamento assistido | Produto | SPEC-2-004 | CA-2-06/07 | — | — | — | T2.5 | bloqueada até concluir pré-condições; uma task por vez |
| T2.7 | Memória de cálculo navegável | Produto | SPEC-2-004 | CA-2-08 | — | — | — | T2.5 | bloqueada até concluir pré-condições; uma task por vez |
| T2.8 | Ajustes com trilha de auditoria | Produto | SPEC-2-004 | CA-2-09 | — | — | — | T2.5 | bloqueada até concluir pré-condições; uma task por vez |
| T2.9 | Exportar memória de cálculo | Produto | SPEC-2-004 | CA-2-10 | — | — | — | T2.5 | bloqueada até concluir pré-condições; uma task por vez |
| T2.10 | Ensaiar jornada sintética ponta a ponta | Consultor | SPEC-2-005 | CA-2-13/14 | — | — | — | T2.6..T2.9 | bloqueada até concluir pré-condições; uma task por vez |
| T2.11 | Cerimônia de aceite da Fase 2 | Consultor | SPEC-2-005 | CA-2-15/16 | — | — | — | T2.10 | bloqueada até concluir pré-condições; uma task por vez |
| T2.12 | Consolidar aceite técnico e de experiência da Fase 2 | Consultor | SPEC-2-005 | Aceite integrado SPEC-2-005; CA-2-01..16 e critérios UX aprovados na emenda | Consultor consolida matriz integral com esperado/obtido, versão, evidência e aprovador para critérios originais e somente UX expressamente aprovados; falha ou critério não medido impede fechamento. É cerimônia de aceite, não task de implementação nem liberação da fase seguinte. | RED/REG-P2-005 + UX-005-REG | evidencias/T2.12/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.11, T2.35, T2.36 | bloqueada até concluir pré-condições; uma task por vez |
| T2.13 | Preservar correção e aceite das mensagens de negócio | Produto | SPEC-2-006 | CA-2-11 | Preservar o aceite da T2.13 no STATUS; ao sincronizar versões, executar sua suíte sem reabrir aceite automaticamente; correção não encerra T2.3. | RED/GREEN-P2-006A | evidencias/T2.13/: versão, esperado/obtido, prova nomeada e aceite do validador | gates gerais | concluída — histórico preservado; T2.13 reconciliada em f533682 |
| T2.14 | Encontrar módulos reais no menu conforme o papel | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Cada função entregue tem acesso permitido, sem placeholders CRM/indicadores falsos; links levam a áreas existentes e URL antiga tem retorno seguro. Onde não extraído, abrir seção existente com contexto, sem perder função. | RED/GREEN-P2-006B + UX-006-NAV | evidencias/T2.14/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.30, T2.13 | concluída 2026-10-21 — champion confirmou os cinco cenários; recibo `05_entregas/fase-2/evidencias/t2-14/ACEITE-T2.14.md` |
| T2.15 | Abrir Biblioteca em página própria preservando o contrato | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Extrair somente a Biblioteca de composições para rota própria com os mesmos serviços, estados e papéis; criar/reabrir rascunho e erro de duplicidade funcionam sem painel inteiro. Mapa indica T2.31 para demandas, T2.32 para ficha, T2.34 para prontidão e T2.36 para administração transitória. | REG-P2-006 + UX-006-MOD | evidencias/T2.15/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | concluída 2026-10-22 — Paulo confirmou "Testado, funcionou" após reteste do fluxo de criação corrigido; versão Skip 0.0.79/f0b31fa. QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`), Vitest local focado 27/27. Recibo `05_entregas/fase-2/evidencias/t2-15/ACEITE-T2.15.md`; produção não publicada. |
| T2.16 | Escolher unidades e dimensões por nome no cadastro técnico | Produto | SPEC-2-007 | CA-2-12; UX-F2-007 | Engenharia cadastra/homologa unidade com dimensão; seletor distingue rascunho/homologada/inativa e servidor rejeita uso não homologado; Comercial não cria. | RED-P2-007A (unidade/papel) + UX-007-UN | evidencias/T2.16/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.3 | concluída 2026-10-27 — Paulo confirmou "Fiz o teste e funcionou". Coleção `units` criada (migration 0050, CRUD direto negado, código único), hooks `units_create`/`units_lifecycle`/`units_list` com papel Engenharia/Admin e auditoria, service `units.ts` e página `/unidades` (rota direta, **sem item de menu** por decisão do champion — T2.36 é dona do índice). Validação por campo espelhando o hook (código `[a-z0-9/]` ≤20, nome ≤120, dimensão da lista homologada). Limite declarado: a rejeição server-side de *uso* de unidade não homologada em composição é provada na T2.17, que cria o vínculo. Skip 0.0.86/08b6742; QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`), regressão local 140/140 em 9 arquivos. Recibo `05_entregas/fase-2/evidencias/t2-16/ACEITE-T2.16.md`; produção não publicada. |
| T2.17 | Ligar entradas da composição aos parâmetros da ficha | Produto | SPEC-2-007 | CA-2-12; UX-F2-007 | Selecionar parâmetro por nome/unidade/origem sem ID; ver mínimo/máximo e obrigatoriedade; salvar preserva o vínculo e valores ausentes/unidade divergente/faixa inválida têm mensagem específica. | RED-P2-007A (faixa) + UX-007-MAP | evidencias/T2.17/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.16, T2.33 | concluída 2026-10-29 — champion confirmou as negativas (unidade divergente, faixa invertida, unidade não homologada, item de catálogo já composto), o caminho feliz ("Consegui criar um rascunho após mudar o item do catalogo") e o papel Comercial ("Confirmado, comercial não cria"). Hook `composition_versions.js` (create e revise) com vínculo opcional `sheet_param` {nome, unidade, origem, mín, máx} e rejeições `sheet_unit_mismatch`, `sheet_range_invalid`, `unit_not_homologado` (prova server-side da regra da T2.16); coluna "Parâmetro da ficha (opcional)" com seletor por nome via `?oportunidade=`, entrada manual honesta sem contexto (0.0.138) e dica "Homologadas: …" (0.0.139). Limites: sem editor de fórmula (T2.18), sem fixture (T2.19), sem conversão de unidade e sem cálculo; releitura do vínculo depende da emenda de leitura por ID. Skip 0.0.139/b9d55f8; QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`), regressão local 153/153 em 9 arquivos. Recibo `05_entregas/fase-2/evidencias/t2-17/ACEITE-T2.17.md`; produção não publicada. |
| T2.18 | Montar fórmula por passos e conferir simulação identificada | Produto | SPEC-2-007 | CA-2-12; UX-F2-007 | Engenharia monta expressão sem JSON/código, desfaz passo e vê dimensão; servidor valida AST e calcula massa sintética identificada sem aprovação operacional; nenhuma função fora do contrato é aceita. | RED/GREEN-P2-007A + UX-007-FORM | evidencias/T2.18/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.5, T2.17 | bloqueada até concluir pré-condições; uma task por vez |
| T2.19 | Executar caso de referência antes de permitir homologação | Produto | SPEC-2-007 | CA-2-13; UX-F2-007 | Na versão exata, registrar e identificar caso de referência com entradas/esperado/tolerância e responsável; executar no servidor e mostrar esperado/obtido/diferença; disponibilizar seleção por rótulo nesta superfície, somente depois de existir composition_fixtures. Divergência mantém rascunho. Massa sintética não substitui contrato e assinatura real. | RED/GREEN-P2-007B/REG-P2-007 + UX-007-REF | evidencias/T2.19/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.18 | bloqueada até concluir pré-condições; uma task por vez |
| T2.20 | Montar solução com várias composições na oportunidade | Produto | SPEC-2-008 | CA-2-14; UX-F2-008 | Engenharia escolhe versões utilizáveis por nome/código/família, ordena/remove itens com justificativa e reabre o rascunho; servidor valida acesso e nenhuma seleção calcula caso real com gate fechado. | RED/GREEN-P2-008A (itens) + UX-008-ITENS | evidencias/T2.20/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.4, T2.18, T2.32 | bloqueada até concluir pré-condições; uma task por vez |
| T2.21 | Painel de dimensionamento por passos | Produto | SPEC-2-008 | CA-2-13 | — | — | — | T2.5, T2.20 | bloqueada até concluir pré-condições; uma task por vez |
| T2.22 | Resolver pendências antes de confirmar ou congelar | Produto | SPEC-2-008 | CA-2-15; UX-F2-008 | Painel lista tipo/campo/responsável/data, abre origem permitida e atualiza após correção; guard compartilhado nega tentativa com pendência, inclusive por chamada direta. Teste do guard em instância isolada antecede ligação das ações T2.7/T2.9. | RED-P2-008B + UX-008-PEND | evidencias/T2.22/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.21, T2.17 | bloqueada até concluir pré-condições; uma task por vez |
| T2.23 | Congelar baseline e registrar parecer | Produto | SPEC-2-008 | CA-2-16 | — | — | — | T2.22 | bloqueada até concluir pré-condições; uma task por vez |
| T2.24 | Definir família-piloto e dono | Mercogeo (Comercial) | — | — | — | — | — | — | pendente — dono Mercogeo |
| T2.25 | Baseline técnico da família | Mercogeo (Engenharia) | — | — | — | — | — | — | pendente — dono Mercogeo |
| T2.26 | SLA e janela de resposta | Mercogeo (Comercial) | — | — | — | — | — | — | pendente — dono Mercogeo |
| T2.27 | Recuperação de dados reais | Mercogeo (Dados) | — | — | — | — | — | — | pendente — dono Mercogeo |
| T2.28 | Evidências documentais do piloto | Mercogeo (Comercial) | — | — | — | — | — | — | pendente — dono Mercogeo |
| T2.29 | Registrar vínculos do gate | Mercogeo (Engenharia) | — | — | — | — | — | T2.25..T2.28 | pendente — dono Mercogeo |
| T2.30 | Mapear URLs legadas e retornos seguros | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | — | — | — | T2.13 | pendente |
| T2.31 | Abrir Demandas em página própria com busca e retorno | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Página `/demandas` com ação "Nova demanda" pelo endpoint existente; detalhe relido do servidor; busca local sobre o carregado; retorno preserva termo e foco. | REG-P2-006 + UX-006-DEM | evidencias/T2.31/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | concluída 2026-10-23 — Paulo confirmou "O teste da t2.31 foram bem sucedidos". Versão Skip 0.0.80/423a270; QA setup/estática/build/integrações PASS, suíte pulada (`ran:false`); regressão local 47/47. Recibo `05_entregas/fase-2/evidencias/t2-31/ACEITE-T2.31.md`; produção não publicada. |
| T2.32 | Abrir Ficha técnica em página própria com validação por campo | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Página `/ficha` em contexto da demanda; validação por campo espelhando o hook; histórico relido do servidor com versão destacada; estados honestos; menu e `?secao=ficha` redirecionam. | REG-P2-006 + UX-006-FIC | evidencias/T2.32/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | concluída 2026-10-27 — Paulo confirmou "Agora deu certo" no reteste do item 9 (404 de viewRule mapeado para estado de acesso indisponível; 0.0.82/8bfdeef). Recibo `05_entregas/fase-2/evidencias/t2-32/ACEITE-T2.32.md`; produção não publicada. |
| T2.33 | Criar/reabrir composição com tabelas e seletores por nome | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Insumos e recursos em tabelas com seleção por nome; validação por campo espelhando o hook; sem pipe/ID/JSON. | REG-P2-006 + UX-006-COMP | evidencias/T2.33/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.15 | concluída 2026-10-27 no recorte autorizado (opção 1) — Paulo confirmou "O teste funcionou". "Reabrir" fora do recorte: DÚVIDA de emenda de leitura por ID registrada em Emendas. Versão Skip 0.0.83/ddb9e8c; regressão 114/114. Recibo `05_entregas/fase-2/evidencias/t2-33/ACEITE-T2.33.md`; produção não publicada. |
| T2.34 | Entender e preparar prontidão sem digitar IDs | Produto | SPEC-2-001 | UX-F2-001 (proposto) | Família exibe bloqueios/dono/data; selecionar por rótulos apenas SLA/baseline/evidências que possuam consulta segura existente. Não prometer seletor de fixture estruturada no gate. UI envia os mesmos vínculos do contrato vigente e o backend revalida; consulta ausente bloqueia o recorte até emenda explícita, sem acesso irrestrito. | UX-001-UI | evidencias/T2.34/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.15 | bloqueada até concluir pré-condições; uma task por vez |
| T2.35 | Validar jornada sintética e acessibilidade antes do caso real | Consultor | SPEC-2-005 | UX-F2-005 (proposto) | Champion/Engenharia, com papéis separados, executam roteiro sem IDs fornecidos pelo executor; mediador não ensina caminho; conclusão de todos cenários + falhas registradas + aceite explícito. Protótipo/documento não conta como software validado. | UX-005-SINT/UX-005-REG | evidencias/T2.35/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.10, T2.23, T2.32, T2.33, T2.34, T2.36 | bloqueada até concluir pré-condições; uma task por vez |
| T2.36 | Organizar entrada administrativa e evidências existentes | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Entregar índice administrativo com destinos autorizados para baseline/SLA/backup/fontes/gates/catálogo/modelos/prévia/tempo/qualidade; abrir seções existentes por entradas contextuais preserva os serviços. Não extrair nem redesenhar todas essas telas nesta task; não exigir recibo técnico na jornada cotidiana nem ampliar acesso. | REG-P2-006 + UX-006-ADM | evidencias/T2.36/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | bloqueada até concluir pré-condições; uma task por vez |

## Emendas

| Data | Origem do sinal | Micro-spec/task | Motivo |
|---|---|---|---|
| 2026-10-27 | T2.33 (análise read-only + decisão do champion) | a definir em SPEC-2-002 | **DÚVIDA:** a T2.33 exige "reabrir composição", mas `composition_versions` não tem leitura individual (`viewRule: null` e nenhuma rota GET por ID; o hook expõe só lista, create e revise). Cumprir exige rota de leitura autenticada por ID no mesmo recorte de papel da listagem. A SPEC-2-002 determina que demanda de endpoint novo sai da minuta até SPEC explícita. Alternativa: reduzir formalmente o critério da T2.33 a criar + listar e mover "reabrir" para a task da emenda. Aguarda decisão da consultoria. |
| 2026-10-29 | T2.17 (teste humano, rodada 3) | a definir em SPEC-2-002 (ciclo de vida de `units`) | **DÚVIDA:** o design da T2.16 combina índice único permanente em `units.code` com proibição de rehomologar unidade inativa — o código inativado fica permanentemente indisponível (não rehomologa, não recadastra; bloqueou o teste da T2.17 com o `m2` inativado). Opções: (a) reativação com auditoria; (b) código único só entre ativas (índice parcial) com recadastro; (c) manter como intencional (código queimado). Altera migration/hook da T2.16 e exige recorte próprio. Aguarda decisão do champion/consultoria. |

## Aditivo de jornada e UX — aprovado by Kim em 20/10/2026

Este aditivo prevalece nos recortes explicitamente alterados. Preserva evidências e aceites anteriores; não aprova software ou uso real por si só.

### Critérios UX aprovados

- UX-F2-001 Prontidão por família: bloqueios, dono e data visíveis; seleção por rótulos.
- UX-F2-002 Biblioteca: busca por nome/família; estados vazios explicam o próximo passo.
- UX-F2-003 Ficha técnica: pendências explicadas em linguagem de negócio.
- UX-F2-004 Dimensionamento: passos visíveis, desfazer seguro, memória legível.
- UX-F2-005 Jornada sintética: papéis separados, sem IDs digitados.
- UX-F2-006 Navegação: menu contextual por papel, sem placeholders.
- UX-F2-007 Composição: unidades e parâmetros por nome, faixas explícitas.
- UX-F2-008 Pendências: painel único com origem e prazo.

### Cenários de validação

1. Engenharia cria demanda sintética, preenche ficha, monta composição com unidades homologadas e parâmetros da ficha, simula e registra memória.
2. Comercial acompanha demanda sem editar dados técnicos; tentativas de edição são negadas com mensagem.
3. Gate bloqueia família sem baseline/SLA/evidências; ao completar, libera cálculo real.
4. Pendência aberta impede confirmar/congelar; corrigida, o painel atualiza e a ação é liberada.
5. URLs antigas redirecionam sem perda de função; mobile preserva leitura e ações principais.

## Sequenciamento sugerido

Concluir T2.16/T2.17 antes de T2.18; T2.9/T2.21/T2.22 antes de T2.6 para garantir memória multi-item e negativas; T2.23/T2.35 antes de T2.11 para ensaio/exportação completos; T2.29 pode usar superfície antiga sem depender de T2.34.
