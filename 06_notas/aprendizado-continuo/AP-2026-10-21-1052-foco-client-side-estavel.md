# AP-2026-10-21-1052 — Verificar foco após estabilização da navegação client-side

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T2.14 / SPEC-2-006 / UX-006-NAV
- Sinal: uma varredura rápida de navegação SPA observou foco atrasado do destino anterior; a repetição isolada, após renderização e foco estabilizarem, confirmou cada âncora.
- Evidência: `05_entregas/fase-2/evidencias/t2-14/PROVAS-T2.14.md`, matriz 14/14 âncoras e registro da primeira varredura inconsistente.
- Regra reutilizável: em verificações de foco após navegação client-side, aguardar renderização/paint e verificar um destino por vez antes de marcar PASS.
- Quando aplicar: testes de navegação SPA que alterem hash/query, scroll e foco de cabeçalho.
- Quando não aplicar: navegação com carregamento integral do documento ou quando o critério não envolve foco/scroll após renderização assíncrona.
- Confiança: alta — o resultado inicial inconsistente foi substituído por repetição isolada com evidência para todos os 14 destinos.
- Privacidade: sem credenciais, dados pessoais ou transcrição bruta.
