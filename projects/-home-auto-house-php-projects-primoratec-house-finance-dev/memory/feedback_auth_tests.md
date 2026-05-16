---
name: Testes Feature/Auth sempre falham — ignorar
description: 8 testes de autenticação Breeze falham porque as rotas não existem no app Filament-only
type: feedback
originSessionId: 55638b81-f3f0-4c32-9286-d68ac6971fe7
---
Os 8 testes em `tests/Feature/Auth/` (AuthenticationTest, EmailVerificationTest, PasswordResetTest, RegistrationTest) e `tests/Feature/ExampleTest` sempre falham com RouteNotFoundException ou falha de autenticação.

**Why:** O projeto usa apenas Filament para autenticação (sem Breeze/rota `/login` padrão). Esses stubs foram gerados automaticamente mas nunca foram aplicáveis.

**How to apply:** Ao rodar `php artisan test`, considerar apenas os testes Unit como indicador de saúde. Os 8 falhas Feature/Auth são ruído — não corrigir, não reportar como problema da refatoração.
