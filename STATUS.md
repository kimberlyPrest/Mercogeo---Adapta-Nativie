# STATUS — Mercogeo

> Atualizado em 2026-11-09 · Consultoria Adapta

- **Fase 1:** concluída administrativamente com ressalvas (Kim, 30/09); T1.17 concluída em 2026-10-03 — recibo REG-004 (16/17 CAs; CA-1-13 parcial/bloqueado por BLK-1..4). Fechamento definitivo pendente da validação da consultora.
- **Fase atual:** 2 — Dimensionamento e catálogo homologado.
- **Estado F2:** **15/37** tasks concluídas (T2.1, T2.2, T2.3, T2.5, T2.13, T2.14, T2.15, T2.16, T2.17, T2.30, T2.31, T2.32, T2.33, T2.34, T2.36). A fase tem 37 tasks (T2.1–T2.37; a T2.37 foi criada pela D-T2.16); a contagem anterior "13/29" considerava só a tabela original.
- **T2.5 concluída (2026-11-09):** motor decimal + rota de prova sintética na v0.0.150 (`095b88a`), conforme D-T2.5; aceite registrado pela Kim informando teste do champion. Recibo `05_entregas/fase-2/evidencias/t2-5/ACEITE-T2.5.md`.
- **T2.30 concluída (2026-11-09)** pela decisão **D-UX-01** (Kim): arquitetura de trabalho centrada na oportunidade (funil, card com abas, Hoje, Clientes, Painel), design system claro/escuro com as cores da marca, desfecho ganha/perdida, leitura de todas as oportunidades para Gestão/Aprovador/Admin e admin de usuários/permissões. Ver Emendas em `04_fase-atual/fase.md`.
- **Correções de coerência (2026-11-09):** tabela da fase realinhada às SPECs e 11 correções pré-implementação (C1–C11) em `04_fase-atual/fase.md`. Destaque: a T2.6 passa a rodar com composição sintética homologada; o caso real (fixture assinada) vai para a T2.11 — assim o Produto avança até a T2.10/T2.23/T2.35 sem depender do gate.
- **Próxima task de Produto:** **T2.18 — Montar o modelo de orçamento da família** (campos da visita e regras de quantidade em blocos visuais; reformulada em 09/11 pela C15 para substituir a planilha orçamentária), depois **T2.19 — conferir o modelo contra a planilha atual**. A T2.37 (reativar unidade) pode vir antes.
- **Decisões de 09/11 (Kim):** D-T2.33 — reabrir composição por `GET /backend/v1/compositions/{id}`, entregue na T2.18; D-T2.16 — reativação de unidade com auditoria, nova **T2.37**. Correções C12 (cálculo sintético sem gate, sempre como simulação), C13 (contrato de experiência alinhado à D-UX-01) e C14 (rotas novas conferem a matriz de permissões).
- **Caminho crítico do caso real:** T2.24–T2.29 (Mercogeo: família-piloto, SLA, baseline, recuperação real, contrato/fixture real, vínculos do gate). Sem elas não há T2.11 nem cálculo real.
- **Regressão corrigida na consultoria (2026-11-09):** a v0.0.149 havia removido a leitura das mensagens de negócio do servidor (`getErrorMessage`, T2.13). Restaurada no repo de código, branch `ux-crm-propostas`; entra no próximo deploy.
- **Prontidão F2:** recibo GREEN-P2-001 aprovado (`05_entregas/fase-2/PRONTIDAO-F2.md`), porém 0/4 dependências de domínio (BLK-1..4) resolvidas; gate de cálculo operacional segue **BLOQUEADO**.
- **Ressalvas F1:** CA-1-13 sem recuperação real (BLK-1); piloto/SLA sem homologação real (BLK-2); baseline/parecer pendente (BLK-3); família Poliureia/geotecnia sem decisão (BLK-4). Ver `05_entregas/fase-1/RECIBO-T1.17.md` e `05_entregas/fase-2/PRONTIDAO-F2.md`.
- **Limite:** nenhuma operação de cálculo real antes do gate de prontidão da família e das homologações/fixtures exigidas. Esta atualização não publica a aplicação.
