# AP-2026-10-29-1650 — Índice contextual como alternativa honesta à extração de painel monolítico

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T2.36 / SPEC-2-006 (CA-2-11; UX-F2-006)
- Sinal: quando a SPEC proíbe extrair/redesenhar telas de um painel monolítico, uma página-índice com destinos por entrada contextual (âncoras/rotas existentes) organiza a navegação sem tocar o monolito — zero risco de regressão funcional e prova barata por unidade (ids/urls/rótulos).
- Evidência: Skip 0.0.147/41c68e4 — Dashboard.tsx (5.3k linhas) intocado; 6 testes novos de navegação; regressão 165/165; teste humano aprovado de primeira.
- Regra reutilizável: para organizar acesso a funções existentes sem extração, criar índice que navega (não duplica) — derivar os destinos das âncoras/rotas reais e provar por unidade que nenhum destino foi inventado e que nenhum rótulo divergiu da função real.
- Quando aplicar: painel monolítico com seções âncora; SPEC com proibição de extração; necessidade de organização navegável.
- Quando não aplicar: quando o critério exige rota própria por função (aí a extração é o recorte) ou quando as âncoras não existem.
- Confiança: alta — padrão aplicado com sucesso e provado por testes + teste humano.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
