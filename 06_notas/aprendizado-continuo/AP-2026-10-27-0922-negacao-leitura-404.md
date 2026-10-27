# AP-2026-10-27-0922 — Negação de leitura no PocketBase responde 404, não 403

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T2.32 / SPEC-2-006
- Sinal: no teste humano da ficha técnica, o usuário que não era responsável pela demanda não recebia a mensagem de permissão: via o erro genérico. A regra de acesso do servidor estava correta — ninguém acessou dado indevido; o que falhou foi a apresentação.
- Evidência: documentação oficial de API rules do PocketBase (`https://pocketbase.io/docs/api-rules-and-filters/`): `viewRule` não satisfeita responde 404; 403 fica reservado a regra "bloqueada" (superusuário). Causa confirmada no debug `artifacts/t2-32/DEBUG-T2.32-item9.md`, corrigida em Skip 0.0.82/8bfdeef com 2 casos de regressão em `src/lib/techSheetForm.test.ts`.
- Regra reutilizável: ao apresentar uma restrição de leitura, mapear 404 de leitura para um estado de acesso negado com explicação própria; reservar o estado de erro para falhas reais (500/rede). Tratar apenas 403 como permissão deixa a mensagem de negação inalcançável.
- Quando aplicar: toda tela que abre um registro único por ID e cuja regra de acesso dependa do usuário (responsável, dono, vínculo).
- Quando não aplicar: operações de escrita, em que `createRule` insatisfeita retorna 400 e o caminho é outro; e casos em que um 404 real (registro excluído) precise ser distinguido — nesse caso a mensagem deve cobrir as duas leituras sem prometer qual ocorreu.
- Confiança: alta — comportamento documentado pelo fornecedor e reproduzido no teste humano.
- Privacidade: sem segredo, dado pessoal ou conteúdo bruto.
