# Registro de decisões

Decisões obtidas na entrevista de produto. Questões técnicas sem validação permanecem propostas, não decisões finais.

| ID | Decisão | Estado |
| --- | --- | --- |
| D-001 | Cliente inicial é um app iOS em React Native, distribuído fora da App Store. | Decidido; método de distribuição aberto |
| D-002 | Login do app usa Conta Google. Um Google principal autentica; contas adicionais são fontes de leitura. | Decidido |
| D-003 | O app começa pronto para múltiplos usuários, com perfis separados. | Decidido |
| D-004 | O núcleo inclui metas de vida/ano/mês/semana/dia e planejamento relacionado; tarefas podem ser independentes. | Decidido |
| D-005 | Configuração inicial por conversa guiada; calendário é conectado depois. | Decidido |
| D-006 | Planejamento semanal usa texto/voz, perguntas essenciais, decomposição de tarefas e plano por dia com prioridades/blocos flexíveis. A pessoa revisa antes de gravar. | Decidido |
| D-007 | Compromissos existentes, trabalho e prazos acadêmicos são âncoras; a IA não os move ou altera. | Decidido |
| D-008 | Conta Google principal pode receber blocos criados pelo app; contas secundárias são somente leitura. | Decidido |
| D-009 | Sem provedor de IA, fluxos de IA ficam bloqueados, mas funções manuais continuam disponíveis. O usuário conecta e paga seu provedor. | Decidido; provedores/métodos disponíveis a validar |
| D-010 | Credenciais do provedor de IA ficam no Keychain e chamadas partem do iPhone por HTTPS/TLS; não armazenar credenciais no backend do app ou em logs. | Decidido |
| D-011 | A nuvem armazena dados com criptografia em trânsito e em repouso; recuperação é administrada pelo serviço, sem chave de recuperação exclusiva do usuário. | Decidido |
| D-012 | A IA não aplica ações ou reorganizações em segundo plano. Um job diário pode consultar o Google Calendar e preparar propostas que aguardam revisão e aprovação; com o app aberto, replanejamentos podem ser aplicados e registrados. | Decidido |
| D-013 | Dados pessoais mínimos podem ser enviados ao provedor escolhido; indicadores simples de energia são aceitáveis. Dados de alto risco e texto bruto de e-mail ficam fora. | Decidido |
| D-014 | Gmail e MCPs personalizados entram depois; começar por conectores selecionados pelo app e com permissões controladas. | Decidido |
| D-015 | Planejamento e edição manual, cronômetro e registro de progresso devem funcionar offline; sincronizar quando a conexão voltar. | Decidido |
| D-016 | Uso inicial é em um único dispositivo por usuário; portabilidade vem depois. | Decidido |
| D-017 | gVisor não entra inicialmente: não há execução de código arbitrário; isolamento por usuário é responsabilidade da arquitetura de dados/API/contexto. | Decidido |
| D-018 | Painéis usam marcos concretos como medida principal de progresso; horas e tarefas são contexto. Barras comparam planejado/realizado; radar mostra ações por área. | Decidido |
| D-019 | Interpretações da IA são hipóteses apoiadas em dados e submetidas à validação do usuário. Dados registrados não são alterados pela interpretação. | Decidido |
| D-020 | Um job diário pode consultar o Google Calendar e preparar propostas de reorganização quando mudanças afetarem o plano; propostas nunca são aplicadas sem revisão e aprovação. | Decidido; viabilidade e mecanismo técnico a definir |

## Questões em aberto

- Método de instalação/distribuição fora da App Store.
- Serviço de nuvem e desenho de autorização multiusuário.
- Provedor(es) de IA e fluxo de conexão por API key/login.
- Política de exportação, exclusão e retenção de conta/dados.
- Conflitos de sincronização, caso o suporte a vários dispositivos seja adicionado.
- Ordem e escopo técnico de conectores para mapa de carreira e materiais da pós-graduação.
