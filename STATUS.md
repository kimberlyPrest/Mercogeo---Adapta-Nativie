# Status — Mercogeo

- **Escopo:** aprovado pela consultora e CSM/cliente.
- **Fase ativa:** Fase 1.
- **SPECs:** 7 publicadas documentalmente.
- **Tasks:** 17 publicadas em tabela operacional e matriz; 16 concluídas, 1 pendente (94,1%).
- **Revisões:** TDD e decomposição/rastreabilidade executadas; correções incorporadas.
- **Implementação:** T1.1 a T1.16 concluídas no SKIP (versões 0.0.4–0.0.58); T1.16 validada por revisão semanal server-side assinada, teste humano aprovado no preview e logs autenticados com criação HTTP 201 e leitura HTTP 200.
- **Evidência T1.16:** migration 0043 aplicada; coleção `time_quality_reviews` protegida; rotas sem sessão HTTP 401; CRUD direto HTTP 403; correção da incompatibilidade de spread no JSVM registrada no debug e no changelog.
- **Achado preservado:** os dois modelos aprovados existentes retornam `family=geotecnia` no backend; um registro possui nome/arquivo de Poliureia. Não houve alteração automática desse dado real.
- **Próximo gate:** análise e autorização operacional da T1.17, consolidação do recibo da Fase 1 e handoff; depende de T1.10, T1.11, T1.14, T1.15 e T1.16, todas concluídas.
