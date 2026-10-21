# T2.14 — Evidências RED/GREEN-P2-006B e UX-006-NAV

**Task/SPEC:** T2.14 · SPEC-2-006 · CA-2-11 / UX-F2-006.  
**Preview verificado:** Skip 0.0.74 / `5c9a014` (2026-10-20). Não publicado em produção.  
**Champion:** Paulo Romeiro aprovou os cinco cenários humanos reportados em 2026-10-21.

## RED — versão anterior

No baseline 0.0.73, o snapshot Engenharia mostrava Início/Clientes/Propostas/Projetos/Configurações; Biblioteca e Prontidão não estavam no menu. A home mostrava clientes/propostas/projetos/receita com zeros fixos, formulário de busca e notificações demonstrativas. Detalhes: `RED-preview.txt`, `RED-snapshot.txt`, `RED-engenharia.png` no arquivo local `artifacts/t2-14/`.

## GREEN — navegação e funções reais

Após autenticação como Engenharia, o menu expôs Início, Oportunidades, Ficha técnica, Biblioteca técnica, Prontidão da família e as dez entradas administrativas. A home não contém atalhos CRM, números sem fonte, busca ou sino fictícios.

Teste isolado das 14 âncoras, após renderização estável: cada destino foi localizado e recebeu foco no respectivo título; viewport 360px e scrollWidth 360px em todos:

| Seção | Elemento focado |
|---|---|
| demanda | `secao-demanda` |
| ficha | `secao-ficha` |
| biblioteca | `secao-biblioteca` |
| prontidao | `secao-prontidao` |
| catalogo | `secao-catalogo` |
| backup | `secao-backup` |
| modelos | `secao-modelos` |
| previa | `secao-previa` |
| fontes | `secao-fontes` |
| gates | `secao-gates` |
| sla | `secao-sla` |
| baseline | `secao-baseline` |
| qualidade | `secao-qualidade` |
| tempo | `secao-tempo` |

Matriz máquina: `navigation-stable-engenharia.json`. Uma varredura inicial rápida produziu foco atrasado; não foi aceita como GREEN. Repetição isolada com espera estável substituiu aquela evidência.

## Permissões, compatibilidade e erro

- GET composição e GET prontidão: sem sessão HTTP 401; com sessão autenticada HTTP 200 (`api-read-auth.json`).
- Comercial: Biblioteca acessível para leitura, botão de criar ausente; tentativa POST de criar composição e POST de aprovar prontidão retornaram HTTP 403 (`comercial-negative.json`). O servidor permanece a barreira de segurança; o menu não altera permissões.
- URLs `/clientes`, `/propostas`, `/projetos`, `/configuracoes` redirecionam a `/dashboard`; uma URL desconhecida apresenta NotFound/404 (`compatibility.json`).
- Regressão HTTP direta de duplicidade geotecnia `COMP-TESTE-01`: HTTP 409, motivo `code_duplicated` e texto real do servidor; uma única versão antes/depois e total de composições 2→2 (`duplicate-regression.json`). Não foi uma submissão pela UI nesta T2.14. O endpoint conserva o evento de rejeição em `audit_logs`; nenhuma composição ou versão nova foi criada. A exibição do motivo pela interface está coberta na evidência prévia da T2.13.
- Ficha sem demanda selecionada: rota contextual explica que uma demanda precisa estar selecionada e oferece link para Oportunidades, sem inventar ficha/dados. O snapshot confirmou o formulário de demanda e todas as superfícies legadas visíveis.

## Responsividade e teclado

- Home a 360, 768 e 1440 px: largura do documento igual à viewport, sem overflow; CTAs medidos com 58 px de altura. Contraste calculado: links 9,72:1 e texto explicativo 5,26:1 (`viewport-metrics.json`).
- Drawer mobile: 15 links com alvos de pelo menos 44 px; contraste calculado 9,72:1. Tab/Shift+Tab exercitados. Escape fecha o diálogo e restaura foco no botão “Abrir menu de navegação” (`drawer-metrics.json`, `drawer-close.json`).
- O champion relatou o menu mobile funcionando normalmente. Não foi feito laudo de leitor de tela nem medição de todas as superfícies legadas fora do recorte visual.

## Teste humano do champion

Paulo informou que executou os cinco cenários do roteiro: início sem placeholders/números/busca/sino — “Deu certo”; Biblioteca/Prontidão/contexto — “Deu certo”; funções antigas correspondentes, observando que os demais itens administrativos aparecem ao rolar verticalmente; navegação mobile/teclado — “Funcionando normalmente”; Comercial com leitura sem criação/homologação — “Funcionou”. Considerado teste humano aprovado.

## QA e limites

- QA Skip 0.0.74: setup, análise estática, build e integrações PASS. O QA retornou `test.ran:false`: suíte do Skip PULADA, não PASS.
- Vitest local 3.2.7: 16/16 (9 testes do mapa/permissões + 7 testes do helper de mensagens da T2.13), resultado em `tests-local-16.txt`. Limite: os 9 testes do mapa/permissões usaram uma transcrição normalizada da lógica do projeto fora do checkout integral e sem renderização React; não são prova da suíte integral.
- Revalidação do código completo e preview confirmou formulário de demanda, ficha contextual e superfícies antigas visíveis. Nenhum hook, endpoint, migration, schema ou permissão foi alterado pela T2.14.
- Sem novo build na revalidação final; produção não publicada. `.skip.config.json` ficou pendente e não foi editado manualmente.
- Gate operacional de cálculo segue **BLOQUEADO — 0/4 dependências BLK-1..4 resolvidas**. T2.15 não iniciada.

Arquivos de captura/JSON citados acima permanecem como evidência local em `artifacts/t2-14/`; este recibo registra os resultados de forma canônica no repositório do cliente.