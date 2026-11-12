# Caso 4: SaaS de agenda para terapeutas

## Contexto
Terapeutas perdem receita com faltas e perdem tempo com agenda e cobrança manuais. O produto reúne agenda, pacientes, fichas e financeiro, com **lembretes automáticos por WhatsApp** e cobrança por assinatura.

## Desafios
- Reduzir faltas sem que o profissional precise mandar mensagens.
- Cobrar a assinatura e bloquear o acesso quando ela vence.
- Funcionar bem no celular, que é onde o terapeuta usa o sistema.

## Arquitetura
- **React + TypeScript + Vite (PWA)** com agenda, pacientes, fichas, painel de métricas e conexão do WhatsApp por QR Code.
- **Supabase:** PostgreSQL com RLS, Auth e Edge Functions.
- **Edge Functions:** envio de lembretes, webhook do WhatsApp, criação de sessão de checkout e webhook do Stripe.
- **Assinaturas** em tabela própria, com tela de bloqueio (paywall).

## Decisões técnicas
- **Lembretes com cobrança de confirmação:** quem não confirmou recebe novo aviso.
- **Webhook do Stripe como fonte da verdade** da assinatura, em vez de confiar no retorno do navegador.
- **Migrações versionadas** para lembretes e assinaturas, evoluindo o banco sem quebrar contas existentes.

## Lições
Em SaaS pequeno, o gargalo não é a funcionalidade, e sim o ciclo de cobrança: tratar renovação, falha de pagamento e bloqueio como fluxo principal evita suporte manual.
