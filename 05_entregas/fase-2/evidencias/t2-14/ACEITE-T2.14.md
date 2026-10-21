# Aceite T2.14 — Encontrar módulos reais no menu conforme o papel

- **Task/SPEC**: T2.14 · SPEC-2-006 · CA-2-11 / UX-F2-006.
- **Versão do preview**: Skip 0.0.74 / `5c9a014`, conferida em 2026-10-21; produção não publicada.
- **Aceite humano**: Paulo confirmou em 2026-10-21 ter executado os cinco cenários; todos foram relatados como funcionando, incluindo a observação de que as entradas administrativas aparecem ao rolar verticalmente.

## Critérios e evidências

| Critério | Evidência observável | Veredito |
|---|---|---|
| Menu/home levam às funções existentes conforme permissões; sem atalhos CRM ou indicadores inventados | RED no preview anterior à mudança: menu Engenharia continha Início/Clientes/Propostas/Projetos/Configurações e home exibia zeros/receita fixa. Após a mudança, snapshot autenticado mostrou Oportunidades, Ficha técnica, Biblioteca técnica, Prontidão e dez entradas administrativas; home sem Clientes/Projetos, zeros, receita, busca ou sino demonstrativos. Paulo confirmou o cenário no teste humano. | PASSOU |
| Contexto das funções preservado | Preview Engenharia: navegação isolada pelas 14 âncoras (`demanda`, `ficha`, `biblioteca`, `prontidao`, `catalogo`, `backup`, `modelos`, `previa`, `fontes`, `gates`, `sla`, `baseline`, `qualidade`, `tempo`) encontrou cada destino e focou seu título; viewport 360px sem overflow horizontal. O snapshot confirmou formulário de Nova demanda e demais superfícies existentes. Teste humano aprovou Biblioteca/Prontidão, voltar, Oportunidades e Administração. | PASSOU |
| Acesso respeita os papéis existentes; ocultar ação não substitui segurança do servidor | A função de navegação usa `viewDashboard`, já atribuída aos seis papéis existentes; ações de mutação mantêm guards existentes. No preview, GET sem sessão retornou 401 e autenticado 200. Comercial leu Biblioteca sem botão de criação; POST de criação de composição e aprovação de prontidão retornaram 403. Paulo confirmou o comportamento Comercial. | PASSOU |
| URLs legadas seguras e rota inexistente | `/clientes`, `/propostas`, `/projetos`, `/configuracoes` voltaram a `/dashboard`; uma rota desconhecida foi para NotFound/404. | PASSOU |
| Motivo de duplicidade e bloqueio de segunda composição preservados | Regressão HTTP autenticada no preview, código geotecnia `COMP-TESTE-01`: 409 `code_duplicated` com motivo real. GET antes/depois encontrou uma única versão; total de composições permaneceu 2→2. Esse teste de regressão foi uma chamada HTTP direta, não uma nova submissão pela UI; a exibição do motivo na UI já está documentada na prova da T2.13. O endpoint registra tentativas rejeitadas conforme seu comportamento existente. | PASSOU |
| Responsividade e teclado do recorte | Home medida em 360/768/1440px: largura do documento igual à viewport, sem overflow; alvos principais 58px; contraste calculado 5,26:1 para texto explicativo e 9,72:1 nos links. Drawer: 15 alvos com altura mínima de 44px, contraste de texto 9,72:1; Tab/Shift+Tab exercitados; Escape fechou e devolveu foco ao acionador. Paulo confirmou o cenário mobile. Não foi produzido laudo de leitor de tela nem contraste de todas as superfícies legadas. | PASSOU no recorte medido |
| Entrada contextual da Ficha sem demanda | `/painel-tecnico?secao=ficha` sem oportunidade selecionada exibiu o título contextual, explicou a pré-condição e ofereceu “Abrir Oportunidades”; sem dados fictícios. A ficha e os formulários legados continuaram visíveis no painel. | PASSOU |

## QA e testes automatizados

- Evidências detalhadas (matriz RED/GREEN, permissões, URLs, duplicidade, responsividade, QA e limitações): [`PROVAS-T2.14.md`](PROVAS-T2.14.md).
- As capturas/JSONs de execução foram preservadas localmente em `artifacts/t2-14/`; os resultados essenciais estão consolidados no recibo canônico de evidências.
- Revalidação completa do código/preview confirmou formulário de Oportunidades, Ficha contextual e superfícies existentes. Nenhum hook, endpoint, migration, schema ou permissão foi alterado.
- A plataforma Skip retornou `test.ran:false` (suíte pulada); 16/16 testes locais passaram dentro das limitações descritas no recibo de evidências. Produção não publicada.

## Limites preservados

A T2.14 organiza acesso contextual às superfícies atuais; não extrai a Biblioteca (T2.15), cria CRM comercial, muda regras de negócio ou libera cálculo real. O gate continua **BLOQUEADO — 0/4 dependências BLK-1..4 resolvidas**. O teste 409 foi regressão de API direta; não representa reenvio pelo formulário nesta task.