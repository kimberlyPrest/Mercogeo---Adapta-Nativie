# AP-2026-10-22-0913 — ID relacional selecionado de registro existente

- Status: candidato
- Escopo: projeto do cliente
- Task/SPEC: T2.15 / SPEC-2-006
- Sinal: formulário de criação recebeu texto livre para `catalog_item_id`, embora o endpoint exija ID de registro real com formato `[a-z0-9]{15}`. A tentativa humana recebeu HTTP 400; os logs registram a mensagem, mas não o payload.
- Evidência: `06_notas/debug/debug-2026-10-22-t2-15-id-catalogo.md`; hook `pocketbase/hooks/composition_versions.js`; testes do helper `src/lib/compositionCatalog.test.ts`.
- Regra reutilizável: para campos relacionais que exigem ID interno, oferecer seleção baseada em registros retornados por uma consulta autorizada e validar que o valor selecionado pertence ao conjunto carregado antes do POST; não depender de texto digitado nem de regex isolada.
- Quando aplicar: formulário relaciona um registro existente e o serviço de leitura autorizado já está disponível.
- Quando não aplicar: o contrato aceita explicitamente identificadores externos/entrada livre ou não existe uma fonte autorizada para listar o registro; nesse caso, especificar a origem e o contrato antes de improvisar.
- Confiança: alta — regra confirmada no hook, formato do campo na coleção, erro observado e teste focado.
- Privacidade: sem segredos, dados pessoais ou payloads brutos.
