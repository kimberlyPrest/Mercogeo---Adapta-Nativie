# Mercogeo — jornada e contrato de experiência propostos

**Revisão documental aprovada por Kim em 20/10/2026. Execução por task com gates próprios.**

## 1. Decisão de produto

A Fase 2 é uma central de trabalho técnico: **demanda → ficha → solução e quantitativos → revisão técnica**. Não é um CRM de clientes/obras, não calcula preço e não envia proposta comercial. O fluxo termina em resultado técnico revisado/congelado, com memória exportável. Família, fórmula, unidades, faixas, coeficientes e tolerância continuam decisões da Engenharia.

A marca verde/laranja é preservada como hipótese de direção visual para revisão da Kim. A mudança proposta é hierarquia, densidade, linguagem, acessibilidade e interação, não uma troca cosmética de paleta. Não foi validada visualmente com o cliente.

## 2. Mapa de navegação proposto

**Recorte administrativo aprovado pela Kim nesta revisão:** o CA-2-11 hoje exige rota própria por função. Esta minuta extrai as superfícies centrais e mantém provisoriamente as seções administrativas acessíveis por índice/entrada contextual no painel existente, sem prometer extração integral nesta onda. O CA-2-11 passa a distinguir superfícies centrais próprias de acesso administrativo contextual. Ver `inventario-superficies.md`.

| Área | Quem usa | Conteúdo e ação principal |
|---|---|---|
| Oportunidades | usuários com acesso às demandas | Lista real autorizada; busca por dados existentes; status e responsável existentes; ação Nova demanda. Sem cards de receita, notificações fictícias ou cadastro CRM. |
| Detalhe da oportunidade | Comercial/Engenharia conforme permissões atuais | Cabeçalho cliente/obra e família, estado, responsável, pendências e contexto; seções Ficha técnica, Solução e quantitativos, Revisão e histórico. A ação principal depende da etapa e do papel. |
| Biblioteca técnica | Engenharia/Admin; leitura permitida aos demais | Composições e versões; criação em rascunho; itens, entradas, recursos, fórmula, casos de referência e homologação. Não digitar IDs, JSON ou linhas com separador. |
| Prontidão da família | Engenharia/Admin; leitura apenas se já autorizada | Pendências e evidências da família, com seleção por nomes e verificação do servidor. Estado bloqueado/aprovado/inválido explícito. |
| Administração e evidências | somente papéis já autorizados | Reorganizar as funções existentes de catálogo, SLA, baseline, recuperação, auditoria de fontes, gates, modelos e prévia sem preço; preservar acesso e comportamento. Não ampliar permissão nem apagar função por não ser central à jornada. |

**Permissão:** a proposta não concede acesso novo a nenhum papel. Antes da implementação, inventariar ações e dados autorizados; uma rota nova conserva o mesmo controle server-side. Esconder menu não é controle de segurança. Não dar acesso geral ao papel Admin por suposição fora da política existente.

**Rotas:** os nomes acima são de produto, não URLs novas já implementadas. T2.14 deve registrar o mapa concreto a partir das rotas existentes. Links antigos permanecem com redirecionamento/compatibilidade segura até a regressão, sem descartar contexto.

## 3. Jornada principal

| Passo | O usuário faz | A tela precisa responder | Critério de saída |
|---|---|---|---|
| 1. Encontrar/iniciar | Abre Oportunidades; cria demanda ou retoma uma existente | Lista real ou vazio honesto, busca/filtro efetivos, confirmação do registro e detalhe identificável | Demanda persistida; reabrir mantém dados e vínculo |
| 2. Completar ficha | Preenche parâmetros com nome, valor, unidade, origem e anexos existentes | Grupos legíveis, erro no campo, unidades explícitas, histórico por versão e pendências | Ficha da versão escolhida está válida; não presumir ausências |
| 3. Montar solução | Engenharia seleciona versões utilizáveis e justifica itens | Busca por nomes/códigos, família/estado/vigência, tabela de itens e exclusão consciente | Itens e versões identificados; inválidos explicados, não usados |
| 4. Calcular/conferir | Solicita cálculo, abre memória e consolidado | Resultado do servidor, unidades em todos valores, estado não confirmado e origem de cada parcela | Cálculo reprodutível; não confundir resultado calculado com aprovado |
| 5. Resolver/revisar | Abre pendência, corrige dado, revê solução e confirma | Campo de origem acessível, responsável/data e ação permitida; novo cálculo após correção; 409 explica conflito e permite recarregar | Confirmação só sem pendências e por papel autorizado |
| 6. Ajustar/congelar/exportar | Justifica ajuste, reconfirma, congela e exporta memória | Original × ajustado separados, assinatura ligada à versão, snapshot imutável; JSON/CSV e recibo em detalhes | Versão congelada e memória rastreável; nada enviado ao cliente |
| 7. Reaproveitar | Clona para nova demanda autorizada | Novo rascunho com reconfirmações explícitas; original preservado | Não herdar aprovação, validade ou anexos sem acesso |

## 4. Padrão visual e de interação — requisito proposto

- Um título de página, contexto curto e uma ação primária por etapa; ações destrutivas/secundárias distintas. Retirar grandes banners de “acesso autorizado”, duplicação de boas-vindas, selos decorativos e apresentação de roadmap como módulo utilizável.
- Cabeçalho da oportunidade mantém identificação e estado; itens/ficha/memória agrupados em seções curtas. Administração e evidências não dividem o espaço principal com o trabalho cotidiano.
- Listas/tabelas de itens e recursos têm colunas nome, unidade, coeficiente, fonte e ações. Adicionar/remover linha por controle explícito; não exigir pipe, JSON, ID de banco ou caminho de repositório. Código de composição é identificador de negócio e continua visível.
- Seletores mostram nome/código/versão/unidade/estado necessários para desambiguar e enviam ID interno automaticamente. Sem resultados: informar a causa e oferecer o próximo passo permitido; nunca inventar opção.
- Rótulos de negócio: “caso de referência” na UI, com termo fixture apenas em detalhes técnicos; “condições para uso real” em vez de códigos internos sem explicação. Fonte e evidência de domínio continuam exigidas; o recibo técnico de execução não vira tarefa de digitação do operador.
- Rascunhos só indicam “salvo” após confirmação do servidor. Manter campos preenchidos em falha de envio; saída com alterações não salvas exige escolha explícita. Não introduzir autosave ou novo estado de negócio por inferência.
- Confirmação de ações distingue salvar rascunho, calcular, homologar, confirmar e congelar. Não usar o mesmo botão genérico “Salvar” para tudo.
- Status não depende só de cor; rótulo e explicação presentes. Ações indisponíveis indicam motivo em texto acessível, não só tooltip em botão desabilitado.

### Estados obrigatórios por superfície

| Estado | Comportamento esperado |
|---|---|
| Carregando | Identificação da área carregada e ações de mutação indisponíveis; nunca mostrar zero como resultado temporário. |
| Vazio legítimo | Mensagem específica e ação permitida para criar/retomar; sem prometer módulo futuro. |
| Busca sem resultado | Distinguir de erro e lista vazia; permitir limpar filtros. |
| 400 | Resumo + mensagem no campo; foco no primeiro erro; conservar valores. |
| 401 | Voltar ao login; não expor dados/segredos nem persistir formulário sensível fora do contrato existente. |
| 403 | Explicar permissão; não revelar títulos/dados de registros não autorizados; servidor nega ação direta. |
| 409 | Explicar conflito/pendência; opção de recarregar/revisar antes de reenviar; não duplicar gravação. |
| Falha de rede/500 | Informar falha e permitir tentar novamente quando seguro; respeitar idempotência; nunca afirmar sucesso. |
| Sucesso | Confirmar registro e versão efetivamente salvos e permitir reabrir. |

### Aceite visual/acessível proposto (não resultado medido)

Validar o layout em **360, 768 e 1440 px**: sem corte de controles, sobreposição ou rolagem horizontal da página. Tabela extensa pode rolar dentro de contêiner rotulado com alternativa legível em tela pequena. Navegação por teclado completa, foco visível e restaurado ao fechar modal; modal com título/rótulos e escape quando seguro; mensagens de status anunciáveis. Contraste mínimo proposto: 4,5:1 no texto comum e 3:1 no texto grande/controles essenciais; conferir no render final. Alvos de toque propostos ≥44×44 px nas ações principais. Esses números são **critérios novos para aprovação**, não afirmações sobre conformidade atual.

## 5. Fronteira de desenvolvimento e operação

A demonstração de UX e o desenvolvimento usam apenas massa sintética identificada em ambiente isolado. Fluxo técnico pode ser provado ali com gate de teste válido e rastreável; não desabilitar checagem nem criar bypass para produção. Antes de caso real: T2.24–T2.29 e contrato/fixture de domínio válidos, recuperação real, SLA e baseline/parecer; validar gate novamente a cada ação conforme o contrato. Trocar família, versão ou vínculo que invalide gate deve voltar a bloquear.

## Condições de implementação

A aprovação documental não é aceite de software nem uso real. Conferir consultas seguras por seletor antes de implementar; registrar origem e permissão, sem novo endpoint implícito. Referência documental de composição é preservada até existir cadastro estruturado de casos (T2.19); não pressupor esse seletor em T2.33. Gate existente não recebe campo fictício de fixture: T2.28 é evidência documental; composição/cálculo validam a versão homologada e execução assinada do caso real separadamente. T2.29 pode ser concluída na UI vigente, sem esperar redesign.
