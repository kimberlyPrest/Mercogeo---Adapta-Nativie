# Escopo definitivo — Central de Engenharia de Propostas Mercogeo

**Estado:** APROVADO pela consultora e CSM/cliente  
**Fonte soberana:** direção informada pela Kim em 2026-09-11 — “Inteligência técnico-comercial para dimensionamento, precificação e geração de propostas”.

## 1. Escopo funcional

### Entrada e qualificação

- **RF-01 — Oportunidade técnico-comercial:** cadastrar cliente, contato, origem, família de serviço, local, responsável, data da demanda e prazo informado; o primeiro recebimento deve ser registrado por evento verificável e não pode ser retrodatado sem justificativa auditada.
- **RF-02 — Checklist de aptidão:** manter requisitos mínimos configuráveis por família de serviço e impedir o início do orçamento enquanto faltarem dados obrigatórios, salvo exceção justificada e autorizada.
- **RF-03 — Documentos e evidências:** anexar e classificar arquivos, registros de visita, plantas e premissas vinculando-os à oportunidade.
- **RF-04 — Classificação de complexidade:** classificar a proposta por regra homologada e associar SLA, prioridade e aprovadores.

### Engenharia e dimensionamento

- **RF-05 — Ficha técnica versionada:** registrar parâmetros técnicos uma única vez, com unidade, origem, autor e histórico de alterações.
- **RF-06 — Biblioteca de serviços:** manter serviços, composições, recursos, unidades, coeficientes e vigência, com estado rascunho, homologado ou inativo.
- **RF-07 — Seleção humana da solução:** permitir ao responsável técnico selecionar e justificar serviços e composições; o sistema não decide a solução de engenharia.
- **RF-08 — Dimensionamento assistido:** calcular quantitativos apenas a partir de regras homologadas e exibir entradas, fórmula, versão e resultado.
- **RF-09 — Pendências e inconsistências:** alertar unidade incompatível, parâmetro ausente, fórmula inativa, valor fora da faixa ou composição sem homologação.
- **RF-10 — Ajuste técnico controlado:** permitir ajuste manual com justificativa, autor, data e comparação com o cálculo original.

### Custos e precificação

- **RF-11 — Catálogo de recursos e custos:** manter mão de obra, materiais, equipamentos, mobilização, terceiros, EPIs/EPCs e demais itens com fonte, vigência, dono e histórico.
- **RF-12 — Composição de custo direto:** consolidar quantitativos e custos vigentes por item, grupo, serviço e proposta, sem alterar versões anteriores.
- **RF-13 — Parâmetros de preço e BDI:** manter conjuntos versionados de impostos, ISS, administração, risco, despesas financeiras, contingência e margem, ativados somente após homologação.
- **RF-14 — Formação de preço reproduzível:** mostrar custo direto, componentes do BDI, preço calculado, valor proposto e margem estimada, com memória de cálculo exportável.
- **RF-15 — Simulação de cenários:** comparar cenários sem alterar o orçamento-base e permitir promover um cenário mediante registro da decisão.
- **RF-16 — Exceções e alçadas:** exigir aprovação quando desconto, margem, valor fechado ou parâmetro ultrapassar limite homologado.

### Proposta e governança

- **RF-17 — Aprovação técnica e comercial:** oferecer filas separadas, devolução com motivo e registro de quem aprovou cada versão.
- **RF-18 — Geração de proposta completa:** gerar documento em PDF e formato editável a partir de template aprovado, contendo escopo, quantitativos comerciais, premissas, exclusões, prazo, validade, preço e condições.
- **RF-19 — Templates:** suportar template padrão do piloto e permitir evolução para templates dos clientes/plataformas mais frequentes sem automatizar o preenchimento do portal.
- **RF-20 — Versionamento imutável:** preservar cada versão aprovada ou enviada; qualquer alteração posterior cria nova versão e comparação de diferenças.
- **RF-21 — Clonagem controlada:** reutilizar proposta anterior copiando dados para um novo rascunho, sinalizando valores vencidos, regras substituídas e campos que exigem reconfirmação.
- **RF-22 — Acompanhamento mínimo:** registrar pronta para envio, enviada, revisada, ganha ou perdida, datas e motivo de perda, sem construir um CRM completo.

### Métricas e integrações

- **RF-23 — Instrumentação de tempo:** registrar recebimento verificável, aptidão, versão pronta e envio, além de timestamps de fila e tempo ativo por etapa; medir separadamente o esforço pronta→enviada e exigir pausa justificada para calcular K1–K3.
- **RF-24 — Painel mínimo:** exibir volume, tempo, horas, SLA, retrabalho, propostas por estado e margem estimada por família e período.
- **RF-25 — Exportação auditável:** exportar proposta, memória de cálculo e dados do painel com filtros, usuário, data e registro da ação.
- **RF-26 — Conectores controlados:** importar ou consultar VOB/OMIE somente após homologação de contrato, campos, permissões, reconciliação e fonte de verdade.
- **RF-27 — Custo realizado opcional:** receber custo realizado homologado por integração ou importação controlada e calcular K4 somente após fechamento elegível.
- **RF-28 — Assistência por IA opcional:** sugerir preenchimento da ficha ou rascunho textual usando somente evidências vinculadas e dados aprovados, sempre marcado como sugestão e sujeito a confirmação humana.

## 2. Regras de negócio

- **RN-01:** o serviço-piloto deve ser escolhido e seu catálogo homologado antes da ativação do cálculo automático.
- **RN-02:** toda regra de cálculo deve ter versão, vigência, dono, fonte e aprovação.
- **RN-03:** dados ausentes não podem ser convertidos em zero ou valor padrão sem indicação explícita.
- **RN-04:** composição em rascunho ou inativa não pode integrar proposta aprovada.
- **RN-05:** mudanças em custos, coeficientes, BDI ou templates só afetam novos rascunhos e novas versões.
- **RN-06:** a solução técnica, o conjunto de composições e qualquer ajuste técnico dependem de responsável habilitado.
- **RN-07:** proposta não avança para aprovação sem checklist mínimo, memória de cálculo e identificação das versões utilizadas.
- **RN-08:** exceção comercial exige justificativa e aprovador conforme matriz de alçadas homologada.
- **RN-09:** versão aprovada ou enviada é imutável.
- **RN-10:** clonagem nunca herda silenciosamente custos vencidos ou regras substituídas.
- **RN-11:** o relógio contratual de K1 inicia no primeiro registro verificável do recebimento da demanda e termina no registro do envio; recebida→apta, apta→pronta e pronta→enviada são medidos separadamente. Baseline e resultado devem usar a mesma fronteira e calendário.
- **RN-12:** K2 soma tempo ativo dos participantes, incluindo qualificação e esforço de portal até o envio; a qualidade do registro é revisada semanalmente por responsável nomeado e não pode ser inferida apenas do intervalo corrido.
- **RN-13:** K3 usa todas as demandas elegíveis da família-piloto cujo SLA venceu ou que já foram enviadas; o SLA vigente na data de aptidão permanece associado à versão, e exclusão exige motivo auditável.
- **RN-14:** K4 não é exibido como atingido sem custo realizado, regra de fechamento e fórmula de desvio homologados.
- **RN-15:** dado vindo de VOB/OMIE deve informar origem, momento de sincronização e resultado da reconciliação.
- **RN-16:** IA não pode escolher solução técnica, aprovar preço, enviar proposta ou ocultar a origem de uma sugestão.
- **RN-17:** toda perda deve ter motivo; toda devolução para revisão deve indicar o campo ou decisão afetada.
- **RN-18:** o documento gerado deve refletir exatamente a versão aprovada do orçamento.
- **RN-19:** custo vencido ou sem fonte homologada é bloqueado por padrão; uso excepcional exige justificativa, data-limite e alçada equivalente à exceção comercial.
- **RN-20:** o arquivo editável é artefato de trabalho não autorizativo, identificado como tal; somente o PDF aprovado e identificado pode ser registrado como versão enviada.
- **RN-21:** o SLA da família-piloto deve estar homologado antes da ativação da Fase 2; ausência de SLA não pode ser encerrada como sucesso de K3.
- **RN-22:** baseline “antes” deve ser congelado antes do uso das funções de dimensionamento e preço, com critérios de confiabilidade, classes de complexidade e regra estatística documentados.

## 3. Requisitos não funcionais

- **RNF-01 — Segurança:** autenticação individual e autorização por papel para visualizar, editar, homologar, aprovar e exportar.
- **RNF-02 — Auditoria:** trilha append-only das ações críticas, incluindo alterações de catálogo, regras, aprovações, exportações e integrações.
- **RNF-03 — Integridade:** cálculos idênticos com as mesmas entradas e versões devem produzir o mesmo resultado.
- **RNF-04 — Precisão:** valores monetários e percentuais devem seguir precisão e arredondamento homologados, sem uso de ponto flutuante binário em regras financeiras.
- **RNF-05 — Usabilidade:** o caminho principal deve funcionar em desktop e permitir identificar pendências, estado e responsável sem consultar planilha externa.
- **RNF-06 — Desempenho:** para o volume do piloto, recálculo e abertura da proposta devem responder em até 3 segundos, exceto geração documental assíncrona devidamente sinalizada.
- **RNF-07 — Disponibilidade e recuperação:** backup, restauração testada e exportação de saída devem existir antes de dados reais se tornarem fonte operacional.
- **RNF-08 — Portabilidade:** dados e memória de cálculo devem ser exportáveis em formato legível e estruturado.
- **RNF-09 — Privacidade:** dados pessoais e documentos de clientes devem ter acesso mínimo, retenção definida e não serem enviados a IA sem base e autorização.
- **RNF-10 — Observabilidade:** falhas de cálculo, geração, importação e sincronização devem gerar registro técnico sem expor segredos.
- **RNF-11 — Idempotência:** importações e sincronizações repetidas não podem duplicar oportunidades, custos ou lançamentos realizados.
- **RNF-12 — Segredos:** credenciais de integrações nunca podem estar em código, documento, log ou exportação.

## 4. Fora do escopo

1. CRM completo, marketing ou prospecção do Merco Tape.
2. Gestão operacional da obra, compras, estoque, financeiro ou faturamento completos.
3. Substituição de OMIE/VOB sem decisão formal.
4. Envio automático e automação de portais externos.
5. Decisão autônoma de engenharia ou aprovação comercial.
6. Fórmulas, custos e BDI não homologados.
7. Margem realizada sem fonte real confiável.
8. Automação da visita técnica.
9. Preparação operacional da obra.
10. Expansão simultânea para todas as famílias antes da validação do piloto.

## 5. Premissas e decisões preservadas

- Uma família de serviço será escolhida no início da Fase 1.
- O documento comercial completo integra o produto; templates específicos entram por frequência e evidência.
- K1 é o KPI central; K2 e K3 complementam o sucesso; K4 é secundário e condicionado.
- VOB e OMIE serão auditados antes de qualquer duplicação ou integração.
- As planilhas atuais são evidência de estrutura, não catálogo aprovado.
