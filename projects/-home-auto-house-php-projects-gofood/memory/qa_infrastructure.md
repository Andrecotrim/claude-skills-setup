---
name: qa-infrastructure
description: "Infraestrutura de QA E2E Playwright — como executar, onde estão os arquivos, o que o fluxo cobre"
metadata: 
  node_type: memory
  type: project
  originSessionId: 160b1656-7688-4c46-9bb7-142e4f966f41
---

## Infraestrutura de QA E2E (Playwright)

Acionável a qualquer momento com `npm run qa`.

**Arquivos:**
- `playwright.config.js` — baseURL `http://gofood.test`, headless, 1440×900, locale pt-BR
- `tests/e2e/qa-fluxo-completo.spec.js` — spec principal
- `tests/e2e/helpers/auth.js` — `loginDevAdmin(page)` via `/dev-login/padaria-qa`
- `tests/e2e/helpers/report-generator.js` — gera `_docs/qa-reports/REPORT-*.md`
- `tests/e2e/helpers/ticket-generator.js` — cria tickets crítico/alto em `_docs/tickets/`
- `tests/e2e/fixtures/cenarios.js` — 10 cenários (balcão + mesa, dinheiro/débito/crédito/pix/fiado)

**Tenant de QA:** `padaria-qa` — seed via `php artisan db:seed --class=DevSeeder`

**O que cobre:** Login → abertura de turno → 10 comandas (mesas e balcão) → lançar produtos via autocomplete → pagamento no Caixa → tela da Cozinha → fechamento de turno

**Saídas:** relatório MD por tela em `_docs/qa-reports/` + tickets automáticos para achados crítico/alto

**Why:** Criado para permitir QA on-demand a qualquer ponto do desenvolvimento sem setup manual.

**How to apply:** Quando o usuário pedir "rodar o QA" ou "executar o fluxo completo", instruir a rodar `npm run qa` na raiz do projeto.
