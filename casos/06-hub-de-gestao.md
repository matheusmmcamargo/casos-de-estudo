# Caso 6: Hub de gestão

## Contexto
Um painel único para acompanhar financeiro pessoal e da agência hoje, com clientes, comercial e saúde dos produtos nas próximas fases. O foco foi montar a **base de engenharia** certa antes de crescer: banco versionado e deploy sem etapas manuais.

## Arquitetura
- **React + Vite + Tailwind (PWA)**: login, visão do dia, lançamentos e categorias.
- **Supabase:** PostgreSQL, Auth e Edge Functions, com **relatório financeiro diário** enviado por e-mail (Resend).
- **Migrações versionadas** como fonte da verdade do banco.
- **GitHub Actions:** deploy automático no push para a `main`, com script manual de apoio.

## Decisões técnicas
- **Banco no Git:** nenhuma alteração de schema acontece "na mão"; tudo entra como migração revisável.
- **Deploy como código:** o mesmo fluxo roda na máquina e na pipeline, reduzindo erro humano.
- **Estrutura de monorepo leve** (`apps/web`, `supabase`, `scripts`) para acomodar novos módulos.

## Lições
Investir na pipeline antes da funcionalidade deixa cada nova tela mais barata de publicar e mais fácil de reverter.
