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

Próxima sequência: T2.3, T2.14, T2.15, T2.31 e T2.32 concluídas. T2.32 foi aceita pelo champion em 2026-10-27 ("Agora deu certo" após correção do item 9); recibo em `05_entregas/fase-2/evidencias/t2-32/ACEITE-T2.32.md`. As superfícies centrais de Oportunidades e Ficha estão extraídas; a T2.33 foi aceita em 2026-10-27 no recorte autorizado de tabelas e seletores (reabrir pendente de emenda de leitura por ID). A T2.16 (unidades e dimensões) foi concluída em 2026-10-27. A T2.17 (vínculo entrada↔parâmetro) foi concluída em 2026-10-29 com quatro rodadas de teste humano. A T2.34 (prontidão por rótulos, pré-condição T2.15) foi concluída em 2026-10-29. A T2.36 (índice administrativo, pré-condição T2.14) foi concluída em 2026-10-29; com isso, o corredor sem a T2.5 está esgotado no lado Produto e as demais tasks da fase dependem da T2.5 (pulada por decisão do champion) ou são documentais de dono Mercogeo. Apresentar análise e aguardar pedido/autorização explícitos. Uma task por vez e teste humano explícito antes de avançar. A T2.5 permanece pulada por decisão do champion, com a DÚVIDA de consultoria registrada.

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
| T2.4 | Homologar versão válida e encontrar somente composições utilizáveis | Produto | SPEC-2-002 | CA-2-01/02/10; UX-F2-002 | Pela UI, Engenharia vê versão/fonte/vigência e resultado do caso de referência; homologação exige execução válida dessa referência. Rascunho/inativo/vencido não aparece como utilizável; Comercial não escreve. | GREEN-P2-002B/REG-P2-002 + UX-002-HOMOLOGAR | evidencias/T2.4/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.3, T2.19, T2.33 | bloqueada até concluir pré-condições; uma task por vez |
| T2.5 | Demonstrar cálculo decimal seguro com exemplos sintéticos | Produto | SPEC-2-003 | CA-2-03/04 | Execução no runtime real reproduz valores/limites do contrato e rejeita AST inválido, unidade incompatível e divisão por zero; apresentação da memória distingue simulação de aprovação. | RED/GREEN-P2-003A | evidencias/T2.5/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.3 | concluída 2026-11-09 — implementada na v0.0.150 (Skip 095b88a): motor decimal + rota de prova `GET /backend/v1/dimensioning/selftest` (29 casos GREEN/RED) e página de diagnóstico; aceite registrado pela Kim em 09/11 informando teste do champion; recibo `05_entregas/fase-2/evidencias/t2-5/ACEITE-T2.5.md` |
| T2.6 | Calcular caso homologado mostrando origem de cada valor | Produto | SPEC-2-003 | CA-2-03/04; UX-F2-003 | No card da oportunidade (aba Dimensionamento), usuário escolhe ficha/versões por rótulos, solicita cálculo e vê entradas, unidades, resultado e parcelas reproduzíveis; ausências são explicadas no campo. Executa com composição sintética homologada da família sintética isolada (C2); para família real, gate inválido nega o cálculo (409). | GREEN-P2-003A2 (sintético homologado) + negativa de gate real + UX-003-CALCULAR | evidencias/T2.6/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.2, T2.4, T2.5, T2.19, T2.21, T2.22 | bloqueada até concluir pré-condições; uma task por vez |
| T2.7 | Revisar e confirmar tecnicamente a versão calculada | Produto | SPEC-2-003 | CA-2-05; UX-F2-003 | Engenharia revisa itens/memória e confirma com justificativa; pendência ou alteração concorrente nega confirmação e orienta revisão; Comercial não confirma. | GREEN-P2-003B/REG-P2-003 + GREEN-P2-008B + UX-003-CONFIRMAR | evidencias/T2.7/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.6, T2.22 | bloqueada até concluir pré-condições; uma task por vez |
| T2.8 | Ajustar valor com comparação e nova revisão obrigatória | Produto | SPEC-2-004 | CA-2-06; UX-F2-004 | A UI mostra original, ajustado, unidade e motivo; ajuste cria nova versão em rascunho e invalida a aprovação anterior para esse conteúdo; autor/data preservados. | RED/GREEN-P2-004A + UX-004-AJUSTAR | evidencias/T2.8/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.7 | bloqueada até concluir pré-condições; uma task por vez |
| T2.9 | Congelar versão reconfirmada sem pendências | Produto | SPEC-2-004 | CA-2-07; UX-F2-004 | Tela mostra versão e consequência antes de congelar; servidor rejeita pendência/assinatura antiga; mudar composição não altera snapshot congelado e estado somente leitura é explícito. | GREEN-P2-004A/REG-P2-004 + UX-004-CONGELAR | evidencias/T2.9/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.8, T2.22 | bloqueada até concluir pré-condições; uma task por vez |
| T2.10 | Clonar para novo rascunho com reconfirmações visíveis | Produto | SPEC-2-004 | CA-2-08; UX-F2-004 | Usuário autorizado cria um único clone, abre o novo caso e encontra reconfirmações de dados/documentos/prazos; original e aprovações preservados só no histórico; anexos não ganham acesso. | GREEN-P2-004B/REG-P2-004 + UX-004-CLONAR | evidencias/T2.10/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.9 | bloqueada até concluir pré-condições; uma task por vez |
| T2.11 | Demonstrar a jornada com oportunidade real autorizada | Engenharia Mercogeo | SPEC-2-005 | CA-2-09; UX-F2-005 | Após gate e homologações reais atuais, responsável percorre ficha → solução → revisão com memória do sistema; declara planilha apenas como conferência e registra falhas sem corrigi-las silenciosamente. | GREEN-P2-005 + GREEN-P2-003B (fixture real assinada) + UX-005-REAL | evidencias/T2.11/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.10, T2.23, T2.28, T2.29, T2.35 | bloqueada até concluir pré-condições; uma task por vez |
| T2.12 | Consolidar aceite técnico e de experiência da Fase 2 | Consultor | SPEC-2-005 | Aceite integrado SPEC-2-005; CA-2-01..16 e critérios UX aprovados na emenda | Consultor consolida matriz integral com esperado/obtido, versão, evidência e aprovador para critérios originais e somente UX expressamente aprovados; falha ou critério não medido impede fechamento. É cerimônia de aceite, não task de implementação nem liberação da fase seguinte. | RED/REG-P2-005 + UX-005-REG | evidencias/T2.12/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.11, T2.35, T2.36 | bloqueada até concluir pré-condições; uma task por vez |
| T2.13 | Preservar correção e aceite das mensagens de negócio | Produto | SPEC-2-006 | CA-2-11 | Preservar o aceite da T2.13 no STATUS; ao sincronizar versões, executar sua suíte sem reabrir aceite automaticamente; correção não encerra T2.3. | RED/GREEN-P2-006A | evidencias/T2.13/: versão, esperado/obtido, prova nomeada e aceite do validador | gates gerais | concluída — histórico preservado; T2.13 reconciliada em f533682 |
| T2.14 | Encontrar módulos reais no menu conforme o papel | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Cada função entregue tem acesso permitido, sem placeholders CRM/indicadores falsos; links levam a áreas existentes e URL antiga tem retorno seguro. Onde não extraído, abrir seção existente com contexto, sem perder função. | RED/GREEN-P2-006B + UX-006-NAV | evidencias/T2.14/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.30, T2.13 | concluída 2026-10-21 — champion confirmou os cinco cenários; recibo `05_entregas/fase-2/evidencias/t2-14/ACEITE-T2.14.md` |
| T2.15 | Abrir Biblioteca em página própria preservando o contrato | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Extrair somente a Biblioteca de composições para rota própria com os mesmos serviços, estados e papéis; criar/reabrir rascunho e erro de duplicidade funcionam sem painel inteiro. Mapa indica T2.31 para demandas, T2.32 para ficha, T2.34 para prontidão e T2.36 para administração transitória. | REG-P2-006 + UX-006-MOD | evidencias/T2.15/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | concluída 2026-10-22 — Paulo confirmou "Testado, funcionou" após reteste do fluxo de criação corrigido; versão Skip 0.0.79/f0b31fa. QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`), Vitest local focado 27/27. Recibo `05_entregas/fase-2/evidencias/t2-15/ACEITE-T2.15.md`; produção não publicada. |
| T2.16 | Escolher unidades e dimensões por nome no cadastro técnico | Produto | SPEC-2-007 | CA-2-12; UX-F2-007 | Engenharia cadastra/homologa unidade com dimensão; seletor distingue rascunho/homologada/inativa e servidor rejeita uso não homologado; Comercial não cria. | RED-P2-007A (unidade/papel) + UX-007-UN | evidencias/T2.16/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.3 | concluída 2026-10-27 — Paulo confirmou "Fiz o teste e funcionou". Coleção `units` criada (migration 0050, CRUD direto negado, código único), hooks `units_create`/`units_lifecycle`/`units_list` com papel Engenharia/Admin e auditoria, service `units.ts` e página `/unidades` (rota direta, **sem item de menu** por decisão do champion — T2.36 é dona do índice). Validação por campo espelhando o hook (código `[a-z0-9/]` ≤20, nome ≤120, dimensão da lista homologada). Limite declarado: a rejeição server-side de *uso* de unidade não homologada em composição é provada na T2.17, que cria o vínculo. Skip 0.0.86/08b6742; QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`), regressão local 140/140 em 9 arquivos. Recibo `05_entregas/fase-2/evidencias/t2-16/ACEITE-T2.16.md`; produção não publicada. |
| T2.17 | Ligar entradas da composição aos parâmetros da ficha | Produto | SPEC-2-007 | CA-2-12; UX-F2-007 | Selecionar parâmetro por nome/unidade/origem sem ID; ver mínimo/máximo e obrigatoriedade; salvar preserva o vínculo e valores ausentes/unidade divergente/faixa inválida têm mensagem específica. | RED-P2-007A (faixa) + UX-007-MAP | evidencias/T2.17/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.16, T2.33 | concluída 2026-10-29 — champion confirmou as negativas (unidade divergente, faixa invertida, unidade não homologada, item de catálogo já composto), o caminho feliz ("Consegui criar um rascunho após mudar o item do catalogo") e o papel Comercial ("Confirmado, comercial não cria"). Hook `composition_versions.js` (create e revise) com vínculo opcional `sheet_param` {nome, unidade, origem, mín, máx} e rejeições `sheet_unit_mismatch`, `sheet_range_invalid`, `unit_not_homologado` (prova server-side da regra da T2.16); coluna "Parâmetro da ficha (opcional)" com seletor por nome via `?oportunidade=`, entrada manual honesta sem contexto (0.0.138) e dica "Homologadas: …" (0.0.139). Limites: sem editor de fórmula (T2.18), sem fixture (T2.19), sem conversão de unidade e sem cálculo; releitura do vínculo depende da emenda de leitura por ID. Skip 0.0.139/b9d55f8; QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`), regressão local 153/153 em 9 arquivos. Recibo `05_entregas/fase-2/evidencias/t2-17/ACEITE-T2.17.md`; produção não publicada. |
| T2.18 | Montar fórmula por passos e conferir simulação identificada | Produto | SPEC-2-007 | CA-2-12; UX-F2-007 | Engenharia monta expressão sem JSON/código, desfaz passo e vê dimensão; servidor valida AST e calcula massa sintética identificada sem aprovação operacional pela rota `POST /backend/v1/compositions/simulate` (Engenharia/Admin; não grava resultado; memória marcada "simulação") (C4); o motor decimal da T2.5 é extraído para `pocketbase/hooks/lib/decimal_engine.js` e reutilizado, sem cópia (C3); arredondamento gravado em nome canônico D-T2.5 (C6); unidade homologada com código fora do padrão do motor (ex.: `m²`) é bloqueada na fórmula com mensagem (C7); nenhuma função fora do contrato é aceita. | RED/GREEN-P2-007A + UX-007-FORM | evidencias/T2.18/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.5, T2.17 | bloqueada até concluir pré-condições; uma task por vez |
| T2.19 | Executar caso de referência antes de permitir homologação | Produto | SPEC-2-007 | CA-2-13; UX-F2-007 | Na versão exata, registrar e identificar caso de referência com entradas/esperado/tolerância e responsável; executar no servidor e mostrar esperado/obtido/diferença; a própria T2.19 cria a coleção `composition_fixtures` (versão, entradas, esperado, tolerância, precisão, arredondamento canônico, responsável, sintético/real; CRUD direto negado) e a rota de execução, e disponibiliza a seleção por rótulo (C5). Divergência mantém rascunho. Massa sintética não substitui contrato e assinatura real. | RED/GREEN-P2-007B/REG-P2-007 + UX-007-REF | evidencias/T2.19/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.18 | bloqueada até concluir pré-condições; uma task por vez |
| T2.20 | Montar solução com várias composições na oportunidade | Produto | SPEC-2-008 | CA-2-14; UX-F2-008 | Engenharia escolhe versões utilizáveis por nome/código/família, ordena/remove itens com justificativa e reabre o rascunho; servidor valida acesso e nenhuma seleção calcula caso real com gate fechado. | RED/GREEN-P2-008A (itens) + UX-008-ITENS | evidencias/T2.20/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.4, T2.18, T2.32 | bloqueada até concluir pré-condições; uma task por vez |
| T2.21 | Conferir quantitativos por item e total por recurso | Produto | SPEC-2-008 | CA-2-14; UX-F2-008 | Dados sintéticos isolados com recurso repetido mostram soma decimal exata e origem por parcela; mesmo recurso em unidades diferentes fica separado; cálculo real continua condicionado ao gate. | GREEN-P2-008A (consolidação) + UX-008-TOTAL | evidencias/T2.21/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.20, T2.5 | bloqueada até concluir pré-condições; uma task por vez |
| T2.22 | Resolver pendências antes de confirmar ou congelar | Produto | SPEC-2-008 | CA-2-15; UX-F2-008 | Painel lista tipo/campo/responsável/data, abre origem permitida e atualiza após correção; guard compartilhado nega tentativa com pendência, inclusive por chamada direta. Teste do guard em instância isolada antecede ligação das ações T2.7/T2.9. | RED-P2-008B + UX-008-PEND | evidencias/T2.22/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.21, T2.17 | bloqueada até concluir pré-condições; uma task por vez |
| T2.23 | Exportar memória técnica conferível pela interface | Produto | SPEC-2-008 | CA-2-16; UX-F2-008 | Da versão congelada autorizada, exportar JSON/CSV, conferir conteúdo/unidades/hash e recibo; erro não mostra sucesso nem arquivo vazio como válido; exportação não envia proposta. | GREEN-P2-008C/REG-P2-008 + UX-008-EXP | evidencias/T2.23/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.9, T2.21 | bloqueada até concluir pré-condições; uma task por vez |
| T2.24 | Escolher e registrar a família-piloto | Comercial Mercogeo | SPEC-2-001 | RN-01/RN-21 | Template D parte 1 assinado registra família e tratamento do modelo alternativo; sem escolha inferida pelo executor. | GREEN-P2-001 (família) | evidencias/T2.24/: versão, esperado/obtido, prova nomeada e aceite do validador | gates gerais | pendente — dono Mercogeo |
| T2.25 | Homologar SLA real da família escolhida | Engenharia Mercogeo | SPEC-2-001 | RN-21 | Template A e parâmetro homologado no sistema estão vinculados à família e ao dono; evidência verificável, não apenas texto de aprovação. | GREEN-P2-001 (SLA) | evidencias/T2.25/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.24 | pendente — dono Mercogeo |
| T2.26 | Congelar baseline ou assinar parecer de limitação | Engenharia Mercogeo | SPEC-2-001 | RN-22 | Template B e baseline/parecer registram comparabilidade e limitações; não declarar ganho sem medição. | GREEN-P2-001 (baseline) | evidencias/T2.26/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.24 | pendente — dono Mercogeo |
| T2.27 | Comprovar recuperação real em instância isolada | Dados Mercogeo | SPEC-2-001 | CA-1-13 | Template C inclui dados/anexos/configuração necessários e comparação antes/depois; hash ou HTTP200 isolado não satisfaz a prova. | GREEN-P2-001 (recuperação) | evidencias/T2.27/: versão, esperado/obtido, prova nomeada e aceite do validador | gates gerais | pendente — dono Mercogeo |
| T2.28 | Assinar contrato e caso de referência da composição real | Engenharia Mercogeo | SPEC-2-001 | RN-02/CA-2-03 | Template D parte 2 assinado contém entradas/unidades/faixas/coeficientes/fórmula/resultado/tolerância/precisão/arredondamento/versão; valores reais não são escolhidos pelo executor. | GREEN-P2-001 (fixture) | evidencias/T2.28/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.24 | pendente — dono Mercogeo |
| T2.29 | Aprovar condições de uso real com vínculos verificáveis | Engenharia Mercogeo | SPEC-2-001 | RN-21/RN-22/CA-1-13; UX-F2-001 | Engenharia seleciona os vínculos já suportados pelo gate atual e solicita aprovação; servidor confere família/SLA/baseline/recuperação/recibo nos termos do contrato existente, nega vínculo ausente/inválido e invalida quando referência suportada muda. Contrato/fixture real T2.28 é pré-condição documental explícita, não vínculo server-side inventado no schema atual. Ainda que este gate esteja aprovado, cálculo e homologação reais exigem composição/fixture assinada, executada e válida na versão exata nos seus próprios contratos; divergência bloqueia ação. | GREEN-P2-001 (aprovação) + UX-001-GATE | evidencias/T2.29/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.2, T2.25, T2.26, T2.27, T2.28 | pendente — dono Mercogeo |
| T2.30 | Revisar a jornada e a especificação visual da área de trabalho | Consultor | SPEC-2-006 | UX-F2-006 (proposto) | Kim revisa documento com navegação por papel, hierarquia de oportunidade, lista/ficha/solução, estados e regra mobile; orientação verde/laranja e remoção de adorno ficam explícitas. Aprovação é só de design, não aceite da fase. | UX-006-DESIGN | Registro de decisão da Kim por seção (aprovada/ajustar/rejeitada), versão do contrato visual e mapa de navegação, sem inferir aceite do produto | gates gerais | concluída 2026-11-09 pela decisão D-UX-01 (C10): Kim aprovou a arquitetura funil/card por perfil e o design system "Laje nivelada" (petróleo `#17677A` + laranja da marca, claro e escuro), que substitui a orientação verde/laranja; documentos `docs/design-system/` no repo de código |
| T2.31 | Abrir Demandas em página própria com busca e retorno | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Página `/demandas` com ação "Nova demanda" pelo endpoint existente; detalhe relido do servidor; busca local sobre o carregado; retorno preserva termo e foco. | REG-P2-006 + UX-006-DEM | evidencias/T2.31/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | concluída 2026-10-23 — Paulo confirmou "O teste da t2.31 foram bem sucedidos". Versão Skip 0.0.80/423a270; QA setup/estática/build/integrações PASS, suíte pulada (`ran:false`); regressão local 47/47. Recibo `05_entregas/fase-2/evidencias/t2-31/ACEITE-T2.31.md`; produção não publicada. |
| T2.32 | Abrir Ficha técnica em página própria com validação por campo | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Página `/ficha` em contexto da demanda; validação por campo espelhando o hook; histórico relido do servidor com versão destacada; estados honestos; menu e `?secao=ficha` redirecionam. | REG-P2-006 + UX-006-FIC | evidencias/T2.32/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | concluída 2026-10-27 — Paulo confirmou "Agora deu certo" no reteste do item 9 (404 de viewRule mapeado para estado de acesso indisponível; 0.0.82/8bfdeef). Recibo `05_entregas/fase-2/evidencias/t2-32/ACEITE-T2.32.md`; produção não publicada. |
| T2.33 | Criar/reabrir composição com tabelas e seletores por nome | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Insumos e recursos em tabelas com seleção por nome; validação por campo espelhando o hook; sem pipe/ID/JSON. | REG-P2-006 + UX-006-COMP | evidencias/T2.33/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.15 | concluída 2026-10-27 no recorte autorizado (opção 1) — Paulo confirmou "O teste funcionou". "Reabrir" fora do recorte: DÚVIDA de emenda de leitura por ID registrada em Emendas. Versão Skip 0.0.83/ddb9e8c; regressão 114/114. Recibo `05_entregas/fase-2/evidencias/t2-33/ACEITE-T2.33.md`; produção não publicada. |
| T2.34 | Entender e preparar prontidão sem digitar IDs | Produto | SPEC-2-001 | UX-F2-001 (proposto) | Família exibe bloqueios/dono/data; selecionar por rótulos apenas SLA/baseline/evidências que possuam consulta segura existente. Não prometer seletor de fixture estruturada no gate. UI envia os mesmos vínculos do contrato vigente e o backend revalida; consulta ausente bloqueia o recorte até emenda explícita, sem acesso irrestrito. | UX-001-UI | evidencias/T2.34/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.15 | concluída 2026-10-29 — Paulo confirmou "Funcionou" no reteste da seção prontidão após correção do crash de render (TDZ: derivação de opções antes da declaração do estado). Seletores por rótulo para SLA homologado (pilot_params) e baseline congelado (baseline_snapshots, restrito ao próprio usuário) no lugar dos inputs de ID; estados vazio/carregando/erro com causa e próximo passo; sem endpoint/migration/schema/permissão nova; sem seletor de fixture no gate. Skip 0.0.143/f685e0f; QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`); regressão local 153/153 em 9 arquivos + prova de unidade T2.34 6/6. Recibo `05_entregas/fase-2/evidencias/t2-34/ACEITE-T2.34.md`; produção não publicada. |
| T2.35 | Validar jornada sintética e acessibilidade antes do caso real | Consultor | SPEC-2-005 | UX-F2-005 (proposto) | Champion/Engenharia, com papéis separados, executam roteiro sem IDs fornecidos pelo executor; mediador não ensina caminho; conclusão de todos cenários + falhas registradas + aceite explícito. Protótipo/documento não conta como software validado. | UX-005-SINT/UX-005-REG | evidencias/T2.35/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.10, T2.23, T2.32, T2.33, T2.34, T2.36 | bloqueada até concluir pré-condições; uma task por vez |
| T2.36 | Organizar entrada administrativa e evidências existentes | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Entregar índice administrativo com destinos autorizados para baseline/SLA/backup/fontes/gates/catálogo/modelos/prévia/tempo/qualidade; abrir seções existentes por entradas contextuais preserva os serviços. Não extrair nem redesenhar todas essas telas nesta task; não exigir recibo técnico na jornada cotidiana nem ampliar acesso. | REG-P2-006 + UX-006-ADM | evidencias/T2.36/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | concluída 2026-10-29 — Paulo confirmou "Funcionou" no teste humano do índice. Página /administracao com 11 destinos (os 10 da SPEC + Unidades, decisão do champion) com descrição de produto, abrindo as seções existentes por entrada contextual (/painel-tecnico?secao=<id> e /unidades); menu com "Índice da administração" e home com card do índice; nenhuma linha do painel legado alterada; sem endpoint/migration/schema/permissão nova. Skip 0.0.147/41c68e4; QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`); regressão local 165/165 em 10 arquivos (navigation 11+6). Recibo `05_entregas/fase-2/evidencias/t2-36/ACEITE-T2.36.md`; produção não publicada. |

## Emendas

| Data | Origem do sinal | Micro-spec/task | Motivo |
|---|---|---|---|
| 2026-10-27 | T2.33 (análise read-only + decisão do champion) | a definir em SPEC-2-002 | **DÚVIDA:** a T2.33 exige "reabrir composição", mas `composition_versions` não tem leitura individual (`viewRule: null` e nenhuma rota GET por ID; o hook expõe só lista, create e revise). Cumprir exige rota de leitura autenticada por ID no mesmo recorte de papel da listagem. A SPEC-2-002 determina que demanda de endpoint novo sai da minuta até SPEC explícita. Alternativa: reduzir formalmente o critério da T2.33 a criar + listar e mover "reabrir" para a task da emenda. Aguarda decisão da consultoria. |
| 2026-10-29 | T2.17 (teste humano, rodada 3) | a definir em SPEC-2-002 (ciclo de vida de `units`) | **DÚVIDA:** o design da T2.16 combina índice único permanente em `units.code` com proibição de rehomologar unidade inativa — o código inativado fica permanentemente indisponível (não rehomologa, não recadastra; bloqueou o teste da T2.17 com o `m2` inativado). Opções: (a) reativação com auditoria; (b) código único só entre ativas (índice parcial) com recadastro; (c) manter como intencional (código queimado). Altera migration/hook da T2.16 e exige recorte próprio. Aguarda decisão do champion/consultoria. |
| 2026-11-09 | Decisão da consultoria (Kim) — D-T2.5, responde à DÚVIDA de 22/10 | T2.5 / SPEC-2-003 (e SPEC-2-002 no arredondamento) | **DECISÃO D-T2.5.** (1) **Recorte da prova:** a T2.5 se limita a módulo decimal puro + rota de prova isolada `GET /backend/v1/dimensioning/selftest` (Engenharia/Admin; 401/403 nos demais) que executa no runtime real (goja/JSVM) somente fixtures sintéticas fixas no servidor, sem receber AST/valores do cliente, sem persistência, sem `dimensioning_runs`, sem endpoint de produto, sem cálculo real e sem abrir o gate. Permitida página de diagnóstico somente leitura (fora da jornada de produto) para o teste humano, mostrando esperado × obtido e a memória marcada como simulação. O cenário "calcular sem gate" do RED-P2-003A passa para a T2.6 (endpoint real). (2) **Arredondamento canônico:** `half-up`, `half-even`, `down` e `up` (afastando de zero), simétricos em relação a zero. Nomes legados do hook de composição: `normal` = `half-up`; `down` = `down`; `up` = `up` (incluído por esta emenda na SPEC-2-003). Novos contratos usam os nomes canônicos; o hook de composição não é alterado neste recorte. (3) **Divisão:** escala interna de 30 casas com bit de inexatidão (resto descartado) que desempata `half-*` e `up`; passo inexato é sinalizado na memória. Resultado intermediário acima de 18 algarismos inteiros é recusado (`out_of_range`), sem truncamento. Não altera CA-2-03/04, não homologa domínio e não libera T2.6+. Implementação pela consultoria a pedido da Kim; aceite segue com teste humano do champion. |
| 2026-11-09 | Decisão da Kim — D-UX-01 | navegação, superfícies e acompanhamento (RNF-01/RNF-05, RF-22, RF-24, RF-17) | **DECISÃO D-UX-01.** (1) Arquitetura de trabalho centrada na oportunidade: funil por etapa, card com abas da jornada, Hoje, Clientes (derivados das demandas, sem cadastro novo), Painel e Configurações; módulos técnicos saem do menu do dia a dia para Configurações e Evidências e controles. (2) Design system "Laje nivelada" (claro) / "Galpão à noite" (escuro) com as cores da marca. (3) Desfecho mínimo ganha/perdida com motivo obrigatório (RF-22/RN-17), migration 0052. (4) Gestão, Aprovador e Admin leem todas as oportunidades (escrita inalterada), migration 0052. (5) Admin de usuários e matriz perfil × módulo (ver/criar/editar/apagar), migration 0051; o Paulo vira administrador se não houver outro. Não altera CA-2-01..16 nem libera cálculo real; fora do escopo segue CRM completo (marketing/prospecção). Implementação pela consultoria no repo de código, branch `ux-crm-propostas`. |

## Aditivo de jornada e UX — aprovado por Kim em 20/10/2026

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

## Correções de coerência pré-implementação — 09/11/2026

Análise das tasks abertas após a T2.5, feita a pedido da Kim. Nenhuma destas tasks foi implementada; por isso as correções entram direto no contrato, sem emenda. Regra aplicada: a tabela **Tasks vinculadas** de cada SPEC prevalece (AP-2026-10-27-1530).

- **C1 — Tabela desta fase realinhada às SPECs.** Divergiam nome, dono, SPEC de origem ou pré-condição em: T2.4, T2.5, T2.6, T2.7, T2.8, T2.9, T2.10, T2.11, T2.18, T2.19, T2.21, T2.23, T2.24, T2.25, T2.26, T2.27, T2.28, T2.29, T2.30. A tabela acima agora espelha as SPECs; status preservados.
- **C2 — Cadeia sintética × real.** A T2.6 exigia fixture real (GREEN-P2-003B) e, por consequência, T2.7–T2.10, T2.23 e a validação sintética T2.35 ficavam presas ao gate e às tasks da Mercogeo (T2.24–T2.29) — contradição com "ensaio sintético antes do caso real". Agora a T2.6 executa com composição sintética homologada numa **família sintética isolada** (GREEN-P2-003A2); resultados sintéticos nunca entram no Painel nem em K1–K3 e são limpos por migration ao fim da fase. O cálculo com fixture real assinada (GREEN-P2-003B) passa para a **T2.11**, que ganha a pré-condição T2.28. Para família real, gate inválido continua negando o cálculo (409).
- **C3 — Motor decimal compartilhado.** O motor da T2.5 está dentro do hook de prova. A T2.18 o extrai para `pocketbase/hooks/lib/decimal_engine.js` (carregado com `require` dentro dos handlers) e a rota de prova passa a usá-lo; o teste segue lendo o mesmo arquivo. Proibido copiar o motor para outros hooks.
- **C4 — Rota de simulação explícita na T2.18:** `POST /backend/v1/compositions/simulate` (Engenharia/Admin; sem gravar resultado; memória marcada "simulação"). Antes, o fluxo pedia simulação no servidor e o aditivo dizia que endpoint novo exige SPEC explícita.
- **C5 — Caso de referência:** a T2.19 cria a coleção `composition_fixtures` e a rota de execução (antes a T2.19 dependia de uma coleção que ninguém criava).
- **C6 — Arredondamento canônico (D-T2.5)** em tudo que for gravado a partir da T2.18: `half-up`, `half-even`, `down`, `up`; `normal` legado é lido como `half-up`.
- **C7 — Unidades × motor:** o motor deriva a dimensão do código da unidade (`m2`, `kg/m2`, `m3`, `h`). Unidade homologada com código fora desse padrão (ex.: `m²`) é bloqueada na fórmula com mensagem clara.
- **C8 — Superfícies (D-UX-01):** T2.6–T2.10 e T2.20–T2.23 ficam na aba **Dimensionamento** do card da oportunidade; editor de fórmula e caso de referência (T2.18/T2.19) na Biblioteca técnica e na aba Composições. Nenhum item novo de menu.
- **C9 — Descrição de pré-condições da SPEC-2-007** alinhada à tabela (T2.19 antes de T2.4).
- **C10 — T2.30 concluída** pela D-UX-01 (arquitetura e design system aprovados pela Kim em 09/11).
- **C11 — Contagem:** a fase tem **36 tasks** (T2.1–T2.36); o STATUS passa a contar sobre 36.

**Próxima task de Produto:** T2.18. **Caminho crítico do caso real:** T2.24–T2.29 (Mercogeo).
