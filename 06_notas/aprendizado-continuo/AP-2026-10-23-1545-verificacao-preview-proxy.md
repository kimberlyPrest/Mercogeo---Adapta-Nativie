# AP-2026-10-23-1545 — Verificação HTTP do preview bloqueada pelo proxy do ambiente

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T2.31 / SPEC-2-006
- Sinal: no fechamento da T2.31, toda requisição HTTP direta ao preview (`/`, `/demandas`, `/biblioteca`) retornou 403 pelo proxy do ambiente — inclusive rotas que já existiam e funcionam. O bloqueio não distingue rota nova de antiga, portanto não é evidência sobre a entrega.
- Evidência: execução de `urllib` contra `https://login-crm-merco-geopolimeros-3076d--preview.goskip.app` em 2026-10-23, três rotas, todas com HTTPError 403 antes de qualquer HTML; contraste com o registro da T2.15, em que a mesma verificação havia retornado estados distintos por rota.
- Regra reutilizável: ao verificar rota no preview por HTTP direto, incluir sempre uma rota de controle já existente. Se o controle também falhar com 403, registrar como limitação de observabilidade e sustentar o caminho real no teste humano — não tratar o 403 como falha da entrega.
- Quando aplicar: fechamento de tasks de UI verificadas por requisição HTTP ao preview, quando houver proxy de saída no ambiente de execução.
- Quando não aplicar: quando a checagem autenticada funcionar (sessão válida, controle respondendo 200); nesse caso o 403 por rota é sinal legítimo de falta de permissão.
- Confiança: média — o padrão foi observado uma vez, mas o contraste com uma execução anterior bem-sucedida sustenta a leitura de bloqueio ambiental.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
