# Caso 3: Plataforma multi-igreja

## Contexto
Uma comunidade religiosa precisava de um app para membros (agenda, avisos, rádio) e de um ambiente de cursos com certificado. O desafio evoluiu para atender **várias igrejas na mesma plataforma**, cada uma com seus dados isolados, e vender os cursos por assinatura.

## Desafios
- Isolar dados de cada organização sem duplicar o banco.
- Controlar quem acessa cada curso (assinatura, presente ou administrador).
- Operar três níveis: membro, administração da igreja e painel master da plataforma.

## Arquitetura
- **React + Vite (PWA)** com design system próprio e rotas protegidas por papel.
- **Supabase:** PostgreSQL com **RLS por igreja**, Auth, Storage e Edge Functions.
- **Stripe:** checkout, webhook e controle de assinatura.
- **Camadas de função:** membro, admin da igreja e master, com painéis separados.
- Funções para convites, integração com WhatsApp e análise de conteúdo.

## Decisões técnicas
- **A regra final de acesso vive no banco (RLS)**, nunca só na interface: mesmo que o front seja alterado, o dado continua protegido.
- **Isolamento por igreja** como migração dedicada, com correção posterior de recursão infinita nas políticas, e blindagem da assinatura contra edição indevida.
- **Migrações versionadas e scripts de cutover** para migrar de um projeto Supabase para outro sem perder dados.
- **Certificados com verificação pública** por código.

## Lições
RLS bem desenhada é a parte mais difícil e a mais valiosa: erros de recursão e de escopo só aparecem com dados reais, então os testes de política precisam acontecer cedo.
