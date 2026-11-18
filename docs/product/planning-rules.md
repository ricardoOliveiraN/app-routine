# Regras do motor de planejamento

**Status:** regras de produto consolidadas em sessão de revisão; pendentes de validação final do usuário.

## Objetivo

O motor transforma metas, tarefas, compromissos, disponibilidade e informações autorizadas em uma proposta de rotina que caiba na vida real. A IA pode tomar decisões de planejamento com base no contexto permitido pelo usuário, mas o usuário mantém controle sobre o plano e sobre alterações futuras.

Este documento especifica comportamento. Não escolhe uma fórmula de pontuação nem uma implementação técnica.

## 1. Entradas e estimativas

Para cada tarefa, a IA pode estimar:

- prazo e urgência;
- duração e esforço;
- impacto imediato e de longo prazo;
- energia necessária;
- área da vida e relação com metas;
- decomposição em tarefas menores, quando útil.

As estimativas podem usar o perfil, o histórico de planejamento e execução, as correções anteriores e as fontes que o usuário autorizou, incluindo documentação e MCPs disponíveis. A IA deve considerar também compromissos fixos, prazos protegidos, disponibilidade informada, descanso e margem para imprevistos.

Quando faltar contexto ou houver incerteza relevante, a IA deve sinalizá-la e perguntar ao usuário. As estimativas e suas justificativas devem ficar visíveis na revisão do plano, para que o usuário possa corrigir antes de aprovar.

### Correções e divergências de fontes

- Correções do usuário sobre prioridade e tempo gasto prevalecem para o planejamento atual.
- Correções sobre conteúdo que contradigam uma fonte autorizada não substituem a fonte automaticamente. A IA apresenta a divergência e pergunta qual informação deve usar.
- Se duas fontes autorizadas divergirem sem uma correção explícita do usuário, a IA mostra o conflito e pergunta qual informação deve usar.
- Correções e tempos registrados podem melhorar estimativas futuras para tarefas semelhantes. O histórico original não deve ser reescrito para refletir uma interpretação posterior.

A incerteza deve ser indicada com rótulos simples de confiança (alta, média ou baixa) e o motivo correspondente.

## 2. Aprovação e controle do plano

- Toda proposta de plano deve ser revisada e aprovada pelo usuário antes de ser gravada.
- A aprovação pode ser do plano inteiro ou de tarefas individualmente.
- Para cada tarefa, o usuário pode aprovar, editar ou rejeitar a proposta.
- Se uma tarefa rejeitada tiver dependências, a IA revisa essas tarefas e propõe os ajustes necessários.
- A revisão mostra prioridades, justificativas e estimativas incertas.
- Mudanças sugeridas para datas futuras aguardam aprovação antes de serem aplicadas.

## 3. Prioridades, capacidade e descanso

A IA deve priorizar tarefas buscando a melhor rotina para o usuário, considerando contexto, metas, prazos, impacto, esforço e disponibilidade. Não se define uma fórmula de pontuação neste documento.

Compromissos fixos e prazos importantes de trabalho ou faculdade são âncoras protegidas: a IA planeja ao redor deles e não os move nem substitui. Se um prazo estiver em risco por competir com outras tarefas ou com descanso, a IA recomenda alternativas e explica o risco; a decisão final permanece com o usuário.

Quando a semana exceder a capacidade:

1. A IA prioriza as tarefas que melhor atendem ao contexto e às metas do usuário.
2. Propõe remanejar as tarefas que não couberem.
3. Pode perguntar se o usuário quer mudar a priorização antes de fechar o plano.
4. Se uma tarefa estiver perto do prazo e competir com descanso ou outra prioridade, explica o que recomenda adiar ou reduzir e qual é o risco.
5. Se uma tarefa for remanejada repetidamente, pergunta se o usuário quer mantê-la, dividi-la, reduzir seu escopo ou removê-la das prioridades.

O plano deve reservar tempo para descanso e imprevistos. A IA pode ajustar esse espaço conforme a semana e perguntar se vale a pena incluir descanso ou reorganizar a agenda para acomodá-lo. Não há uma quantidade mínima fixa definida; o ajuste depende do contexto e deve ser apresentado para revisão no plano.

## 4. Distribuição no calendário

O usuário escolhe nas configurações o dia da semana em que informará sua disponibilidade; pode mudar esse dia depois. A disponibilidade semanal é informada por períodos gerais, delimitados por horários em horas (por exemplo, manhã, das 9h às 12h).

O Google Calendar complementa essa informação e prevalece quando houver conflito. Horários vazios no calendário podem ser considerados disponíveis. A IA deve levar em conta o horário habitual de sono, cadastrado nas configurações, e permitir exceções para semanas específicas. Se não souber se um período é utilizável, deve perguntar quando essa informação for necessária ao plano.

- O plano combina tarefas distribuídas por dia sem horário específico com blocos de horário sugeridos quando forem úteis.
- Horários sugeridos são flexíveis e podem ser movidos durante o dia, preservando a prioridade da tarefa.
- A IA não deve preencher toda a disponibilidade com uma grade rígida.
- Compromissos existentes e âncoras protegidas permanecem intactos.

## 5. Mudanças de disponibilidade e reorganização

Um job diário pode consultar o Google Calendar mesmo com o app fechado. Ao encontrar evento novo, alterado ou removido, só prepara uma proposta se a mudança afetar tarefas planejadas ou a disponibilidade. Se não afetar o plano, não faz nada. O job não aplica alterações: propostas de reorganização, inclusive as que afetem datas futuras, aguardam revisão e aprovação do usuário.

A IA não executa reorganizações em segundo plano. Com o app aberto, se a disponibilidade mudar, pode reorganizar tarefas e blocos gerenciados pelo app, informa o que foi alterado e permite ao usuário restaurar o plano anterior.

## 6. Tarefas em andamento, parciais ou não concluídas

Quando uma tarefa exceder o tempo estimado, a IA pergunta quanto falta. Com a resposta, pode sugerir uma pausa ou recalcular o restante da semana, inclusive recomendando concluir a tarefa naquele momento quando isso parecer melhor.

Para uma tarefa encerrada sem conclusão, a IA pergunta o motivo antes de decidir como reorganizá-la. Essa resposta, junto com o tempo registrado e o progresso parcial, pode aperfeiçoar estimativas e perguntas em planejamentos futuros.

Se a causa ou o escopo restante não estiver claro, a IA pergunta em vez de inventar uma resposta como fato. Pode apresentar uma hipótese para o usuário confirmar.

## 7. Exemplos de comportamento

Os exemplos ilustram as regras; não determinam prioridades fixas nem uma fórmula.

### Semana com capacidade normal

Há compromissos de trabalho fixos, uma tarefa de estudo com prazo e tempo disponível em alguns dias. A IA preserva os compromissos, distribui o estudo em tarefas menores, combina um ou mais blocos flexíveis com tarefas sem horário e reserva espaço para descanso e imprevistos. Mostra estimativas e justificativas; o usuário revisa o plano inteiro ou tarefa por tarefa antes de gravar.

### Semana sobrecarregada

As tarefas excedem o tempo disponível antes de um prazo acadêmico. A IA mantém o prazo e os compromissos fixos, prioriza o trabalho relevante, propõe remanejar tarefas que não couberem e explica o risco das alternativas. Pode perguntar se o usuário quer mudar as prioridades. Se uma tarefa tiver sido adiada repetidamente, pergunta se deve mantê-la, dividi-la, reduzir o escopo ou removê-la das prioridades. A proposta passa por aprovação antes de ser gravada.

### Mudança inesperada de disponibilidade

Surge um imprevisto enquanto o app está aberto e reduz o tempo disponível. A IA pode reorganizar as tarefas gerenciadas pelo app, informa as alterações e oferece restaurar o plano anterior. Se a proposta deslocar tarefas para datas futuras, essas mudanças aguardam aprovação.

### Tarefa maior do que o estimado

O tempo previsto termina antes da conclusão. A IA pergunta quanto falta e, conforme a resposta, sugere uma pausa ou recalcula o restante da semana. Se a tarefa não for concluída, pergunta o motivo e usa a resposta e o tempo registrado para melhorar estimativas futuras.

## Critério de aceitação

Todos os comportamentos definidos neste documento são obrigatórios para considerar o planejador pronto para implementação. A validação deve cobrir o conjunto completo de regras, incluindo disponibilidade, proteção de âncoras, prioridades, incertezas, revisão/aprovação, reorganizações, descanso, tarefas parciais e dependências.

## 8. Questões ainda abertas

Nenhuma questão de comportamento pendente nesta etapa.

