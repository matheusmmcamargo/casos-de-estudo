# Caso 5: SaaS de planejamento de corte

## Contexto
Na indústria madeireira, o rendimento de cada tora define a margem. A planilha manual não compara cenários nem registra o histórico. A solução é um sistema web para **simular o desdobro**, cadastrar a operação e gerar relatório.

## Desafios
- Comparar combinações de cortes e apontar a mais rentável.
- Modelar a operação real: perfis de madeira, máquinas, linhas de produção e classes de tora.
- Entregar relatórios em PDF que o gestor leve para a reunião.

## Arquitetura
- **React 18 + TypeScript + Vite + Tailwind** com rotas protegidas e contexto de assinatura.
- **Motor de otimização** em módulo isolado, independente da interface.
- **Supabase** para autenticação, cadastros e histórico.
- **Relatórios:** geração de PDF no navegador a partir de um modelo de relatório.

## Decisões técnicas
- **Motor separado da UI:** a lógica de otimização pode ser testada e evoluída sem tocar nas telas.
- **Cadastros como fonte de parâmetros:** a simulação lê máquinas e perfis cadastrados, o que adapta o sistema a cada serraria.
- **Plano de assinatura** com controle de acesso no contexto da aplicação.

## Lições
O valor percebido estava no número final (rendimento e preço), por isso o relatório em PDF foi tratado como funcionalidade central, e não como extra.
