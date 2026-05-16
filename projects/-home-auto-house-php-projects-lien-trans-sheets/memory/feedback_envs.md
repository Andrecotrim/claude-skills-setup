---
name: Nunca commitar arquivos .env
description: Os arquivos .env e .env.production nunca devem ser commitados no git
type: feedback
---

Nunca adicionar `.env` ou `.env.production` ao git, nem sugerir isso.

**Why:** Contêm credenciais do banco de dados (senhas de dev e produção).

**How to apply:** Antes de qualquer commit, verificar que esses arquivos estão no `.gitignore` e não aparecem em `git ls-files`.
