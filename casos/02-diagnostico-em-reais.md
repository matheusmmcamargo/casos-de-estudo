# Caso 2: Diagnóstico em reais

## Contexto
Em vez de pedir "agende uma reunião", o funil entrega valor primeiro: um diagnóstico gratuito de poucos minutos que **estima, em reais por mês, quanto a empresa deixa de ganhar** com processos manuais (por exemplo, leads que esfriam por demora no atendimento).

## Desafios
- Transformar respostas qualitativas em uma estimativa financeira defensável.
- Capturar o lead sem fricção e respeitar a privacidade.
- Medir o funil (onde as pessoas desistem) sem ferramentas pesadas.

## Arquitetura
- **App React** com formulário em etapas, apresentação dos resultados e comparação antes/depois.
- **Motor financeiro** isolado em módulo próprio, com testes unitários.
- **Supabase Edge Functions** para triagem do lead e aviso ao comercial.
- **Eventos de funil** gravados em tabela própria, com RLS e funções seguras (RPC) em vez de acesso direto às tabelas.

## Decisões técnicas
- **Cálculo fora dos componentes:** o motor financeiro é puro e testável, e a interface só o consome.
- **RPCs seguras para escrita pública:** o visitante anônimo só consegue chamar funções específicas, nunca gravar livremente.
- **Página de privacidade e consentimento** desde a primeira versão.
- **Rastreamento mínimo:** eventos próprios no banco, sem dependência de scripts de terceiros.

## Lições
Quando a conta aparece em reais, a conversa comercial muda de "quanto custa?" para "quanto eu recupero?", e o produto passa a vender o payback.
