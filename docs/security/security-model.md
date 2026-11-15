# Segurança e privacidade — Modelo inicial

**Status:** decisões de produto para revisão; ainda não substitui análise de ameaças, implementação ou auditoria.

## Dados e limites acordados

- Não solicitar nem armazenar identificadores de alto risco desnecessários, como CPF.
- Perfil, metas, tarefas, planejamentos e históricos são armazenados em nuvem para recuperação; o serviço pode tecnicamente acessar os dados necessários ao produto.
- Proteger tráfego com HTTPS/TLS e criptografia em repouso no armazenamento em nuvem.
- A chave/token do provedor de IA fica no Keychain do iPhone; não vai para o backend do app nem para logs.
- Chamadas de IA são diretas do iPhone ao provedor escolhido, somente com o app aberto.
- O provedor escolhido recebe o prompt/contexto enviado. Enviar somente dados mínimos necessários, em vez de contexto bruto completo.
- Gmail entra depois. O texto bruto de e-mail deve ser processado no aparelho e nunca enviado à IA; apenas um resumo de tarefa/prazo pode ser enviado.
- Energia/bem-estar pode ser representada por indicador simples. Não enviar relatos livres de saúde mental.
- O usuário pode revogar conexões e corrigir/remover dados pessoais, sujeito a uma política de exclusão/exportação ainda a definir.

## Controles de projeto

### Armazenamento e autenticação

- Guardar segredos de provedores no Keychain, nunca em preferências simples, código, analytics ou arquivos de log.
- Usar autenticação Google para identidade do app e autorização OAuth com escopos mínimos para integrações Google. Não pedir a senha Google dentro do app.
- Isolar todos os registros por usuário e validar autorização no servidor em cada operação, não apenas na interface.
- Usar criptografia em trânsito e em repouso; a opção escolhida é recuperação administrada pelo serviço, não criptografia ponta a ponta com chave exclusiva do usuário.

### Rede e chamadas ao provedor

- Usar APIs HTTPS padrão do iOS com validação de certificado habilitada; não permitir HTTP claro nem ignorar erros de validação TLS.
- Enviar credenciais em mecanismos de autenticação próprios do protocolo, nunca em URLs ou logs.
- Não registrar prompt completo, e-mail, token, chave de API ou corpo de calendário em logs/telemetria.
- Informar claramente qual provedor recebe cada pedido e permitir desconectar/revogar a credencial.

### Calendário e ferramentas de IA

- Aplicar permissões por conta: principal para leitura e criação de blocos do app; adicionais somente leitura.
- Não permitir que chamadas do modelo alterem eventos preexistentes, trabalho ou prazos acadêmicos.
- Ferramentas disponíveis ao agente são allowlisted e recebem somente os dados necessários àquela ação.
- Registrar ações de replanejamento e apresentar diferenças ao usuário.

### Execução e isolamento

- Não há execução de código arbitrário na primeira versão; gVisor não é necessário para separar perfis de usuários.
- Manter isolamento multiusuário no modelo de dados, API, tokens e contexto do agente.
- Se forem adicionadas extensões ou execução de código não confiável, revisar sandbox, rede de saída, arquivos montados, limites de CPU/memória e credenciais temporárias.

## Riscos residuais reconhecidos

- O provedor de IA recebe os prompts enviados e aplica seus próprios termos, retenção e controles.
- O serviço de nuvem pode tecnicamente acessar dados da conta, apesar da criptografia em trânsito e em repouso.
- Um iPhone comprometido ou um app malicioso com acesso ao dispositivo pode expor dados disponíveis enquanto o app os usa.
- A transmissão TLS protege o canal contra interceptação comum, mas não elimina riscos no aparelho, no provedor, no endpoint ou nos metadados de rede.

## Referências de segurança para implementação

- Apple: [Keychain Services](https://developer.apple.com/documentation/security/keychain-services)
- Apple: [Preventing Insecure Network Connections](https://developer.apple.com/documentation/Security/preventing-insecure-network-connections)
- OWASP MASVS: [Network Communication](https://mas.owasp.org/MASVS/08-MASVS-NETWORK/) e [Cryptography](https://mas.owasp.org/MASVS/06-MASVS-CRYPTO/)
