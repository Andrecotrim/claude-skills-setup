---
name: Projeto Casa Financeira — estado atual
description: Sistema de orçamento doméstico (refatorado do ERP Primoratec), modelos vigentes, fases concluídas e pendentes
type: project
originSessionId: 55638b81-f3f0-4c32-9286-d68ac6971fe7
---
Sistema Laravel 12 + Filament 3 para controle de orçamento doméstico. Refatorado a partir do ERP Primoratec B2B.

**Fase 1 concluída (2026-05-06):**
- Removidos: Cliente, Contrato, ContratoLicenca, FornecedorFavorecido
- Renomeados: Fornecedor→Credor, ContaPagar→Despesa, Pagamento→Receita
- Tabelas: `credores`, `despesas`, `receitas` (ex: `fornecedores`, `contas_pagar`, `pagamentos`)
- Brand name: "Casa Financeira" (era "Primoratec ERP")

**Modelos ativos:**
- `Credor` (tabela: `credores`) — quem você paga
- `Despesa` (tabela: `despesas`) — contas a pagar/pagas, tipos domésticos (moradia, alimentação, saúde, etc.)
- `Receita` (tabela: `receitas`) — entradas (salário, freelance, benefício, investimento, outros)
- `ContratoFornecedor` (tabela: `contratos_fornecedores`, FK: `credor_id`) — contratos recorrentes
- `ExtratoBancario`, `Conciliacao`, `ConciliacaoItem` (usa `receita_id`), `ContaBancaria`

**Fase 2 concluída (2026-05-07):**
- 2a: `Categoria` (tabela: `categorias`, hierárquica, tipos: despesa/receita/ambos)
- 2b: `ContaRecorrente` (ex-`ContratoFornecedor`, tabela: `contas_recorrentes`, FK: `credor_id`, `categoria_id`)
- 2b: `ReajusteContaRecorrente` (ex-`ReajusteContratoFornecedor`, tabela: `reajustes_conta_recorrente`)
- 2c: `OrcamentoMensal` (tabela: `orcamentos_mensais`, valor_planejado vs valor_realizado computado)
- 2c: `Meta` (tabela: `metas`, valor_alvo/valor_atual, progresso em %)
- `Despesa` e `Receita` ganham `categoria_id`
- `Despesa` usa `conta_recorrente_id` (era `contrato_fornecedor_id`)
- Seeder: 28 categorias domésticas padrão

**Fase 3 concluída (2026-05-07):**
- Dashboard: 3 novos widgets (DespesasCategoriaWidget doughnut, OrcamentoProgressoWidget, MetasProgressoWidget)
- RelatorioFinanceiro: corrigidos refs B2B, 8 seções (DRE, projeção, orçado vs realizado, metas)
- Factories criadas: Credor, Categoria, Despesa, Receita, OrcamentoMensal, Meta, ContaRecorrente
- HasFactory adicionado em todos os models acima
- Test: RelatorioFinanceiroTest (7 testes, cobertura end-to-end da página e métodos)

**Fase 4 concluída (2026-05-07):**
- CLAUDE.md reescrito para refletir domínio doméstico (Casa Financeira)

**Fases pendentes:**
- Nenhuma pendente

**Why:** Usuário quer controle financeiro do lar (não empresa). O sistema anterior gerenciava clientes/contratos de software.

**How to apply:** Ao implementar novos módulos, seguir os nomes domésticos (Credor, Despesa, Receita, etc.). Fase 2 deve criar Categoria antes de outros módulos pois ela é dependência de vários.
