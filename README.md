# Casos de estudo

Documentação técnica dos sistemas que construí na [Agência Camargo](https://agenciacamargo.com). O código dos projetos de clientes e dos produtos é privado; aqui estão **o problema, a arquitetura, as decisões e o que aprendi** em cada um.

Cada caso segue o mesmo formato: contexto, desafios, arquitetura, decisões técnicas e lições.

| Caso | Tema | Stack principal |
|---|---|---|
| [Agente SDR de prospecção](casos/01-agente-sdr.md) | Automação comercial com segurança contra banimento | Node, React, Supabase, Docker |
| [Diagnóstico em reais](casos/02-diagnostico-em-reais.md) | Funil de diagnóstico com motor financeiro | React, Supabase Edge Functions |
| [Plataforma multi-igreja](casos/03-plataforma-multi-igreja.md) | Multi-tenant, assinaturas e certificados | React, Supabase (RLS), Stripe |
| [SaaS de agenda para terapeutas](casos/04-saas-agenda-terapeutas.md) | Agenda, lembretes e cobrança recorrente | React, TypeScript, Supabase, Stripe |
| [SaaS de planejamento de corte](casos/05-saas-planejamento-de-corte.md) | Motor de otimização e relatórios | React, TypeScript, Supabase |
| [Hub de gestão](casos/06-hub-de-gestao.md) | Operação, financeiro e deploy automático | React PWA, Supabase, GitHub Actions |

## Princípios que se repetem nos projetos

1. **Banco primeiro:** migrações versionadas e RLS antes do código que as usa.
2. **Segurança por padrão:** nenhuma chave secreta no front-end ou no Git; regras de acesso no banco, não só na interface.
3. **Experiência do usuário:** estados de carregamento, mensagens de erro úteis e mobile-first.
4. **Automação testada:** a lógica de negócio crítica (cobrança, limites de envio, motor financeiro) tem testes.
5. **Deploy reproduzível:** build, publicação e permissões documentados e, quando possível, automatizados.

## Contato

[agenciacamargo.com](https://agenciacamargo.com) · [LinkedIn](https://www.linkedin.com/in/matheuscamargo-ia/)
