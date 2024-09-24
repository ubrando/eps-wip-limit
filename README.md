# Utilizando ZenHub para Calcular o WIP

## 1. Introdução

O Work In Progress (WIP), ou Trabalho em Progresso, é uma métrica que representa o número de tarefas que estão em andamento em um determinado momento em um projeto. A gestão do WIP é fundamental por várias razões:

- **Melhoria da Eficiência:** Controlar a quantidade de trabalho em progresso ajuda a evitar sobrecargas na equipe e a manter o foco nas tarefas que realmente precisam ser concluídas.
- **Identificação de Gargalos:** Um WIP elevado pode indicar a presença de gargalos no fluxo de trabalho, onde as tarefas se acumulam em um determinado estágio.
- **Aumento da Previsibilidade:** Ao monitorar o WIP, as equipes conseguem fazer previsões mais precisas sobre quando o trabalho será concluído.
- **Promoção do Foco:** Limitar o WIP incentiva a equipe a concluir tarefas antes de iniciar novas, melhorando a produtividade.

Gerenciar o WIP é uma prática comum em metodologias ágeis, como o Kanban, que estabelece limites claros para o número de tarefas que podem estar em andamento simultaneamente. Essa abordagem ajuda a otimizar o fluxo de trabalho e a melhorar a entrega de resultados.

## 2. Calculando Limites de WIP

Segundo o [Capítulo 2](https://engsoftmoderna.info/cap2.html) do livro [Engenharia de Software Moderna](https://engsoftmoderna.info/), os limites de WIP servem para evitar que as equipes fiquem sobrecarregadas com trabalho. Muitas vezes, tendemos a assumir muitas atividades, o que gera sobrecarga e diminui a qualidade das entregas. O Kanban reconhece esse problema e cria "travas", que são os limites de WIP, a fim de evitar a sobrecarga de trabalho.

Vamos supor o seguinte quadro Kanban:
  
![image](https://github.com/user-attachments/assets/165f72d1-4623-407d-b5e4-c40542e35f88)

Cada um dos Tn no quadro representa uma atividade a ser executada, enquanto as letras X, Y e Z correspondem aos limites de WIP que desejamos estabelecer.

Utilizaremos aqui o algoritmo proposto por Eric Brechner, um engenheiro da Microsoft, em seu livro sobre o uso de Kanban no desenvolvimento de software. O primeiro passo é estimar um tempo médio em que as tarefas devem ficar em cada passo do nosso quadro Kanban. Vamos supor, para este exemplo, os seguintes valores:

- LT(Especificação) = 2 dias
- LT(Em andamento) = 6 dias
- LT(Revisão) = 4 dias

Em seguida, devemos estimar o throughput (TP) do passo com maior lead time do nosso quadro Kanban. No cenário de desenvolvimento de software, sabemos que o passo que demanda mais tempo geralmente se encontra na implementação, ou seja, nas tarefas em andamento. Vamos supor que a equipe consiga suportar 9 tarefas por mês e que um mês tenha 21 dias úteis. Nesse caso, temos:

`TP = 9/21 = 0.42 tarefas/dia`

Por fim, o WIP de cada passo será calculado da seguinte forma:

**WIP(passo) = TP * LT(passo)**

Para nosso cenário de exemplo, temos:

- WIP(Especificação) = 0,42 × 2 = 0,84
- WIP(Em andamento) = 0,42 × 6 = 2,52
- WIP(Revisão) = 0,42 × 4 = 1,68

Arredondando para cima, os resultados finais ficam assim:

- WIP(Especificação) = 1
- WIP(Implementação) = 3
- WIP(Revisão) = 2

Como resultado, nosso quadro Kanban com os limites de WIP para cada passo será:
![Quadro Kanban](https://github.com/user-attachments/assets/58840bd1-4d62-49e7-ab79-57c6533c5f41)

## 3. ZenHub

Neste documento, iremos explorar como o ZenHub pode nos auxiliar no cálculo do WIP, utilizando ferramentas que nos ajudam a visualizar o cenário do projeto.

### 3.1 Board

Para começar a se familiarizar com o ZenHub, podemos iniciar com o Board dessa ferramenta.

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/0b4be0d1-58e0-4112-a2a0-cdb8ca2ab4fa" alt="Board" />
  <p><em>Board - sentinela-2024.1 <a href="https://app.zenhub.com/workspaces/sentinela-20241-6600879e9c18ff20971a451a/board">Ver Board</a></em></p>
</div>

Ao visualizar o Board, você verá uma coleção de pipelines que representam os estágios pelos quais o trabalho passa dentro da sua equipe. O Board é uma ferramenta fundamental para monitorar o Work In Progress (WIP), pois permite que as equipes visualizem quantas e quais tarefas estão em cada pipeline, facilitando a identificação de sobrecargas.  
Embora o Board apresente visualmente o status das tarefas, pode haver uma perda de panorama temporal durante o desenvolvimento. Por exemplo, não temos como saber quantas atividades estavam em desenvolvimento no mês passado. Isso pode ser crucial para análise e planejamento futuros.

#### 3.1.1 Funcionalidades do Board

O ZenHub oferece diversas funcionalidades que enriquecem a experiência de uso do Board. Recursos como filtros, etiquetas e priorização de tarefas ajudam na organização, permitindo que a equipe mantenha o foco nas atividades mais relevantes. Os filtros podem ser usados para visualizar apenas as tarefas de um determinado membro da equipe ou aquelas que pertencem a um projeto específico, enquanto as etiquetas ajudam a categorizar e identificar rapidamente o estado ou tipo de cada tarefa.

#### 3.1.2 Integração com Outras Métricas

Além disso, o Board pode ser integrado a outras métricas de desempenho, como lead time e throughput, proporcionando uma visão abrangente da eficiência do trabalho em equipe. Monitorar essas métricas em conjunto com o WIP permite que as equipes identifiquem áreas de melhoria, ajustem processos e aumentem a produtividade de maneira mais eficaz.

### 3.2 Cumulative Flow

Os diagramas de fluxo cumulativo acompanham o movimento das tarefas em cada pipeline da sua equipe dentro de cada Workspace do ZenHub. À medida que os problemas avançam pelo Board, você pode utilizar o diagrama para visualizar o rendimento. Essa visualização permite que as equipes monitorem não apenas o acúmulo de trabalho em cada pipeline durante um período específico, mas também identifiquem gargalos e áreas que podem ser aprimoradas no processo.

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/f7c2473c-c028-4d62-9921-e7a37e933123" alt="Cumulative Flow" />
  <p><em>Cumulative flow - sentinela-2024.1: <a href="https://app.zenhub.com/workspaces/sentinela-20241-6600879e9c18ff20971a451a/reports/cumulative?df=06-23-2024&dr=3m&dt=09-23-2024&labels[]=&notLabels[]=&p[]=Closed&r=">Ver relatório</a></em></p>
</div>

#### 3.2.1 Como utilizar:

O Cumulative Flow é preenchido automaticamente. Tudo o que você precisa fazer é mover o trabalho pelo Board. Ou seja, cada coluna do seu Board será espelhada para a construção do gráfico, permitindo que a equipe veja seu comportamento ao longo do tempo. Em períodos de inatividade, as linhas do gráfico tendem a permanecer planas.

![image](https://github.com/user-attachments/assets/c9968ca0-e9e4-4ea4-8d1c-433ee2204004)


#### 3.2.2 Como seria o Diagrama ideal?

Idealmente, os diagramas de fluxo cumulativo apresentam uma inclinação ascendente e para a direita, com faixas coloridas uniformes. Isso indica que, em todos os pipelines (exceto o pipeline de `Closed`), a mesma quantidade de problemas flui aproximadamente em cada estágio, de forma consistente. O pipeline de `Closed` deve aumentar progressivamente, o que significa que você está finalizando mais tarefas.

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/8c35b083-a743-43f2-8d2d-6b2cc4e94c25" alt="Cumulative Flow" />
  <p><em>Cumulative flow - 2024.1-MeasureSoftGram: <a href="https://app.zenhub.com/workspaces/20241-measuresoftgram-660b3c2cc830ad0f64db16b6/reports/cumulative?df=07-07-2024&dr=custom&dt=09-15-2024&labels[]=&notLabels[]=&p[]=Product%20Backlog&r=">Ver relatório</a></em></p>
</div>

#### 3.2.3 Limites WIP com Cumulative Flow

Com o panorama obtido pelo gráfico, podemos realizar análises para definir limites de WIP para cada pipeline. Essa ferramenta permite a seleção de um período de tempo para análise, facilitando, por exemplo, a identificação de quantas tarefas foram concluídas durante o mês ou a detecção de gargalos no desenvolvimento.

### 3.3 Control Chart

![image](https://github.com/user-attachments/assets/fdffe735-4a80-4012-96f1-3316a503f943)

O Control Chart (CCR) fornece informações sobre o tempo de ciclo e o tempo de espera, ou seja, quanto tempo os problemas levam do início ao fim. Não importa se sua equipe está usando estimativas ou não; este gráfico pode ajudar a prever a rapidez com que os próximos problemas serão fechados, além de identificar gargalos e eficiências em cada estágio do seu processo.

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/211f6840-3672-4952-a35d-aa04c30d673c" alt="Cumulative Flow" />
  <p><em>Exemplo de Control Chart - 2024.1-MeasureSoftGram: <a href="https://app.zenhub.com/workspaces/20241-measuresoftgram-660b3c2cc830ad0f64db16b6/reports/control?df=06-22-2024&dr=3m&dt=09-22-2024&ep=Z2lkOi8vcmFwdG9yL1BpcGVsaW5lLzA&labels[]=&notLabels=&prs=false&r=&sp=Z2lkOi8vcmFwdG9yL1BpcGVsaW5lLzMyODM4NDg&s=day">Ver relatório</a></em></p>
</div>

#### 3.3.1 Como o Control Chart pode ajudar a equipe?
- **Calcule seu tempo de ciclo e tempo de entrega**: Obtenha uma visão clara do tempo que as tarefas levam para serem concluídas.
- **Preveja o tempo médio de conclusão dos problemas**: Baseie-se em dados históricos para estimar prazos futuros.
- **Descubra bloqueadores e gargalos**: Identifique áreas específicas do seu processo que podem estar causando atrasos.
- **Identifique anormalidades — positivas e negativas**: Use essas informações para ajudar a melhorar o processo.

#### 3.3.2 Compreendendo o Control Chart:
- **Pontos no gráfico**: Cada ponto no gráfico representa uma issue fechada. Os pontos de cor sólida (preenchidos) representam um conjunto de issues fechadas no mesmo dia. Passar o cursor sobre um ponto fornece mais detalhes sobre as issues, como título e número de dias para o fechamento.
- **Eixos X e Y**:
  - O eixo X mostra a data em que a issue foi fechada.
  - O eixo Y sinaliza a quantidade de dias para o fechamento.
- **Média e média móvel**:
  - A linha azul mostra o número médio de dias que leva para fechar um problema durante todo o período de tempo selecionado.
  - A linha verde representa uma média móvel do número de dias para fechar as issues mais recentes, ajudando a identificar tendências ou mudanças recentes no seu processo.

Entender quanto tempo leva para fechar problemas e sua velocidade permite prever melhor a rapidez com que os próximos problemas serão concluídos.

- **Desvio Padrão**: A área sombreada em cinza, ou desvio padrão, ajuda a diferenciar entre essa variação “normal” e os outliers. Problemas dentro da área sombreada em cinza fazem parte da variação normal e previsível, mesmo que fiquem acima ou abaixo da média. Já os problemas fora da área cinza levaram um tempo anormalmente curto ou longo para serem fechados e devem ser examinados mais detalhadamente para entender por que isso ocorreu.

#### 3.3.3 Como seria o gráfico ideal?
- **Variância Limitada**: Quanto menor a área sombreada em cinza, mais estável é o seu processo. Esses problemas levam consistentemente o mesmo tempo para fechar, com poucos que são significativamente mais lentos ou mais rápidos. Menos variância significa que você pode prever seu rendimento (quão rápido os problemas são concluídos) com um grau maior de confiança.
- **Média Estável**: A linha da média móvel deve permanecer razoavelmente plana; uma inclinação acentuada significa que os problemas estão começando a levar mais tempo para fechar e pode ser evidência de um gargalo no processo. No entanto, como acontece com todas as mudanças no gráfico, use isso como uma oportunidade para iniciar uma conversa. Por exemplo, mudanças na média móvel podem indicar que os problemas estão demorando mais para fechar, mas também podem indicar que os problemas estão ficando mais complexos.

#### 3.3.4 Limites de WIP com Control Chart
Para obter as medidas Lead Time, Throughput e Work in Progress (WIP) usando o Control Chart no ZenHub, você pode seguir os seguintes passos:

- **Lead Time**: No ZenHub Control Chart, o Lead Time é calculado automaticamente para cada tarefa ou issue. Cada ponto no gráfico representa uma issue que foi concluída, e a distância no eixo X mostra o tempo total que levou para essa issue ser concluída (Lead Time). Você pode ver o Lead Time individual para cada item ao passar o cursor sobre os pontos no gráfico.

- **Throughput**: Embora o Control Chart no ZenHub não exiba diretamente o Throughput, você pode inferi-lo contando quantas issues foram concluídas dentro de um intervalo de tempo no gráfico. O eixo X do gráfico mostra o tempo, enquanto o eixo Y mostra as tarefas concluídas. Para calcular o Throughput, basta contar os pontos concluídos dentro de...

- **Cycle Time:** O Cycle Time também é uma métrica valiosa quando analisada em um Control Chart. O Cycle Time representa o tempo que uma tarefa leva para ser concluída após seu início. Ao monitorar o Cycle Time no gráfico, você pode identificar variações no desempenho e garantir que o processo esteja dentro dos limites aceitáveis. Cada ponto no gráfico representa o Cycle Time de uma tarefa específica, e as linhas de controle (superior e inferior) ajudam a determinar se o processo está estável. Quando os pontos ultrapassam os limites de controle, isso pode indicar problemas, como gargalos ou ineficiências no processo, que devem ser investigados.

## 4. Milestones de Release no ZenHub
A gestão eficaz de releases é fundamental para garantir a entrega contínua e organizada de funcionalidades e correções em um projeto de software. O ZenHub, integrado ao GitHub, oferece uma abordagem eficiente para planejar e monitorar o progresso de releases através da funcionalidade de milestones.

Os milestones permitem que equipes de desenvolvimento agrupem e organizem tarefas relacionadas a uma entrega específica, associando issues e pull requests a uma meta comum, como uma versão de software ou sprint. A integração com o GitHub facilita a criação de milestones, permitindo que as atividades do time sejam centralizadas e monitoradas de forma contínua.

No ZenHub, o acompanhamento de milestones é reforçado com ferramentas visuais, como o Release Report e o Roadmap, que oferecem uma visão clara do progresso de cada release. O Release Report exibe o andamento detalhado de cada milestone, destacando o número de tarefas concluídas em relação ao total planejado, enquanto o Roadmap fornece uma visão global dos milestones distribuídos ao longo do tempo, auxiliando na previsão de entregas e no gerenciamento de prazos.

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/682538b1-fd2d-4991-9fc6-3ffec57c5ed3" alt="Roadmap" />
  <p><em>Roadmap - 2024.1-MeasureSoftGram: <a href="https://app.zenhub.com/workspaces/20241-measuresoftgram-660b3c2cc830ad0f64db16b6/roadmap">Ver relatório</a></em></p>
</div>

Com essa integração, as equipes podem não apenas visualizar o progresso em tempo real, mas também adaptar e ajustar o escopo conforme necessário para garantir que os objetivos do projeto sejam alcançados com eficiência.

### 4.1 Como criar milestone de release e visualizar no ZenHub?
Para criar e acompanhar milestones de release no ZenHub, você pode usar os milestones do GitHub em conjunto com o ZenHub. O ZenHub integra os milestones do GitHub e permite acompanhar os releases de forma mais eficiente. Aqui estão os passos detalhados para criar e acompanhar os milestones no ZenHub:

**Criação de Milestones (Releases) no GitHub**  
Os milestones são criados diretamente no GitHub, e o ZenHub os sincroniza automaticamente.

**Como criar um milestone:**
1. Acesse o repositório onde deseja criar o milestone.
2. Vá para a aba Issues.
3. No menu lateral, clique em Milestones.
4. Clique no botão **New Milestone** no canto superior direito.
5. Defina os detalhes do milestone:
   - **Title**: Dê um nome ao seu milestone (por exemplo, "Release 1.0").
   - **Description**: Descreva o que esse release/milestone representa.
   - **Due Date**: Defina uma data de entrega ou conclusão para o milestone.
6. Após configurar o milestone, clique em **Create milestone**.

Depois de criar o milestone no GitHub, ele será visível no ZenHub e poderá ser vinculado a issues ou pull requests.

**Associar Issues e Pull Requests ao Milestone**  
Para organizar um release no ZenHub, você precisa associar issues ou pull requests ao milestone criado.

**Como associar issues a um milestone:**
1. No GitHub:
   - Acesse a issue ou pull request.
   - No lado direito da página, você verá uma seção chamada Milestone.
   - Clique em Milestone e selecione o milestone que deseja associar à issue/PR.
   - Salve as alterações.
2. No ZenHub:
   - Dentro do ZenHub Board, clique na issue desejada.
   - No painel da issue, localize a opção de Milestone (no mesmo painel que outras opções como Labels).
   - Selecione o milestone criado anteriormente no GitHub.

As issues e pull requests agora farão parte do milestone e serão automaticamente acompanhadas no ZenHub.

3. Acompanhar os Milestones no ZenHub:
- Uma vez que os milestones estejam configurados e com issues vinculadas, você pode acompanhar o progresso diretamente no ZenHub usando o Release Report.

  **Como visualizar e acompanhar milestones:**
  1. Acesse seu ZenHub Board.
  2. No topo da página, clique em **Reports**.
  3. Selecione o relatório de **Releases**.

![image](https://github.com/user-attachments/assets/c13026e3-3f3c-4401-87d9-5130ce462039)

  4. Na tela de Release Report, você verá uma lista de todos os milestones.
     - Cada milestone exibirá uma barra de progresso mostrando o número de issues ou pull requests concluídas em relação ao total.
     - O Release Report oferece uma visão detalhada do andamento do milestone, incluindo status de cada issue, tempo restante e outros detalhes.

Você também pode aplicar filtros para visualizar milestones relacionados a uma equipe, projeto ou repositório específico, e observar como cada milestone está avançando em relação à data limite (due date).

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/929b91ee-ac72-4770-aa86-68f246a021db" alt="Release Report" />
  <p><em>Release Report - 2024-1-GEROcuidado-Doc: <a href="https://app.zenhub.com/workspaces/2024-1-gerocuidado-doc-660827e5fa3f1738008c4f67/reports/release?release=Z2lkOi8vcmFwdG9yL1JlbGVhc2UvMTAzNTk5">Ver relatório</a></em></p>
</div>

## 5. Cálculo de Velocity no ZenHub e Como Monitorá-lo
Velocity (ou Velocidade) é uma métrica amplamente utilizada em metodologias ágeis para medir a produtividade de uma equipe em cada sprint ou ciclo de desenvolvimento. No ZenHub, o Velocity é calculado com base na quantidade de story points (ou pontos de história) concluídos pela equipe em um período de tempo específico, geralmente uma sprint ou semana. Essa métrica ajuda a prever o ritmo de trabalho da equipe e a planejar sprints futuras com mais precisão.

### 5.1 Como o ZenHub Calcula o Velocity
O cálculo de Velocity no ZenHub é feito da seguinte maneira:
- **Pontos de História**: As issues ou tarefas no ZenHub são associadas a pontos de história, que representam o esforço necessário para completar cada item. Esses pontos são definidos pela equipe de acordo com a complexidade da tarefa.
- **Sprint ou Ciclo de Tempo**: O ZenHub agrupa os pontos de história concluídos dentro de um período específico, como uma sprint. Cada sprint tem uma duração fixa (geralmente de 1 a 2 semanas).
- **Soma dos Pontos Concluídos**: No final de cada sprint, o ZenHub soma os pontos de história das issues que foram movidas para a coluna "Done" (ou equivalente) até o final da sprint. Issues que não forem concluídas até esse momento não são incluídas no cálculo da Velocity para aquela sprint.
- **Velocity Médio**: O ZenHub também calcula a Velocity média ao longo de várias sprints, o que ajuda a equipe a obter uma estimativa mais precisa da produtividade ao longo do tempo. O valor médio é útil para planejar sprints futuras, ajustando o número de tarefas para corresponder à capacidade da equipe.

### 5.2 Como Monitorar o Velocity no ZenHub
O ZenHub oferece ferramentas visuais para monitorar o Velocity diretamente no Velocity Report. Para acessar e monitorar a Velocity:
1. **Acessar o Velocity Report**:
   - No ZenHub Board, clique em **Reports** no menu superior.
   - Selecione **Velocity** no menu de relatórios.

![image](https://github.com/user-attachments/assets/006b4a4c-47b9-4fb2-8934-7be84e524021)


2. **Visualização do Relatório de Velocity**:
   - O Velocity Report mostra um gráfico de barras que representa os pontos de história concluídos em cada sprint. As barras são divididas em "Planned" (planejado) e "Completed" (concluído), permitindo uma comparação clara entre o que foi planejado e o que foi realmente entregue.
   - Cada barra representa uma sprint, e ao passar o cursor sobre elas, você pode ver os detalhes do número de pontos planejados e concluídos.

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/067747c8-9e62-4286-a8a1-75dc4fdbf93a" alt="Velocity Report" />
  <p><em>Velocity Report - 2024-1-GEROcuidado-Doc:<a href="https://app.zenhub.com/workspaces/20241-measuresoftgram-660b3c2cc830ad0f64db16b6/reports/velocity"> Ver relatório</a></em></p>
</div>

3. **Análise e Ajustes**:
   - Ao observar o relatório de Velocity ao longo de várias sprints, você pode identificar padrões de produtividade. Se a equipe está constantemente abaixo ou acima da meta de pontos planejados, é possível ajustar o planejamento para sprints futuras.
   - O Velocity médio também é exibido para facilitar a previsão de quanto trabalho pode ser assumido na próxima sprint, com base no desempenho passado.

### 5.3 Boas Práticas para Melhorar o Monitoramento de Velocity
- **Definição Clara de Pontos de História**: Certifique-se de que os pontos de história são atribuídos de forma consistente para cada issue. Isso garante que a estimativa de esforço seja precisa e que o cálculo da Velocity reflita a realidade da equipe.
- **Planejamento Realista de Sprints**: Ao planejar uma sprint, utilize o Velocity médio das sprints anteriores como referência para não sobrecarregar a equipe com mais tarefas do que ela pode concluir.
- **Concluir Issues Antes do Prazo Final**: Apenas as issues que estão na coluna "Done" no final da sprint são contadas para o cálculo da Velocity. Incentive a equipe a concluir tarefas antes da conclusão da sprint para melhorar a precisão da métrica.
- **Acompanhamento Regular do Velocity Report**: Utilize o Velocity Report como uma ferramenta de aprendizado contínuo, ajustando o planejamento conforme necessário.

## 6. Referências bibliográficas
  1. ZENHUB. Example cumulative flow diagrams to learn from. Disponível em: <https://help.zenhub.com/support/solutions/articles/43000469850-example-cumulative-flow-diagrams-to-learn-from>. Acesso em: 22 set. 2024.
  2. ZENHUB. Use control charts to review issue cycle & lead time. Disponível em: <https://help.zenhub.com/support/solutions/articles/43000300345-use-control-charts-to-review-issue-cycle-lead-time>. Acesso em: 22 set. 2024.
  3. ZENHUB. How throughput and cycle/lead time are read together. Disponível em: <https://help.zenhub.com/support/solutions/articles/43000479014-how-throughput-and-cycle-lead-time-are-read-together>. Acesso em: 22 set. 2024.
  4. ZENHUB. GitHub productivity insights. Disponível em: <https://help.zenhub.com/support/solutions/articles/43000700928-github-productivity-insights>. Acesso em: 22 set. 2024.


