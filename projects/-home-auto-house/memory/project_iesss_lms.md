---
name: iesss-lms-overview
description: Visão geral do projeto iESSS — LMS multi-tenant SaaS para gestão de instituições de ensino
metadata: 
  node_type: memory
  type: project
  originSessionId: 532033e8-b485-46e5-8720-74dfe6c3ea26
---

**iESSS** é uma plataforma SaaS multi-tenant de gestão educacional e financeira para instituições de ensino, desenvolvida pela Isotton Tecnologia.

**Stack:**
- PHP 8.3+ / Laravel 11.9+ / Filament 3.2+ / Livewire
- Tailwind CSS 3.4+ / Vite 6.3+ / Vue.js
- MySQL 8+ / MariaDB 10.6+ / PostgreSQL 13+
- Pagamentos: PagSeguro + PayPal
- Integração externa: EadBox LMS, Google OAuth, WhatsApp

**Domínios principais:**
- Core: Institution (tenant), User, Person, Integration
- Academic: Course, CourseClass, CourseOffer, Student, StudentEnrolment
- Financial: Order, OrderBump, Coupon

**Arquitetura:**
- Multi-tenancy via Eloquent global scopes por Institution
- Admin panel via Filament (rota `/`)
- RBAC via Filament Shield + Spatie Permission
- Rotas públicas: checkout, pagamento, formulário de aluno, thank you page
- Pipeline de matrícula (Brain): GetStudent → GetCourseOffer → GetOrder → EnrolStudent → IntegrateEnrolment
- Multi-idioma: en, pt, es, it

**Why:** Sistema completo para venda e gestão de cursos com gateway de pagamento e integração LMS.
**How to apply:** Sugerir abordagens alinhadas ao padrão Filament + domínios separados (Core/Academic/Financial).
