# Caso 1: Agente SDR de prospecção

## Contexto
Agência e empresas que dependem de prospecção ativa por WhatsApp perdem vendas por demora na resposta e correm o risco de ter o número banido. O objetivo foi um agente que prospecta, qualifica e entrega leads quentes ao time comercial, **sem comportamento de robô**.

## Desafios
- Enviar volume sem acionar os mecanismos de bloqueio da plataforma.
- Conversar de forma natural e qualificar o lead antes de passar para um humano.
- Dar ao gestor controle (campanhas, funil, limites) sem depender de planilhas.

## Arquitetura
- **App web (React + TypeScript):** CRM, funil, assistente de campanha e simulador do SDR para testar o agente antes de ligar.
- **Agente (Node.js em Docker):** processo separado, com fila, agendador e integração com a API de WhatsApp.
- **Supabase:** PostgreSQL com RLS, Auth e Edge Functions; migrações versionadas para o funil, metas de conversão e gestão financeira.
- **Infra:** `docker-compose` com Caddy como proxy HTTPS, scripts de instalação e atualização em VPS.

## Decisões técnicas
- **Camada de proteção separada da lógica de conversa:** módulos distintos para política de envio, capacidade diária, barreiras anti-robô e aquecimento de números, com atrasos aleatórios.
- **Primeira mensagem sem links nem arquivos:** o agente gera atrito sobre o gargalo do prospect e pede permissão para o time humano enviar a apresentação.
- **Mensagens com variação (spintax) e abertura personalizada** por mercado.
- **Cobrança e limites tratados como regra de negócio testada**, não como detalhe de interface.
- **Funil qualificado por IA com saída para humano** quando o lead esquenta.

## Qualidade
Suíte de testes automatizados do agente cobrindo cobrança, capacidade, barreiras, aquecimento, fluxo de conversa, migração e qualificação.

## Lições
Separar "o que o agente diz" de "quando e quanto ele pode enviar" tornou o risco de banimento um problema de engenharia mensurável, e não de sorte.
