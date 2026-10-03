# TEMPLATE-C — Recuperação real em instância isolada (CA-1-13 / BLK-1)

- **Responsável pelo preenchimento:** Dados
- **Quando usar:** ao demonstrar recuperação real de backup — a ressalva principal da Fase 1
- **Vínculos exigidos:**
  - Backup/restauração/exportação: T1.12 (QA 0.0.46, migrations 0025–0026) — recibos auditados, hash SHA-256, falha segura 409
  - **Fingerprint ou HTTP 200 não é recuperação** (SPEC-2-001)

## Preenchimento

| Campo | Valor |
|---|---|
| Backup completo (dados, anexos e configuração necessária) — arquivo/hash | ⬜ |
| Instância isolada usada (ambiente, data, versão) | ⬜ |
| Restauração executada — recibo | ⬜ |
| Comparação antes/depois — conteúdo de registros (resumo + evidência) | ⬜ |
| Divergências encontradas e tratamento | ⬜ |
| Responsável e data | ⬜ |

## Prova de aceitação

- Restauração em instância isolada com comparação de conteúdo antes/depois — não apenas hash/fingerprint.
- Recibo auditado do backup (coleção backup_receipts).
- Falha segura comprovada se hash inválido (409, nada alterado).
