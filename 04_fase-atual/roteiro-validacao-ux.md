# Roteiro proposto de validação da experiência

**Não executado. Critérios aprovados para futura prova do produto.**

## Preparação

- Registrar versão do frontend/backend, família, contas Comercial/Engenharia e dados sintéticos isolados. Confirmar gate de teste válido, contrato e caso de referência sintéticos claramente rotulados; não usar bypass nem alterar o servidor de produção.
- O executor prepara dados, não fornece IDs nem ensina cliques durante a prova. O mediador pode ler o enunciado; qualquer auxílio de navegação fica registrado e impede considerar aquele cenário “concluído sem auxílio”.
- Registrar perfil, viewport, condição, ação, esperado, obtido, evidência e falha. Capturas sem segredos/dados pessoais. Uma gravação contínua pode cobrir vários cenários, desde que os trechos sejam identificados.

## Cenários sintéticos de jornada

| ID | Condição e ação | Resultado binário esperado |
|---|---|---|
| UX-005-SINT-01 | Comercial autorizado entra pela navegação padrão e cria uma demanda sintética | Encontra formulário real; registro salvo aparece na lista e abre detalhe; Nova demanda não retorna ao início sem ação |
| UX-005-SINT-02 | Reabrir demanda; completar ficha com parâmetros/unidade/origem; provocar campo inválido | Versão persistida correta; erro no campo e conteúdo preservado; anexos seguem acesso existente |
| UX-005-SINT-03 | Engenharia entra na Biblioteca e cria rascunho com recursos | Seleciona por nome/código; usa tabela, sem IDs/pipe/JSON/caminho de repo; ausência de referência documental válida bloqueia conforme contrato, sem exigir cadastro de caso estruturado anterior à T2.19 |
| UX-005-SINT-04 | Montar entradas e fórmula, executar referência sintética aprovada e homologar versão de teste | Tela mostra esperado/obtido/diferença, dimensão e versão; referência divergente nega homologação; Comercial recebe negação |
| UX-005-SINT-05 | Montar solução com pelo menos duas composições e recurso repetido | Quantitativos por item e soma exata do recurso; origem da parcela visível; unidades diferentes não somadas |
| UX-005-SINT-06 | Introduzir parâmetro ausente ou versão vencida e tentar confirmar | Painel mostra campo/tipo/responsável/data; servidor nega, inclusive requisição direta; abrir origem permitida e corrigir remove pendência após revalidação |
| UX-005-SINT-07 | Corrigir, recalcular, revisar e confirmar; ajustar valor confirmado | Confirmação ligada à versão; ajuste mostra original × ajustado e cria nova revisão que não reaproveita assinatura antiga |
| UX-005-SINT-08 | Reconfirmar, congelar, mudar composição de origem, exportar e clonar | Snapshot imutável, memória JSON/CSV/hash verificável; clone novo com reconfirmações e original preservado |
| UX-005-SINT-09 | Abrir Administração com cada papel | Somente funções/dados autorizados; índice não concede acesso extra nem elimina controles; evidência interna não invade formulário operacional |

## Erros e recuperação (UX-005-REG)

- 400: mensagem específica, foco no campo e valores conservados; correção permite nova tentativa.
- 401: dados protegidos não são expostos; fluxo de autenticação respeita contrato vigente.
- 403: menu/URL/API não concedem função; não revelar registro não autorizado pela mensagem.
- 409: causa real e caminho de revisão; repetir sem mudança não cria duplicata.
- Rede/500: não afirmar sucesso; tentar de novo respeita idempotência; conservar entrada em memória da tela sem nova persistência sensível não aprovada.
- Duplo clique, concorrência e versão desatualizada: uma mutação válida ou conflito explicado, nunca sobrescrita silenciosa.

## Visual, teclado e telas pequenas

Para cada superfície alterada, repetir o cenário principal em 360, 768 e 1440 px. Registrar: nenhum controle cortado/sobreposto; nenhuma rolagem horizontal global; tabela larga contida e identificada; foco visível; labels associados; ordem de tabulação e retorno de foco em modal; status não dependente de cor. Medir contraste conforme metas propostas no contrato UX e alvos de toque principais. Verificação mecânica/audit automatizado, se houver runner, não substitui inspeção humana.

**Reprovações:** precisar de ID/console/SQL/JSON ou explicação de navegação do executor; clique sem efeito; placeholder; sucesso sem persistência; estado fictício; aprovação com pendência; impossibilidade de usar teclado; valor ausente convertido em zero. Falha abre registro e bloqueia o aceite do recorte; o teste não corrige código ou dados silenciosamente.

## Caso real (UX-005-REAL / T2.11)

Só depois de T2.29 e contratos/homologações reais verificados na versão/família vigentes. Repetir fluxo principal com caso autorizado e minimizado, memória calculada no sistema e declaração de Engenharia de que planilha foi apenas conferência. Se gate invalidar, parar. Sucesso sintético ou aprovação desta minuta não satisfaz o caso real.

## Evidência de fechamento

Para cada critério técnico CA-2-01..16 e critério UX que a Kim aprovar: procedimento, esperado/obtido, versão, evidência e aprovador. Apresentar separadamente teste unitário, integração real, mock, cenário manual e etapa pulada. Nenhum percentual de avanço novo é calculado nesta minuta.

## Método de medição obrigatório

Em cada viewport 360/768/1440: captura com dimensões registradas e conferência de largura do documento versus viewport; rolagem horizontal apenas no contêiner tabelado identificado. Medir alvos principais pelo bounding box no DOM. Registrar pares de cores renderizados de texto/fundo e razão de contraste calculada para texto normal/grande/controle. Percorrer toda ação por Tab/Shift+Tab/Enter/Escape, registrar foco, ordem, fechamento e retorno de modais, rótulos e anúncio de mensagens com leitor disponível. Reportar ferramenta/versão realmente usada e limitações; falta de medição bloqueia apenas o critério correspondente, nunca vira PASS. Não inventar laudo automático.

Cada cenário herdado GREEN-P2-008B é repetido na T2.7: resolver pendência, recalcular quando necessário, painel vazio, confirmação aceita e assinatura ligada à versão. T2.35 reexecuta a mesma integração como regressão.
