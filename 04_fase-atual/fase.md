# Fase 2 — Dimensionamento e catálogo homologado

## Resultado

Transformar a ficha técnica do serviço-piloto em quantitativos e recursos reproduzíveis, mantendo a decisão de engenharia humana e exibindo a memória de cálculo.

## Inclui

- biblioteca versionada de serviços, recursos e composições;
- dimensionamento assistido;
- validação de unidades, campos e vigência;
- ajustes técnicos justificados;
- clonagem controlada de casos;
- área de trabalho por módulo, sem indicadores fictícios (expansão 14/10);
- unidades, vínculo ficha → composição, editor estruturado de fórmula e fixture executada na homologação (expansão 14/10);
- solução técnica com várias composições, quantitativos consolidados por recurso, painel de pendências e exportação da memória (expansão 14/10);
- tasks explícitas, com dono, para destravar BLK-1..4 e aprovar o gate da família (expansão 14/10).

## Critérios de aceite

- **CA-2-01:** cada composição ativa possui código, unidade, coeficientes, fonte, versão, vigência, dono e aprovação.
- **CA-2-02:** composição em rascunho, inativa ou vencida não pode integrar resultado aprovado.
- **CA-2-03:** para fixture homologada, o sistema reproduz o resultado esperado dentro da tolerância definida e apresenta a memória de cálculo.
- **CA-2-04:** unidade incompatível, entrada ausente ou coeficiente inválido bloqueia o cálculo e identifica a causa.
- **CA-2-05:** a seleção da solução e das composições exige confirmação do responsável técnico e fica auditada.
- **CA-2-06:** ajuste manual preserva valor calculado, novo valor, justificativa, autor e data.
- **CA-2-07:** mudança de versão da composição não altera orçamento já congelado.
- **CA-2-08:** clonagem cria novo rascunho e exige reconfirmação de custos vencidos, documentos, prazos e premissas.
- **CA-2-09:** pelo menos uma proposta real percorre ficha → dimensionamento → revisão técnica; a prova inclui registro de tela, memória calculada pelo sistema e declaração do responsável de que a planilha foi usada apenas como referência de conferência, não como calculadora de produção.
- **CA-2-10:** usuário não autorizado não consegue criar, homologar, inativar ou alterar composição.
- **CA-2-11:** toda função entregue nas Fases 1 e 2 é alcançável pelo menu conforme o papel; Oportunidades, Ficha, Biblioteca e Prontidão têm superfícies próprias; Administração pode usar índice com acesso contextual às seções preservadas; nenhuma tela exibe indicador numérico sem fonte server-side; erros de negócio exibem o motivo real retornado pelo servidor.
- **CA-2-12:** Engenharia monta entradas, unidades, faixas, vínculo com a ficha e fórmula pela interface, sem editar JSON; unidade não homologada, dimensão incompatível ou valor fora da faixa é bloqueado no servidor indicando o campo.
- **CA-2-13:** composição só é homologada após o servidor executar a fixture assinada na versão exata e o resultado ficar dentro da tolerância; divergência é exibida e auditada.
- **CA-2-14:** uma oportunidade possui solução técnica com duas ou mais composições justificadas, e o sistema exibe quantitativos por item e consolidados por recurso e unidade, rastreáveis até a parcela, sem custo ou preço.
- **CA-2-15:** painel lista toda pendência que impede confirmar ou congelar (tipo, campo, responsável, data); confirmação ou congelamento com pendência aberta é negado com a lista.
- **CA-2-16:** memória de dimensionamento é exportada em JSON e CSV com hash verificável e recibo de auditoria, respeitando o acesso à oportunidade.

## Demonstração visível

Executar uma fixture homologada e uma oportunidade real com solução de várias composições, explicar cada parcela e o consolidado por recurso, demonstrar bloqueios por dado ausente, unidade incompatível e regra inativa no painel de pendências e exportar a memória com hash.

## Fora desta fase

- Custos, catálogo de custos, BDI, preço, cenários, margem e alçadas — Fase 3.
- Documento de proposta com preço (PDF/editável), aprovação comercial e envio — Fase 4.
- Conectores VOBI/OMIE, IA assistiva e painel K1–K3 — Fase 5.
- Conversão automática entre unidades e funções de fórmula além de soma, subtração, multiplicação e divisão — exige emenda homologada.
- Cadastro comercial de Clientes/Projetos como CRM — fora do programa (escopo, item 1).
- Uso de dados reais ou cálculo operacional antes da aprovação do gate da família (T2.29).

## Expansão de 14/10/2026

Kim autorizou ampliar a Fase 2 depois da análise de coerência. Entram 3 SPECs (2-006 a 2-008), 6 critérios (CA-2-11 a CA-2-16) e 17 tasks (T2.13 a T2.29). Nenhum critério anterior foi alterado. As dependências de T2.6, T2.11 e T2.12 foram ampliadas para incluir as novas provas. Execução: uma task por vez; as levas mostram a ordem de dependência, não autorizam execução em lote. Tasks documentais (T2.24 a T2.28) são feitas pelos donos da Mercogeo, com os templates A–D.

## Emenda de jornada e UX — 20/10/2026

Kim aprovou a reformulação documental e sua publicação em 20/10. As tasks T2.1–T2.29 preservam IDs e histórico; T2.30–T2.36 detalham UX. Foco: demanda → ficha → solução/quantitativos → revisão. Preço, CRM, IA, envio e integrações produtivas permanecem fora da fase.

CA-2-11 é alterado explicitamente somente no recorte administrativo: superfícies centrais extraídas; funções administrativas existentes acessíveis por índice contextual, sem perda de função/controle. Não exigir extrair todo painel em uma sessão. Extrações adicionais exigem recorte próprio. Critérios UX-F2-001..008 e cenários estão nos aditivos de cada SPEC, no contrato de experiência e no roteiro de validação.

Próxima sequência: T2.3, T2.14, T2.15, T2.31 e T2.32 concluídas. T2.32 foi aceita pelo champion em 2026-10-27 ("Agora deu certo" após correção do item 9); recibo em `05_entregas/fase-2/evidencias/t2-32/ACEITE-T2.32.md`. As superfícies centrais de Oportunidades e Ficha estão extraídas; resta a T2.36 (índice administrativo), cuja pré-condição T2.14 já está satisfeita, e a T2.34 (prontidão por rótulos, pré-condição T2.15). Apresentar análise e aguardar pedido/autorização explícitos. Uma task por vez e teste humano explícito antes de avançar. A T2.5 permanece pulada por decisão do champion, com a DÚVIDA de consultoria registrada.

T2.29 conserva somente vínculos suportados pelo gate existente; T2.28 é evidência documental obrigatória. Fixture executada/assinada na versão exata também é exigida pelos contratos de composição/cálculo, não inventada como campo de phase2_readiness. A aprovação do gate não dispensa homologação da composição. Gate de domínio pode usar UI existente sem esperar redesign T2.34.

Consultas seguras necessárias para seletores devem ser inventariadas antes do recorte. Se ausentes, parar e registrar necessidade de SPEC de dados/permissão; não criar acesso irrestrito nem inventar endpoint. Sem casos estruturados ainda, T2.33 preserva validação e referência documental vigente; seletor de composition_fixtures só em T2.19/T2.4.

T2.19 executa caso de referência antes de T2.4; T2.22 entrega guard antes de T2.7/T2.9. T2.7 é dona também da prova positiva GREEN-P2-008B. T2.6 pode ser ensaiada com massa sintética isolada e gate de teste válido; qualquer operação real exige T2.29 atual. Nenhum bypass em produção.

## Tasks

| ID | Task | Dono | SPEC | Critério | Aceite binário | Recorte da prova | Evidência esperada | Pré-condições | Status |
|---|---|---|---|---|---|---|---|---|---|
| T2.1 | Preservar recibo de prontidão e seu histórico | Consultor | SPEC-2-001 | RN-21/RN-22/CA-1-13 | Recibo existente permanece íntegro; seu aceite não é abertura do gate. | GREEN-P2-001 | evidencias/T2.1/: versão, esperado/obtido, prova nomeada e aceite do validador | gates gerais | concluída — histórico preservado; T2.13 reconciliada em f533682 |
| T2.2 | Preservar proteção do gate por família | Produto | SPEC-2-001 | Pré-condições F2 | Preservar aprovação/invalidação e 401/403/409 já provados; refazer regressão ao alterar a UI. | RED/GREEN/REG-P2-001 | evidencias/T2.2/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.1 | concluída — histórico preservado; T2.13 reconciliada em f533682 |
| T2.3 | Revalidar criação do rascunho e mensagem de duplicidade | Produto | SPEC-2-002 | CA-2-01/10 | No ambiente verificado, criar/reabrir rascunho e repetir código mostra motivo real sem duplicar registro; não fechar os demais passos por inferência. | RED/GREEN-P2-002A | evidencias/T2.3/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.13 | concluída 2026-10-20 — aceite próprio do champion (rascunho persistido e duplicidade com motivo real, sem novo registro); recibo em evidencias/t2-3/ACEITE-T2.3.md |
| T2.4 | Homologar versão válida e encontrar somente composições utilizáveis | Produto | SPEC-2-002 | CA-2-01/02/10; UX-F2-002 | Pela UI, Engenharia vê versão/fonte/vigência e resultado do caso de referência; homologação exige execução válida dessa referência. Rascunho/inativo/vencido não aparece como utilizável; Comercial não escreve. | GREEN-P2-002B/REG-P2-002 + UX-002-HOMOLOGAR | evidencias/T2.4/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.3, T2.19, T2.33 | bloqueada até concluir pré-condições; uma task por vez |
| T2.5 | Demonstrar cálculo decimal seguro com exemplos sintéticos | Produto | SPEC-2-003 | CA-2-03/04 | Execução no runtime real reproduz valores/limites do contrato e rejeita AST inválido, unidade incompatível e divisão por zero; apresentação da memória distingue simulação de aprovação. | RED/GREEN-P2-003A | evidencias/T2.5/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.3 | bloqueada até concluir pré-condições; uma task por vez (pulada por decisão do champion em 2026-10-23, com DÚVIDA de consultoria registrada) |
| T2.6 | Calcular caso homologado mostrando origem de cada valor | Produto | SPEC-2-003 | CA-2-03/04; UX-F2-003 | Da oportunidade, usuário escolhe ficha/versões por rótulos, solicita cálculo e vê entradas, unidades, resultado e parcelas reproduzíveis; ausências são explicadas no campo; gate real inválido nega cálculo. | GREEN-P2-003B + UX-003-CALCULAR | evidencias/T2.6/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.2, T2.4, T2.5, T2.19, T2.21, T2.22 | bloqueada até concluir pré-condições; uma task por vez |
| T2.7 | Revisar e confirmar tecnicamente a versão calculada | Produto | SPEC-2-003 | CA-2-05; UX-F2-003 | Engenharia revisa itens/memória e confirma com justificativa; pendência ou alteração concorrente nega confirmação e orienta revisão; Comercial não confirma. | GREEN-P2-003B/REG-P2-003 + GREEN-P2-008B + UX-003-CONFIRMAR | evidencias/T2.7/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.6, T2.22 | bloqueada até concluir pré-condições; uma task por vez |
| T2.8 | Ajustar valor com comparação e nova revisão obrigatória | Produto | SPEC-2-004 | CA-2-06; UX-F2-004 | A UI mostra original, ajustado, unidade e motivo; ajuste cria nova versão em rascunho e invalida a aprovação anterior para esse conteúdo; autor/data preservados. | RED/GREEN-P2-004A + UX-004-AJUSTAR | evidencias/T2.8/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.7 | bloqueada até concluir pré-condições; uma task por vez |
| T2.9 | Congelar versão reconfirmada sem pendências | Produto | SPEC-2-004 | CA-2-07; UX-F2-004 | Tela mostra versão e consequência antes de congelar; servidor rejeita pendência/assinatura antiga; mudar composição não altera snapshot congelado e estado somente leitura é explícito. | GREEN-P2-004A/REG-P2-004 + UX-004-CONGELAR | evidencias/T2.9/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.8, T2.22 | bloqueada até concluir pré-condições; uma task por vez |
| T2.10 | Clonar para novo rascunho com reconfirmações visíveis | Produto | SPEC-2-004 | CA-2-08; UX-F2-004 | Usuário autorizado cria um único clone, abre o novo caso e encontra reconfirmações de dados/documentos/prazos; original e aprovações preservados só no histórico; anexos não ganham acesso. | GREEN-P2-004B/REG-P2-004 + UX-004-CLONAR | evidencias/T2.10/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.9 | bloqueada até concluir pré-condições; uma task por vez |
| T2.11 | Demonstrar a jornada com oportunidade real autorizada | Engenharia Mercogeo | SPEC-2-005 | CA-2-09; UX-F2-005 | Após gate e homologações reais atuais, responsável percorre ficha → solução → revisão com memória do sistema; declara planilha apenas como conferência e registra falhas sem corrigi-las silenciosamente. | GREEN-P2-005 + UX-005-REAL | evidencias/T2.11/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.10, T2.23, T2.29, T2.35 | bloqueada até concluir pré-condições; uma task por vez |
| T2.12 | Consolidar aceite técnico e de experiência da Fase 2 | Consultor | SPEC-2-005 | Aceite integrado SPEC-2-005; CA-2-01..16 e critérios UX aprovados na emenda | Consultor consolida matriz integral com esperado/obtido, versão, evidência e aprovador para critérios originais e somente UX expressamente aprovados; falha ou critério não medido impede fechamento. É cerimônia de aceite, não task de implementação nem liberação da fase seguinte. | RED/REG-P2-005 + UX-005-REG | evidencias/T2.12/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.11, T2.35, T2.36 | bloqueada até concluir pré-condições; uma task por vez |
| T2.13 | Preservar correção e aceite das mensagens de negócio | Produto | SPEC-2-006 | CA-2-11 | Preservar o aceite da T2.13 no STATUS; ao sincronizar versões, executar sua suíte sem reabrir aceite automaticamente; correção não encerra T2.3. | RED/GREEN-P2-006A | evidencias/T2.13/: versão, esperado/obtido, prova nomeada e aceite do validador | gates gerais | concluída — histórico preservado; T2.13 reconciliada em f533682 |
| T2.14 | Encontrar módulos reais no menu conforme o papel | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Cada função entregue tem acesso permitido, sem placeholders CRM/indicadores falsos; links levam a áreas existentes e URL antiga tem retorno seguro. Onde não extraído, abrir seção existente com contexto, sem perder função. | RED/GREEN-P2-006B + UX-006-NAV | evidencias/T2.14/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.30, T2.13 | concluída 2026-10-21 — champion confirmou os cinco cenários; recibo `05_entregas/fase-2/evidencias/t2-14/ACEITE-T2.14.md` |
| T2.15 | Abrir Biblioteca em página própria preservando o contrato | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Extrair somente a Biblioteca de composições para rota própria com os mesmos serviços, estados e papéis; criar/reabrir rascunho e erro de duplicidade funcionam sem painel inteiro. Mapa indica T2.31 para demandas, T2.32 para ficha, T2.34 para prontidão e T2.36 para administração transitória. | REG-P2-006 + UX-006-MOD | evidencias/T2.15/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | concluída 2026-10-22 — Paulo confirmou “Testado, funcionou” após reteste do fluxo de criação corrigido; versão Skip 0.0.79/f0b31fa. QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`), Vitest local focado 27/27. Recibo `05_entregas/fase-2/evidencias/t2-15/ACEITE-T2.15.md`; produção não publicada. |
| T2.16 | Escolher unidades e dimensões por nome no cadastro técnico | Produto | SPEC-2-007 | CA-2-12; UX-F2-007 | Engenharia cadastra/homologa unidade com dimensão; seletor distingue rascunho/homologada/inativa e servidor rejeita uso não homologado; Comercial não cria. | RED-P2-007A (unidade/papel) + UX-007-UN | evidencias/T2.16/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.3 | bloqueada até concluir pré-condições; uma task por vez |
| T2.17 | Ligar entradas da composição aos parâmetros da ficha | Produto | SPEC-2-007 | CA-2-12; UX-F2-007 | Selecionar parâmetro por nome/unidade/origem sem ID; ver mínimo/máximo e obrigatoriedade; salvar preserva o vínculo e valores ausentes/unidade divergente/faixa inválida têm mensagem específica. | RED-P2-007A (faixa) + UX-007-MAP | evidencias/T2.17/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.16, T2.33 | bloqueada até concluir pré-condições; uma task por vez |
| T2.18 | Montar fórmula por passos e conferir simulação identificada | Produto | SPEC-2-007 | CA-2-12; UX-F2-007 | Engenharia monta expressão sem JSON/código, desfaz passo e vê dimensão; servidor valida AST e calcula massa sintética identificada sem aprovação operacional; nenhuma função fora do contrato é aceita. | RED/GREEN-P2-007A + UX-007-FORM | evidencias/T2.18/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.5, T2.17 | bloqueada até concluir pré-condições; uma task por vez |
| T2.19 | Executar caso de referência antes de permitir homologação | Produto | SPEC-2-007 | CA-2-13; UX-F2-007 | Na versão exata, registrar e identificar caso de referência com entradas/esperado/tolerância e responsável; executar no servidor e mostrar esperado/obtido/diferença; disponibilizar seleção por rótulo nesta superfície, somente depois de existir composition_fixtures. Divergência mantém rascunho. Massa sintética não substitui contrato e assinatura real. | RED/GREEN-P2-007B/REG-P2-007 + UX-007-REF | evidencias/T2.19/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.18 | bloqueada até concluir pré-condições; uma task por vez |
| T2.20 | Montar solução com várias composições na oportunidade | Produto | SPEC-2-008 | CA-2-14; UX-F2-008 | Engenharia escolhe versões utilizáveis por nome/código/família, ordena/remove itens com justificativa e reabre o rascunho; servidor valida acesso e nenhuma seleção calcula caso real com gate fechado. | RED/GREEN-P2-008A (itens) + UX-008-ITENS | evidencias/T2.20/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.4, T2.18, T2.32 | bloqueada até concluir pré-condições; uma task por vez |
| T2.21 | Conferir quantitativos por item e total por recurso | Produto | SPEC-2-008 | CA-2-14; UX-F2-008 | Dados sintéticos isolados com recurso repetido mostram soma decimal exata e origem por parcela; mesmo recurso em unidades diferentes fica separado; cálculo real continua condicionado ao gate. | GREEN-P2-008A (consolidação) + UX-008-TOTAL | evidencias/T2.21/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.20, T2.5 | bloqueada até concluir pré-condições; uma task por vez |
| T2.22 | Resolver pendências antes de confirmar ou congelar | Produto | SPEC-2-008 | CA-2-15; UX-F2-008 | Painel lista tipo/campo/responsável/data, abre origem permitida e atualiza após correção; guard compartilhado nega tentativa com pendência, inclusive por chamada direta. Teste do guard em instância isolada antecede ligação das ações T2.7/T2.9. | RED-P2-008B + UX-008-PEND | evidencias/T2.22/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.21, T2.17 | bloqueada até concluir pré-condições; uma task por vez |
| T2.23 | Exportar memória técnica conferível pela interface | Produto | SPEC-2-008 | CA-2-16; UX-F2-008 | Da versão congelada autorizada, exportar JSON/CSV, conferir conteúdo/unidades/hash e recibo; erro não mostra sucesso nem arquivo vazio como válido; exportação não envia proposta. | GREEN-P2-008C/REG-P2-008 + UX-008-EXP | evidencias/T2.23/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.9, T2.21 | bloqueada até concluir pré-condições; uma task por vez |
| T2.24 | Escolher e registrar a família-piloto | Comercial Mercogeo | SPEC-2-001 | RN-01/RN-21 | Template D parte 1 assinado registra família e tratamento do modelo alternativo; sem escolha inferida pelo executor. | GREEN-P2-001 (família) | evidencias/T2.24/: versão, esperado/obtido, prova nomeada e aceite do validador | gates gerais | pendente — dependências e teste humano obrigatórios |
| T2.25 | Homologar SLA real da família escolhida | Engenharia Mercogeo | SPEC-2-001 | RN-21 | Template A e parâmetro homologado no sistema estão vinculados à família e ao dono; evidência verificável, não apenas texto de aprovação. | GREEN-P2-001 (SLA) | evidencias/T2.25/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.24 | bloqueada até concluir pré-condições; uma task por vez |
| T2.26 | Congelar baseline ou assinar parecer de limitação | Engenharia Mercogeo | SPEC-2-001 | RN-22 | Template B e baseline/parecer registram comparabilidade e limitações; não declarar ganho sem medição. | GREEN-P2-001 (baseline) | evidencias/T2.26/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.24 | bloqueada até concluir pré-condições; uma task por vez |
| T2.27 | Comprovar recuperação real em instância isolada | Dados Mercogeo | SPEC-2-001 | CA-1-13 | Template C inclui dados/anexos/configuração necessários e comparação antes/depois; hash ou HTTP200 isolado não satisfaz a prova. | GREEN-P2-001 (recuperação) | evidencias/T2.27/: versão, esperado/obtido, prova nomeada e aceite do validador | gates gerais | pendente — dependências e teste humano obrigatórios |
| T2.28 | Assinar contrato e caso de referência da composição real | Engenharia Mercogeo | SPEC-2-001 | RN-02/CA-2-03 | Template D parte 2 assinado contém entradas/unidades/faixas/coeficientes/fórmula/resultado/tolerância/precisão/arredondamento/versão; valores reais não são escolhidos pelo executor. | GREEN-P2-001 (fixture) | evidencias/T2.28/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.24 | bloqueada até concluir pré-condições; uma task por vez |
| T2.29 | Aprovar condições de uso real com vínculos verificáveis | Engenharia Mercogeo | SPEC-2-001 | RN-21/RN-22/CA-1-13; UX-F2-001 | Engenharia seleciona os vínculos já suportados pelo gate atual e solicita aprovação; servidor confere família/SLA/baseline/recuperação/recibo nos termos do contrato existente, nega vínculo ausente/inválido e invalida quando referência suportada muda. Contrato/fixture real T2.28 é pré-condição documental explícita, não vínculo server-side inventado no schema atual. Ainda que este gate esteja aprovado, cálculo e homologação reais exigem composição/fixture assinada, executada e válida na versão exata nos seus próprios contratos; divergência bloqueia ação. | GREEN-P2-001 (aprovação) + UX-001-GATE | evidencias/T2.29/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.2, T2.25, T2.26, T2.27, T2.28 | bloqueada até concluir pré-condições; uma task por vez |
| T2.30 | Revisar a jornada e a especificação visual da área de trabalho | Consultor | SPEC-2-006 | UX-F2-006 (proposto) | Kim revisa documento com navegação por papel, hierarquia de oportunidade, lista/ficha/solução, estados e regra mobile; orientação verde/laranja e remoção de adorno ficam explícitas. Aprovação é só de design, não aceite da fase. | UX-006-DESIGN | Registro de decisão da Kim por seção (aprovada/ajustar/rejeitada), versão do contrato visual e mapa de navegação, sem inferir aceite do produto | gates gerais | decisão de jornada/UX aprovada pela Kim em 20/10; conferência visual por seção antes de alterar telas |
| T2.31 | Criar e retomar demanda na lista de oportunidades | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Nova demanda abre formulário real; salvar abre detalhe persistido; lista/busca usam registros autorizados e filtros existentes efetivos; vazio, falha e carregamento distintos; voltar preserva contexto e não há CRM novo. | UX-006-OP | evidencias/T2.31/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.15 | concluída 2026-10-23 — Paulo confirmou “O teste da t2.31 foram bem sucedidos”; versão Skip 0.0.80/423a270. QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`), regressão local 47/47. Recibo `05_entregas/fase-2/evidencias/t2-31/ACEITE-T2.31.md`; produção não publicada. |
| T2.32 | Preencher e revisar ficha em contexto da oportunidade | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Usuário usa dados/campos existentes com rótulos/unidades/origem, anexos autorizados, histórico e erros no campo; falha preserva preenchimento; salvar reabre versão correta sem JSON ou ID digitado. | UX-006-FICHA | evidencias/T2.32/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.31 | concluída 2026-10-27 — Paulo confirmou os itens 1–8 e, após a correção do item 9, “Agora deu certo”; versão Skip 0.0.82/8bfdeef. QA setup/estática/build/integrações PASS, suíte Skip pulada (`ran:false`), regressão local 64/64. Recibo `05_entregas/fase-2/evidencias/t2-32/ACEITE-T2.32.md`; produção não publicada. |
| T2.33 | Editar composição e recursos por linhas e seletores | Produto | SPEC-2-002 | CA-2-01/10; UX-F2-002 | Criar/reabrir composição com catálogo por nome/código, recursos em tabela e entradas rotuladas, sem pipe/ID/JSON. Neste recorte não há seletor de composition_fixtures, ainda inexistente. Preservar fonte e validações atuais de fixture_ref com referência documental assinada verificável fornecida pela Engenharia; estado sem referência explica bloqueio e conserva campos. Não cadastrar referência fictícia nem afirmar rascunho salvo quando a API negar. Se o contrato atual exigir caminho técnico inevitável, parar e registrar emenda de dados antes de implementar. Seleção do registro estruturado é T2.19/T2.4. | UX-002-EDITOR | evidencias/T2.33/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.3, T2.15 | bloqueada até concluir pré-condições; uma task por vez |
| T2.34 | Entender e preparar prontidão sem digitar IDs | Produto | SPEC-2-001 | UX-F2-001 (proposto) | Família exibe bloqueios/dono/data; selecionar por rótulos apenas SLA/baseline/evidências que possuam consulta segura existente. Não prometer seletor de fixture estruturada no gate. UI envia os mesmos vínculos do contrato vigente e o backend revalida; consulta ausente bloqueia o recorte até emenda explícita, sem acesso irrestrito. | UX-001-UI | evidencias/T2.34/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.15 | bloqueada até concluir pré-condições; uma task por vez |
| T2.35 | Validar jornada sintética e acessibilidade antes do caso real | Consultor | SPEC-2-005 | UX-F2-005 (proposto) | Champion/Engenharia, com papéis separados, executam roteiro sem IDs fornecidos pelo executor; mediador não ensina caminho; conclusão de todos cenários + falhas registradas + aceite explícito. Protótipo/documento não conta como software validado. | UX-005-SINT/UX-005-REG | evidencias/T2.35/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.10, T2.23, T2.32, T2.33, T2.34, T2.36 | bloqueada até concluir pré-condições; uma task por vez |
| T2.36 | Organizar entrada administrativa e evidências existentes | Produto | SPEC-2-006 | CA-2-11; UX-F2-006 | Entregar índice administrativo com destinos autorizados para baseline/SLA/backup/fontes/gates/catálogo/modelos/prévia/tempo/qualidade; abrir seções existentes por entradas contextuais preserva os serviços. Não extrair nem redesenhar todas essas telas nesta task; não exigir recibo técnico na jornada cotidiana nem ampliar acesso. | REG-P2-006 + UX-006-ADM | evidencias/T2.36/: versão, esperado/obtido, prova nomeada e aceite do validador | T2.14 | bloqueada até concluir pré-condições; uma task por vez |

## Emendas

| Data | Origem do sinal | Micro-spec/task | Motivo |
|---|---|---|---|
| | | | |

## Aditivo de jornada e UX — aprovado por Kim em 20/10/2026

Este aditivo prevalece nos recortes explicitamente alterados. Preserva evidências e aceites anteriores; não aprova software ou uso real por si só.

## Resultado observável aprovado para planejamento

Navegação por papel abre módulos reais; usuário cria/retoma demanda, usa ficha e alcança solução com contexto, estados honestos e identidade visual revisada. Governança fica organizada sem apagar funções.

## Limites, dependências e segurança

Esta é ampliação explícita do limite atual: substituir a exclusão de redesign visual por reorganização visual e interacional definida em ../contrato-experiencia.md. Propõe também revisar CA-2-11: rotas próprias para superfícies centrais; administração pode usar provisoriamente índice com entradas contextuais às seções existentes, sem prometer extração integral nesta onda. Sem aprovação desse desvio, o CA original de rota própria por função permanece e a extração administrativa precisa de novas tasks antes de liberação. Não inclui CRM, novas permissões, conectores, preço ou alterações de regra de negócio.

Aplica o contrato comum de execução vigente (autorização server-side, auditoria, idempotência, versões, unidades, vigência e isolamento sintético). Qualquer demanda de endpoint novo ou mudança de dado/permissão/integração sai desta minuta e exige SPEC explícita antes de executar. Herda limites de aritmética/cálculo das SPECs técnicas. Não inventar dados nem homologação.

## Fluxo e recuperação

Validar especificação visual → expor menu real → extrair por módulo → usar lista/detalhe/ficha → administrar controles existentes por permissão.

Seguir padrões globais de estado vazio, carregamento, erro, conflito, foco, teclado e responsive em `../contrato-experiencia.md`. Ausência de dado é pendência, não zero. Recusar ação indevida no servidor mesmo via URL/API direta.

## Critério adicional para aprovação

- [ ] **UX-F2-006:** Navegação por papel abre módulos reais; usuário cria/retoma demanda, usa ficha e alcança solução com contexto, estados honestos e identidade visual revisada. Governança fica organizada sem apagar funções. Critérios de layout/teclado/contraste/estados do contrato UX precisam ser demonstrados nas superfícies alteradas. Os CA-2-01..16 originais não são renumerados nem dispensados; única mudança de alcance reformulação é CA-2-11 na emenda da SPEC-2-006, que exige decisão explícita da Kim. Sem essa decisão, o critério original permanece.

## TDD da emenda (aprovado para planejamento, não executado)

| Etapa | Cenário verificável | Resultado/evidência |
|---|---|---|
| RED | Na versão real conferida, executar cada cenário nomeado na coluna Recorte da prova abaixo, com o critério binário da task como esperado | Registrar falha inicial em captura/DOM e esperado × obtido; não fingir RED se já passa |
| GREEN | Repetir o mesmo cenário após o recorte mínimo, usando massa sintética isolada e API real do ambiente de teste onde aplicável | Todos critérios do recorte passam; registrar UI, persistência, negativa e versão |
| REGRESSÃO | Repetir provas originais desta SPEC, 401/403/409 e roteiro de jornada/UX nas superfícies tocadas | Sem regressão dos contratos, sem ampliação de acesso, sem bypass de gate |

**Provas novas desta emenda:** UX-006-DESIGN / UX-006-NAV / UX-006-MOD / UX-006-OP / UX-006-FICHA / UX-006-ADM. Cada identificador é um cenário com condição/ação/resultado definido na task correspondente, não nome de suíte já existente. Os nomes não são comandos inventados.

**Comandos existentes de referência:** `npm test -- --run`, `npm run build`, `npm run lint` no projeto de código, depois de confirmar scripts/versão reais. UI/E2E deve usar runner efetivamente disponível ou roteiro manual gravado + prova API, distinguindo mocks de integração. Etapa skipped/bloqueada não conta como teste aprovado.

**Dados e validador:** sintéticos rotulados em instância isolada; Engenharia/champion validam interação, Consultor revisa matriz; caso real só após gate e homologações atuais. Não incluir segredos nas capturas. Evidências por task em `evidencias/<id>/`, sem afirmar que já existem.

## Checklist de liberação (pré-implementação)

- [ ] Decisão da Kim em 20/10 autoriza esta revisão documental; implementação exige os gates por task.
- [ ] Checks de escopo/cliente aplicáveis reconciliados, sem aprovação presumida.
- [ ] Versões Skip/GitHub/evidências conciliadas e mapa de acesso registrado.
- [ ] Cada recorte cabe em uma sessão ou foi decomposto antes da execução.
- [ ] RED/GREEN/regressão e teste humano vinculados ao recorte antes de encerrar.

## Risco e rollback

Reorganização pode perder estado compartilhado, vínculo ou acesso. Se a regressão falhar, voltar à superfície anterior autorizada, sem apagar dados, versões ou evidências; nunca voltar a exibir dados fictícios como reais. Não alterar migration aplicada nem fazer migração destrutiva. Na hipótese de consulta segura ausente, parar e especificar, não improvisar.


### Regras de integração e precedência desta revisão

- Consultas de seletores só reutilizam fontes autorizadas existentes. Falta de fonte/contrato bloqueia recorte até especificação explícita de dados/permissão.
- T2.33 não pressupõe composition_fixtures nem depende de T2.19. Preservar referência documental atual e validações; sem referência verificável não simular sucesso. Cadastro e seleção de caso estruturado são T2.19/T2.4.
- T2.29 valida no servidor apenas vínculos do schema atual (família, SLA, baseline, recuperação e recibo conforme contrato). T2.28 é pré-condição documental, não campo novo prometido. Regra real assinada e fixture executada são verificadas também nos fluxos de cálculo/composição; falha bloqueia operação. Não adicionar fixture_contract_ref por inferência.
- GREEN-P2-008B tem dona explícita T2.7: após resolver pendências, confirmação aceita e painel vazio, com API/UI/auditoria. T2.22 prova guard/negativas antes de haver fluxo de confirmação liberado.
- Roteiro comum de prova: ../roteiro-validacao-ux.md. Cada sufixo UX é um cenário com condição, ação e esperado na task correspondente; cenários compostos devem ter evidências separadas por ação/superfície. Campos de prova nomeiam cenários, não testes já existentes.
- Dependências e aceites da tabela Tasks nesta versão prevalecem sobre sequências descritivas antigas: T2.19 antes de T2.4, T2.22 antes de T2.7/T2.9, T2.21/T2.22 antes de T2.6 para garantir memória multi-item e negativas; T2.23/T2.35 antes de T2.11 para ensaio/exportação completos; T2.29 pode usar superfície antiga sem depender de T2.34.
