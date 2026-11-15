# Arquitetura — Visão inicial

**Status:** proposta conceitual derivada das decisões de produto; não é uma arquitetura técnica aprovada.

## Contexto

O produto terá um cliente iOS em React Native, armazenamento em nuvem e integrações diretas com serviços do usuário. O usuário escolhe e paga seu provedor de IA. O app não executa ações de agente enquanto está fechado; o processamento agentivo começa quando o app está aberto.

## Componentes conceituais

1. **App iOS (React Native):** interface, planejamento manual, dados locais para uso offline, cronômetro, fluxo de revisão, autenticação e integrações.
2. **Armazenamento local:** cache de tarefas e plano; credenciais de provedores em Keychain. O cliente deve suportar edição offline.
3. **Sincronização em nuvem:** guarda perfil, metas, tarefas, histórico e alterações sincronizáveis; aplica autorização por usuário e criptografia em trânsito e em repouso.
4. **Adaptadores de integração:** Google Calendar e futuramente Gmail/mapas de estudo. Cada conta adicional é uma fonte de leitura; a conta principal pode receber blocos criados pelo app.
5. **Camada de IA no cliente:** compõe contexto mínimo, chama o provedor escolhido diretamente e valida respostas antes de executar ações permitidas.
6. **Ferramentas controladas:** operações explícitas, como consultar calendário e criar/editar apenas blocos pertencentes ao app na conta principal. Não expor ferramentas arbitrárias ao modelo.

## Limites de confiança e autorização

- Cada perfil, conexão Google, tarefa e execução de IA pertence a um usuário autenticado; a API e o banco devem validar essa associação em todas as operações.
- O modelo não recebe uma credencial Google ampla nem pode decidir livremente a conta-alvo. O app controla ferramentas, escopos e conta autorizada.
- Calendários adicionais são somente leitura. Eventos preexistentes na conta principal também são tratados como somente leitura pelo agente.
- Escritas no calendário ficam limitadas a blocos gerenciados pelo app. Âncoras de trabalho e prazos acadêmicos nunca são movidos.
- Execução de IA e replanejamento não ocorrem em segundo plano. Ao abrir o app, mudanças podem ser processadas e registradas com um único aviso interno.
- Dados offline sincronizam quando houver conexão. O primeiro escopo presume um dispositivo por usuário; conflitos entre dispositivos ficam para definição futura.

## Isolamento por usuário e gVisor

O requisito é ter contexto, perfil, memória, fontes e permissões separados por usuário. Isso deve ser implementado por autenticação/autorização, isolamento de tenant no serviço e filtragem dos contextos de IA.

gVisor não é requisito da primeira versão: o agente usa ferramentas controladas pelo app e não executa código arbitrário nem extensões de terceiros. Reavaliar sandbox de execução (por exemplo, gVisor em workers Linux) somente se o produto passar a executar código não confiável. Um sandbox de workload não substitui isolamento de dados no banco/API.

## Fluxo de planejamento

1. Carregar perfil e dados autorizados do usuário.
2. Consultar calendário conforme permissões da conta.
3. Montar contexto mínimo para o provedor de IA selecionado.
4. Receber proposta estruturada e validar limites de domínio no app.
5. No planejamento de domingo, mostrar a proposta para revisão antes da escrita.
6. Durante a semana, reorganizações automáticas podem alterar somente tarefas/blocos gerenciados pelo app, com histórico e notificação interna.

## Decisões técnicas pendentes

- Backend, banco, hospedagem, identidade de serviço e modelo de autorização.
- Estratégia concreta de armazenamento e sincronização offline.
- Bibliotecas nativas React Native para Keychain, notificações, calendário e cronômetro.
- Primeiro provedor de IA, formatos de resposta e limites de tokens/dados.
- Escopos OAuth mínimos e ciclo de vida de tokens Google.
- Auditoria, retenção, exportação, exclusão de dados e observabilidade sem dados sensíveis.
- Estratégia de distribuição iOS fora da App Store.
