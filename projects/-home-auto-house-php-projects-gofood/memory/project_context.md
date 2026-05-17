---
name: project-context
description: "GoFood SaaS para padarias — estado atual do projeto, stack, decisões arquiteturais e problemas resolvidos"
metadata: 
  node_type: memory
  type: project
  originSessionId: 2452baed-cd22-4958-961c-82d86e059d5c
---

GoFood é um SaaS multitenant para padarias construído com Laravel 13 + Filament 5 + stancl/tenancy 3.10 + PostgreSQL schemas separados por tenant.

**Why:** Construído do zero seguindo technical-spec.md em .baseproject/. Pipeline /laravel-pipeline em andamento para implementar módulos funcionais.

**How to apply:** Contexto de todos os agentes do pipeline e qualquer trabalho novo no projeto.

## Estado atual (2026-05-16)

### Infraestrutura completa e funcionando:
- Filament `/setup` panel: login, dashboard, TenantResource, AdminResource
- Super-admin: admin@gofood.test / password
- Tenant de teste: padaria-aurora (Padaria Aurora)
- Todas 4 rotas operacionais respondem: /padaria-aurora/{caixa,mesas,estoque,financeiro}
- Schema tenant criado com 21 tabelas via stancl/tenancy
- User de teste no tenant: admin@padaria-aurora.test / password

### Decisões técnicas chave:
- SESSION_DRIVER=file (database causaria conflito com schema switching)
- CACHE_STORE=file (idem)
- QUEUE_CONNECTION=database (jobs table fica no schema tenant)
- TenantResolver usa slug (não UUID do InitializeTenancyByPath)
- prependToPriorityList usa interface AuthenticatesRequests (não Authenticate::class)
- Migrations tenant renomeadas com timestamps sequenciais para garantir ordem FK

### Pendente (próximo passo do pipeline):
- Agente 1: _docs/plano.md
- Agente 2: _docs/especificacao.md
- Agente 3: implementar módulos funcionais (Caixa, Mesas, Estoque, Financeiro)
- Roles spatie/laravel-permission ainda não criadas automaticamente no tenant
