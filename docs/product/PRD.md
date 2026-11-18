# PRD — App Routine

**Status:** rascunho para revisão do usuário
**Plataforma inicial:** iOS, com React Native
**Distribuição:** fora da App Store; o método de instalação ainda será definido

## 1. Visão do produto

O App Routine ajuda uma pessoa a planejar o dia, a semana, o mês e o ano em relação às suas metas de vida. A IA usa o contexto e os recursos que a pessoa já possui para dividir tarefas, estimar o esforço, distribuir prioridades e adaptar o plano ao que realmente aconteceu.

O produto deve reduzir o problema de criar um plano semanal irrealista, não saber como começar tarefas grandes e perder a motivação quando imprevistos consomem o tempo disponível. A IA é uma assistente configurável e sujeita a limites; o planejamento manual deve continuar disponível.

## 2. Princípios

1. **A agenda deve caber na vida real.** Considerar tempo disponível, compromissos fixos, margem para imprevistos e descanso.
2. **Metas de longo prazo devem orientar ações próximas.** Conectar ações diárias e semanais a objetivos mensais, anuais e de vida, sem obrigar toda tarefa a ter uma meta.
3. **A pessoa mantém controle.** O plano inicial é revisado antes de ser gravado. Mudanças automáticas durante a semana são registradas e comunicadas; sugestões para datas futuras precisam de revisão.
4. **Dados observados e interpretações ficam distintos.** A IA não altera registros para sustentar uma leitura; apresenta padrões como hipóteses acompanhadas pelos dados que as motivaram.
5. **As recomendações devem usar recursos existentes.** Mapas de estudo, cursos e objetivos já definidos são fontes; a IA pode complementar com sugestões claramente identificadas.
6. **Sem provedor de IA, há uso manual.** Fluxos que exigem IA ficam bloqueados, mas as funções que não dependem de rede ou IA continuam disponíveis.

## 3. Usuários e contas

- O primeiro usuário é o criador do produto; a estrutura deve permitir contas separadas para outras pessoas desde o início.
- Login somente com Conta Google.
- Uma conta Google principal autentica o usuário e pode receber blocos de tarefas criados pelo app.
- Outras contas Google são fontes de consulta; o app não cria nem altera eventos nelas.
- A experiência inicial é para um dispositivo por usuário. Portabilidade entre dispositivos fica para uma etapa futura.
- A primeira configuração é uma conversa guiada. A conexão ao Calendário Google acontece depois.

## 4. Fluxos principais

### 4.1 Configurar perfil e objetivos

1. O usuário descreve objetivos, rotina, compromissos recorrentes, estudos e restrições em conversa guiada.
2. A IA pergunta o que for essencial e ajuda a transformar metas de vida em marcos e sinais concretos de progresso.
3. A pessoa revisa os marcos propostos antes de salvá-los.
4. O perfil deve poder registrar atividades que a pessoa parou e pretende retomar, sem assumir que ainda são recorrentes.
5. Dados de alto risco de identificação, como CPF, não fazem parte do perfil.

### 4.2 Planejamento semanal

1. No planejamento de domingo, o usuário pode informar tarefas e objetivos por texto ou voz.
2. A IA faz perguntas essenciais, quebra tarefas grandes em passos menores e estima duração, prazo, impacto de curto e longo prazo, energia e efeito no bem-estar.
3. Quando faltar contexto, a IA pergunta. As estimativas ficam visíveis para correção e as correções melhoram estimativas futuras para tarefas semelhantes.
4. O plano é distribuído por dia, com prioridades e blocos flexíveis, em vez de preencher cada horário com uma grade rígida.
5. A IA estima uma margem para imprevistos e descanso. O usuário pode registrar restrições específicas, como tempo de locomoção.
6. A IA considera compromissos e dados do calendário, mas não altera eventos que já existiam.
7. O usuário revisa e ajusta a proposta antes de gravá-la na agenda.

### 4.3 Reorganização durante a semana

- A IA pode reorganizar tarefas gerenciadas pelo app quando o app está aberto, por exemplo, após a pessoa informar que seu tempo mudou.
- Um job diário pode consultar o Google Calendar com o app fechado e preparar uma proposta apenas quando eventos novos, alterados ou removidos afetarem tarefas planejadas ou disponibilidade. O job não aplica mudanças; o usuário revisa e aprova propostas.
- Uma reorganização automática gera um único aviso dentro do app e um registro detalhado do que mudou.
- Compromissos existentes de trabalho e datas de entrega acadêmicas são âncoras: a IA não os move nem altera.
- Quando uma tarefa não couber na semana, a IA sugere uma data futura; essa sugestão só entra na agenda após revisão.
- Se um prazo fixo estiver em risco, a IA explica o conflito e sugere alternativas, como mover tarefas flexíveis, reduzir escopo ou pedir extensão. A pessoa decide.

### 4.4 Tarefas parciais e estimativas

- Cada tarefa pode ser marcada como **concluída**, **parcialmente concluída** ou **não concluída**.
- O cronômetro é manual, iniciado e pausado pelo usuário.
- Para uma tarefa parcial, a pessoa descreve em poucas palavras o que concluiu. A IA usa essa informação e o tempo registrado para estimar o que falta antes de redistribuir a tarefa.
- A IA pergunta diretamente por que tarefas não foram concluídas. Se a pessoa não souber, sugere uma causa para confirmação.
- O histórico de duração real e correções de estimativa ajuda a personalizar tarefas semelhantes.

### 4.5 Objetivos, fontes e prática

- A hierarquia de acompanhamento inclui metas de vida, anuais, mensais, semanais e diárias.
- Tarefas podem estar associadas a uma meta/área ou permanecer independentes, como trabalho, consulta médica e demandas administrativas.
- A IA pode sugerir uma relação com meta ou área quando houver conexão clara; quando houver dúvida, pede confirmação.
- Conectores selecionados pelo app podem fornecer mapas de carreira e materiais de estudo. A IA transforma etapas e materiais existentes em tarefas e identifica a fonte.
- Para tópicos teóricos, a IA pode sugerir projetos pequenos de prática com um entregável verificável. Projetos maiores são tarefas separadas.
- Frequências e recomendações educacionais podem mostrar fontes sem exigir explicações extensas.
- Conectores MCP personalizados ficam fora da primeira etapa; a prioridade inicial é usar conectores controlados pelo app e com permissões de leitura.

### 4.6 Revisões, painéis e indicadores

- **Semanal:** verificar tarefas concluídas, parciais ou não realizadas; perguntar diretamente pelos motivos; usar as respostas para ajustar planos futuros.
- **Mensal:** combinar indicadores numéricos com padrões observados e sugestões de ajuste.
- **Painel diário:** mostrar tarefas, tempo de estudo, progresso por marcos, ações por áreas da vida e descanso preservado, além de como as ações do dia contribuem para metas da semana, mês e ano.
- O progresso de metas longas é medido principalmente por marcos concretos, como módulos concluídos e projetos entregues. Horas e tarefas são contexto complementar.
- Gráficos de barras servem para comparar planejado e realizado. O radar tem áreas da vida como eixos e compara ações planejadas e realizadas por área; quantidade de metas aparece como contexto, não como medida de esforço.
- Compromissos importados do Calendário Google também contam como ações. A IA pode sugerir sua área e pedir confirmação quando não tiver certeza.
- Interpretações da IA são apresentadas como hipóteses, com os dados que as sustentam, e a IA pergunta se a leitura corresponde à experiência do usuário. Os registros originais permanecem intactos.

## 5. Prioridades e regras de domínio conhecidas

- Inglês: objetivo mínimo de cinco sessões por semana, por necessidade diária no trabalho.
- Carreira: estudo, investimentos e projetos podem receber peso por contribuírem para o objetivo de se tornar arquiteto de soluções.
- Saúde física, relacionamento, descanso e outras áreas são importantes; sua frequência deve ser flexível e ajustada à disponibilidade e a recomendações com fontes.
- Compromissos de trabalho devem respeitar estritamente a agenda da chefia.
- Prazos de entregas da faculdade/pós-graduação são fixos e não podem ser deslocados.
- A IA estima atributos de tarefa, mas o usuário pode aceitar, corrigir ou rejeitar inferências.

## 6. Integrações e fases

### Núcleo inicial do produto

- Login Google e perfil pessoal.
- Conversa guiada de configuração.
- Hierarquia de metas e planejamento dia/semana/mês/ano.
- Calendário Google para consultar eventos e criar somente blocos gerenciados pelo app na conta principal.
- Planejamento semanal com revisão antes de gravar.
- Fluxo manual sem IA, cronômetro, estados de tarefa e revisões/painéis conforme o escopo de implementação for detalhado.
- Uso de um provedor de IA escolhido e pago pelo próprio usuário; suportar chave de API ou login do provedor quando disponível e seguro.

### Depois do núcleo

- Gmail como fonte de tarefas e prazos. O conteúdo bruto deve ser processado no aparelho e nunca enviado ao provedor; só um resumo mínimo pode ser enviado à IA.
- Conectores para fontes da pós-graduação e do mapa de carreira.
- MCPs personalizados, após definir controles adicionais de segurança.
- Portabilidade para outros dispositivos.

## 7. Requisitos de IA e privacidade

- A IA funciona quando há provedor configurado e o app está aberto. Um job diário pode monitorar mudanças no Google Calendar e preparar propostas de reorganização, sem aplicá-las em segundo plano.
- A chave/token do provedor de IA fica no Keychain do iPhone e não é armazenado na nuvem do app nem em logs.
- Chamadas seguem diretamente do aparelho ao provedor escolhido, usando HTTPS/TLS e validação padrão de certificados do iOS.
- O provedor recebe o prompt e os dados que o app enviar; o app envia somente o contexto necessário aprovado pelo usuário.
- O conteúdo bruto de e-mail fica no dispositivo. Energia/bem-estar pode ser representado por indicador simples, como “energia baixa”, sem relatos livres de saúde mental.
- O usuário pode corrigir inferências da IA; o app deve aprender essas correções sem alterar o histórico original.

## 8. Requisitos offline

- Consulta e edição manual de tarefas e planos salvos, cronômetro e registro de progresso funcionam sem internet.
- Alterações manuais ficam no aparelho e sincronizam com a nuvem quando a conexão retorna.
- IA, autenticação/integrações Google e atualização de fontes externas exigem conexão.
- O primeiro escopo presume um dispositivo por usuário; conflitos de sincronização e portabilidade entre dispositivos ficam para definição futura.

## 9. Critérios de sucesso do produto

- O usuário consegue concluir o planejamento semanal sem precisar preencher uma grade rígida de horários.
- O plano respeita âncoras de trabalho e prazos acadêmicos e inclui margem realista.
- Tarefas grandes ficam acionáveis e tarefas parciais têm um caminho claro para continuar.
- As revisões explicam padrões de execução sem transformar inferências em fatos ou alterar os registros.
- Os painéis mostram avanço em marcos de longo prazo e distribuição das ações entre áreas de vida.
- O usuário consegue usar os recursos manuais sem configurar IA.

## 10. Questões em aberto

- Definir o método de instalação/distribuição fora da App Store.
- Escolher provedores de nuvem, banco de dados e estratégia de sincronização.
- Definir o primeiro provedor de IA e os métodos de autenticação realmente disponíveis para ele.
- Especificar o onboarding, campos do perfil, formato de marcos/KPIs e interação do cronômetro.
- Definir quais funções acima entram na primeira entrega técnica e a ordem dos conectores de carreira/estudo.
- Definir política de conflito de sincronização, exportação e exclusão de conta/dados.
