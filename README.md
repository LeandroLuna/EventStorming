# EventStorming

O Event Storming é uma técnica especializada que se baseia na colaboração de diversas partes interessadas, como domain experts, arquitetos de software, desenvolvedores e outros envolvidos em um processo. Sua finalidade principal é aprimorar o entendimento conceitual de um sistema, especialmente em relação ao Domain Driven Design (DDD), que envolve a modelagem estratégica e tática de aplicações complexas.

Na modelagem estratégica do DDD, os profissionais buscam entender a aplicação em um nível mais amplo, identificando os contextos delimitados, como subdomínios principais, subdomínios genéricos, subdomínios auxiliares e camadas anti corrupção. Esta é a parte mais estratégica do DDD. Por outro lado, a modelagem tática do DDD envolve a implementação de padrões e técnicas específicas para construir o sistema. O Event Storming ajuda na parte estratégica, fornecendo clareza e profundidade ao entendimento do sistema.

A técnica do Event Storming é altamente colaborativa e requer a participação ativa de todos os envolvidos. Durante uma sessão de Event Storming, os participantes trabalham juntos para mapear eventos, ações e consequências que ocorrem no sistema. Isso não apenas melhora o entendimento geral do sistema, mas também pode ajudar na identificação de microsserviços, subsistemas, módulos (no caso de um sistema monolítico) e eventos cruciais para arquiteturas baseadas em eventos (event-driven architectures).

## Fundamentos do Event Storming

O Event Storming é normalmente realizado em formato de workshop, promovendo a interação entre desenvolvedores e domain experts. Isso ajuda a superar desafios comuns em projetos complexos, onde múltiplos domain experts podem não ter um entendimento claro de todos os processos. Às vezes, surgem zonas cinzentas onde os processos se sobrepõem, e a técnica ajuda a esclarecer essas áreas.

A técnica é dinâmica e divertida, com o uso de post-its e cores para representar diferentes aspectos do domínio. Isso é feito em uma lousa ou parede grande, idealmente em uma sala onde todos possam contribuir, discutir e colaborar. O Event Storming ajuda a mapear eventos, ações e consequências, identificando contextos e uma linguagem ubíqua para a aplicação.

Embora o Event Storming possa ser feito virtualmente, a ideia é que seja uma atividade presencial para facilitar a interação. O livro de Alberto Brandolini, que criou a técnica, oferece uma orientação detalhada sobre como conduzir workshops de Event Storming e aborda casos especiais que podem surgir durante o processo.

## Eventos e comandos

Eventos e comandos são conceitos essenciais no contexto do Event Storming, uma técnica de mapeamento e compreensão de sistemas complexos.

- Eventos:

Eventos são eventos de domínio que representam resultados ou acontecimentos passados no sistema. Eles são relevantes para o sistema e capturam o que ocorreu. Exemplos de eventos incluem "produto criado," "compra realizada," ou "vídeo criado." Esses eventos são fundamentais para entender o histórico das operações que ocorreram no sistema. No contexto do Event Storming, eventos são geralmente representados por post-its ou marcações laranjas.

- Comandos:

Comandos são ações ou operações que desencadeiam eventos no sistema. Eles representam as ações que os usuários, sejam eles reais ou outros sistemas, realizam para interagir com o sistema em questão. Por exemplo, um comando pode ser "finalizar compra," "criar produto," ou "emitir nota fiscal." Os comandos são a causa dos eventos e representam as operações que o sistema realiza em resposta às ações dos usuários. Geralmente, comandos são associados a um ator ou agente que os executa, como um cliente, um administrador, um fornecedor, etc.

A relação entre eventos e comandos é fundamental no Event Storming. Eventos são gerados como resultado da execução de comandos. Ao mapear eventos e associá-los aos comandos que os desencadeiam, é possível entender o funcionamento do sistema e a sequência de ações que levam a resultados específicos. Isso é essencial para modelar o domínio de um sistema complexo de forma clara e compartilhada entre todos os envolvidos, incluindo domain experts, desenvolvedores e outros stakeholders.

### Exemplo de Event Storming

- Eventos:

Os eventos representam o que ocorreu no sistema e são eventos de domínio, que capturam resultados passados. Eles são representados por post-its laranjas.

Exemplos de eventos incluem "vídeo criado," "categoria criada," "assinatura aprovada," e assim por diante. Cada um desses eventos representa um resultado ou acontecimento passado no sistema.

- Comandos:

Os comandos são ações ou operações que desencadeiam eventos no sistema. Eles são representados por post-its azuis.

Cada comando é a causa de um evento específico e representa as ações que os atores (ou agentes) executam para interagir com o sistema.

- Atores:

Os atores são as pessoas ou agentes que executam os comandos. Eles são representados por post-its amarelos.

No contexto apresentado, existem três atores principais: o administrador de vídeos, o cliente e o administrador de assinaturas.

## Pontos de decisão e policies

**Pontos de Decisão:**
   - Os pontos de decisão representam momentos no sistema em que é necessário tomar uma decisão com base em dados disponíveis.
   - Os dados podem ser provenientes de várias fontes, como bancos de dados, filas, APIs ou outras fontes de informação. O Event Storming não se preocupa com a origem exata dos dados nesse contexto, pois isso é considerado "complexidade acidental".
   - A ideia é focar na resolução de problemas no "coração do software", que é a complexidade de negócios, em vez de se aprofundar em detalhes de implementação de onde os dados são obtidos.
   - Um ponto de decisão é representado por um post-it verde e indica que em algum momento do fluxo do sistema, uma decisão precisa ser tomada com base nos dados disponíveis.

**Policies (Políticas):**
   - As políticas, ou policies, são regras ou diretrizes que determinam ações a serem tomadas em resposta a eventos específicos no sistema.
   - Uma política define um comportamento automático ou manual com base em gatilhos. Por exemplo, "Quando um vídeo é criado, envie um e-mail."
   - As políticas são representadas por post-its roxos ou de cor clara, e frequentemente usam a palavra-chave "whenever" (sempre que) para indicar o gatilho.
   - Essas políticas podem ser automatizadas, onde a ação é realizada automaticamente pelo sistema, ou podem envolver intervenção manual do usuário final.
   - O objetivo das políticas é definir como o sistema reage a eventos específicos, facilitando a automação de tarefas e garantindo consistência no sistema.

### Exemplo de police

- **Cenário Inicial:**
   1. O cliente inicia o processo de assinatura no sistema.

- **Fluxo de Eventos:**
   2. Quando o cliente inicia a assinatura, os dados de pagamento são enviados para uma gateway de pagamento.
   3. A gateway de pagamento pode aprovar ou rejeitar o pagamento com base em critérios internos, como informações do cartão de crédito, saldo disponível, entre outros.
   4. Se o pagamento é aprovado, a gateway gera um evento chamado "Pagamento Realizado" ou "Pagamento Aprovado".
   5. Com base no resultado do pagamento, o sistema pode tomar ações diferentes:
      - Se o pagamento é aprovado, o sistema pode avançar com a confirmação da assinatura, marcando-a como "Assinatura Confirmada" ou "Aprovada".
      - Se o pagamento é rejeitado, o sistema pode realizar ações diferentes, como notificar o cliente sobre a rejeição do pagamento ou aguardar uma nova tentativa de pagamento.

- **Policy (Política):**
   - A política nesse cenário está relacionada à decisão de como o sistema deve responder com base no evento "Pagamento Realizado" ou "Pagamento Aprovado".
   - A policy pode definir que, quando um "Pagamento Aprovado" é recebido, a assinatura é confirmada, permitindo ao cliente acessar o serviço.
   - Essa política automatiza o processo de confirmação da assinatura quando o pagamento é bem-sucedido, tornando-o transparente para o cliente.

Portanto, essa policy específica lida com a aprovação de pagamentos e como isso afeta o status da assinatura do cliente, mostrando como políticas podem ser usadas para automatizar ações com base em eventos específicos no sistema.

## Cronologia

A "cronologia" refere-se à organização e visualização dos eventos em uma ordem sequencial ou linha do tempo. Essa técnica ajuda a compreender como os eventos ocorrem em relação uns aos outros e como estão interconectados no sistema. A cronologia é uma representação gráfica ou uma abordagem de modelagem que ajuda a criar uma visão clara do fluxo de eventos em um domínio de negócios.

Neste contexto, a cronologia é usada para:

- **Sequenciar Eventos:** Colocar os eventos na ordem em que ocorrem, permitindo que os envolvidos no projeto visualizem a sequência lógica dos eventos no sistema.

- **Identificar Paralelismo:** Mostrar quais eventos ocorrem em paralelo, ou seja, ao mesmo tempo, para que os stakeholders possam entender as relações entre eventos simultâneos.

- **Demonstrar Fluxos de Trabalho:** Mostrar como os eventos e processos interagem e desencadeiam uns aos outros, permitindo uma compreensão mais profunda do funcionamento do sistema.

- **Facilitar a Comunicação:** Tornar a comunicação mais eficaz entre os membros da equipe, garantindo que todos usem a mesma linguagem e compreendam a ordem de execução dos eventos.

A organização em uma cronologia ajuda a evitar ambiguidades e confusões, facilitando o desenvolvimento de sistemas e a colaboração entre equipes técnicas e especialistas em domínio. Ela é uma técnica útil no contexto de Domain-Driven Design e Event Storming, como demonstrado no texto, para representar visualmente o fluxo de eventos no sistema.

## Origem dos eventos

- **Eventos Originados por Ações de Clientes:** Eventos podem surgir a partir de ações realizadas por clientes. Por exemplo, quando um cliente realiza uma ação, como comprar um produto ou criar uma conta em um sistema, essa ação gera eventos de domínio. Esses eventos representam as consequências das ações tomadas pelos usuários finais.

- **Eventos Originados por Sistemas Externos:** Eventos também podem ser gerados por sistemas externos. Por exemplo, quando um sistema externo, como um gateway de pagamento, interage com o sistema em questão, ele pode gerar eventos, como "compra aprovada" ou "compra rejeitada". Esses eventos são consequências das interações com sistemas externos e podem desencadear ações no sistema em foco.

- **Eventos Originados no Tempo:** Alguns eventos são gerados com base em horários específicos ou agendamentos. Por exemplo, em uma plataforma de e-mail marketing, um evento de envio de e-mail pode ser programado para ocorrer em um momento futuro, como amanhã às 08h00. Esses eventos são temporizados e ocorrem sem a necessidade de intervenção direta dos usuários.

- **Eventos Originados por Policies:** Eventos também podem ser originados por meio de políticas (ou políticas de domínio). Uma política pode ser acionada por uma ação e executar uma série de ações ou verificações complexas, o que resulta na geração de eventos adicionais. Por exemplo, ao iniciar uma assinatura, uma política pode ser acionada para processar o pagamento em uma gateway externa, o que pode levar à geração de eventos relacionados ao pagamento.

Essas diferentes origens de eventos mostram que os eventos de domínio não são limitados apenas às ações diretas dos usuários finais, mas também podem ser acionados por interações com sistemas externos, programações de tempo e execuções de políticas complexas.

## Formação dos agregados

Principais pontos relacionados à formação dos agregados:

- **Regras de Negócio e Enterprise Business Rules:** Agregados representam conjuntos lógicos de entidades e objetos de valor que contêm as regras de negócio e as "enterprise business rules" relacionadas a um domínio específico. Essas regras de negócio são essenciais para garantir a consistência e a integridade dos dados e processos no sistema.

- **Comandos e Eventos de Domínio:** Agregados estão no centro da interação entre comandos e eventos de domínio. Comandos representam ações que os usuários ou sistemas desejam realizar no domínio, enquanto eventos de domínio representam as consequências dessas ações. Os agregados são os responsáveis por aplicar as regras de negócio relacionadas a essas ações e gerar os eventos de domínio resultantes.

- **Identificação de Agregados:** A identificação de agregados é uma parte crítica do processo de design. Os desenvolvedores precisam determinar quais objetos, entidades e objetos de valor devem ser agrupados em agregados com base nas regras de negócio e nas interações entre eles. Cada agregado é tratado como uma unidade coesa que pode ser modificada em uma única transação.

- **Contextos Delimitados:** Agregados estão muitas vezes associados a contextos delimitados. Um contexto delimitado é uma parte específica do domínio onde regras e modelos específicos se aplicam. Agregados ajudam a definir limites claros para esses contextos e a garantir que as regras de negócio sejam aplicadas consistentemente dentro desses limites.

- **Clareza na Comunicação:** Ao identificar agregados, a equipe de desenvolvimento pode estabelecer uma terminologia compartilhada e uma compreensão clara das unidades lógicas do domínio. Isso ajuda a melhorar a comunicação entre desenvolvedores e especialistas do domínio, garantindo que todos estejam na mesma página em relação às regras de negócio.

- **Desenvolvimento e Manutenção Eficientes:** A clareza na identificação de agregados facilita o desenvolvimento e a manutenção de sistemas, uma vez que as regras de negócio relacionadas a um agregado específico são centralizadas. Isso reduz a complexidade e permite que as equipes de desenvolvimento trabalhem de forma mais eficiente.

## Contextos delimitados

No contexto do Event Storming, a definição de contextos delimitados é fundamental para criar uma compreensão clara das áreas distintas dentro de um domínio de negócios. Aqui estão os principais pontos relacionados à definição de contextos delimitados:

- **Zonas Cinzentas:** Zonas cinzentas referem-se a áreas do domínio onde as fronteiras e a responsabilidade não são imediatamente claras. Essas zonas geralmente surgem quando eventos ou conceitos podem ser interpretados de maneiras diferentes por diferentes especialistas de domínio. Resolver essas zonas cinzentas é essencial para evitar futuros conflitos e ambiguidades no design do sistema.

- **Eventos Pivô:** Eventos pivô são eventos-chave que ajudam a delimitar contextos. Eles representam pontos de transição ou interfaces entre diferentes áreas do domínio. Um evento pivô pode ser usado para marcar a fronteira entre um contexto e outro.

- **Delimitação de Contextos:** A delimitação de contextos envolve a identificação de áreas distintas no domínio, onde diferentes regras de negócios e modelos se aplicam. Essa delimitação é feita com base em eventos pivô e em discussões com os especialistas do domínio. É comum que os contextos delimitados correspondam a departamentos ou áreas funcionais de uma organização.

- **Bounded Contexts (Contextos Delimitados):** No contexto do Domain-Driven Design (DDD), os contextos delimitados são frequentemente referidos como "bounded contexts". Um bounded context é uma área claramente definida dentro de um domínio de negócios, onde um conjunto específico de modelos, regras de negócios e terminologia se aplica. Os bounded contexts ajudam a evitar conflitos semânticos entre diferentes partes do sistema.

- **Divergências e Oportunidades:** Quando ocorrem divergências entre especialistas de domínio em relação a como interpretar eventos ou regras, essas divergências podem ser marcadas como "hot spots" ou pontos quentes. Eventualmente, essas divergências podem ser resolvidas por meio de discussões e revisões. Da mesma forma, oportunidades para melhorias ou novos recursos podem ser identificadas e documentadas.

- **Post-its para Sinalizar:** Durante o processo de Event Storming, post-its são frequentemente usados para sinalizar eventos pivô, divergências, pontos de oportunidade e áreas de ambiguidade. Eles ajudam a criar uma representação visual do domínio que pode ser usada como base para o design de software.

A definição de contextos delimitados é uma etapa crítica no Event Storming, pois ajuda a criar uma compreensão compartilhada do domínio de negócios e permite que a equipe de desenvolvimento e os especialistas do domínio colaborem de forma eficaz. A identificação clara de fronteiras entre contextos ajuda a evitar conflitos e ambiguidades durante o desenvolvimento do sistema e contribui para a construção de um software que reflete com precisão as necessidades do negócio.

## Arrow voting

O "Arrow Voting" é uma técnica usada no Event Storming para resolver impasses ou conflitos entre especialistas de domínio quando não há um consenso sobre como interpretar eventos ou regras. A ideia por trás do Arrow Voting é permitir que as partes envolvidas votem em uma decisão quando há divergências.

- **Impasses e Conflitos:** Às vezes, durante um workshop de Event Storming, os participantes, que podem incluir especialistas de domínio, podem chegar a um impasse ou conflito. Isso ocorre quando não há acordo sobre como um evento ou conceito específico deve ser interpretado ou tratado no domínio de negócios.

- **Uso do Arrow Voting:** Quando ocorre um impasse e não é possível chegar a um consenso, o facilitador ou a equipe pode optar por usar o Arrow Voting como uma técnica de resolução. É importante notar que o Arrow Voting é uma abordagem para tomar decisões quando o consenso não pode ser alcançado de outra forma.

- **Mecânica do Arrow Voting:** Para usar o Arrow Voting, normalmente post-its azuis, menores e com setas, são colocados junto aos eventos em questão. Cada seta pode representar um voto. Isso significa que os participantes votam nas opções em disputa, expressando suas preferências.

- **Maioria Vence:** Após a votação, a decisão é tomada com base na maioria dos votos. Por exemplo, se três especialistas de domínio estiverem em desacordo, a opção com mais votos prevalece. O post-it correspondente é removido, indicando que a decisão foi tomada.

- **Cuidado na Condução:** A condução do Arrow Voting deve ser feita com sensibilidade, já que as decisões podem não ser unânimes. É importante evitar criar um ambiente de confronto e assegurar que todos os participantes se sintam ouvidos e respeitados. Um facilitador habilidoso pode desempenhar um papel crucial na condução do processo.

- **Mudança de Decisão Futura:** É importante ressaltar que uma decisão tomada por votação não é necessariamente permanente. Em um contexto de desenvolvimento ágil, as decisões podem ser revisadas à medida que mais informações se tornam disponíveis ou à medida que o projeto progride. Portanto, os participantes que não conseguiram vencer em uma votação podem ver suas opiniões prevalecerem em um momento posterior.

## Agregados e bounded contexts

- **Agregados:** No contexto do Event Storming, os agregados representam grupos de entidades ou objetos de valor que possuem regras de negócio e validações para garantir a consistência no domínio de negócios. Eles servem como unidades lógicas que encapsulam a lógica de negócios relacionada a um conjunto específico de entidades ou objetos. Por exemplo, um "agregado de vídeo" pode incluir regras relacionadas à criação, publicação e upload de vídeos. Da mesma forma, um "agregado de categoria" teria regras relacionadas à criação e gerenciamento de categorias. Os agregados ajudam a organizar o domínio de negócios em unidades gerenciáveis, tornando mais claro qual conjunto de regras de negócio se aplica a um conjunto específico de entidades.

- **Bounded Contexts:** Bounded contexts são delimitações no domínio de negócios que definem os limites dentro dos quais um conjunto específico de conceitos e regras se aplica. Isso significa que diferentes partes de um sistema podem ter contextos delimitados diferentes, cada um com sua própria linguagem ubíqua (vocabulário específico do domínio) e regras de negócio. Um bounded context pode representar uma área funcional ou uma divisão dentro de um sistema onde determinadas regras, terminologia e lógica são aplicadas. Por exemplo, um bounded context "Administração de Vídeo" pode abranger os agregados e eventos relacionados ao gerenciamento de vídeos, enquanto um bounded context separado "Assinaturas" pode abranger os agregados e eventos relacionados às regras de negócio de assinaturas.

## Contextos e microsserviços

Principais considerações e passos para delimitar contextos e microsserviços:

- **Identificando Bounded Contexts:** A primeira etapa é identificar os bounded contexts em seu domínio de negócios. Esses bounded contexts representam limites claros dentro dos quais conjuntos específicos de conceitos e regras de negócios são aplicados. Exemplos de bounded contexts incluem "Catálogo de Vídeos", "Sistema de Gestão de Assinaturas e Planos" e "Administração de Vídeos". Cada um deles descreve uma área distinta de regras de negócios.

- **Classificando os Bounded Contexts:** 
   - "Domínio/subdomínio": É um contexto principal e central que lida com a essência do negócio, como o "Catálogo de Vídeos". É de extrema importância.
   - "Subdomínio principal": Contextos que são essenciais para o domínio principal, como "Administração de Vídeos". Eles são críticos, mas servem para apoiar o domínio principal.
   - "Subdomínio auxiliar": Contextos que existem para atender às necessidades do domínio principal, como "Sistema de Gestão de Assinaturas e Planos". Eles são importantes, mas não essenciais.
   - "Subdomínio genérico": Contextos que são genéricos e podem ser facilmente trocados ou substituídos, como uma "Gateway de Pagamento". São contextos mais flexíveis.

- **Camada Anti-Corrupção:** é válido implementar uma camada anti-corrupção entre os microsserviços e gateways de pagamento. Essa camada atua como uma abstração que traduz as informações e solicitações entre os microsserviços internos e as gateways de pagamento, permitindo a fácil substituição de gateways sem afetar o sistema interno.

- **Identificando Microsserviços Potenciais:** Ao mapear os bounded contexts e suas interações, você pode começar a identificar microsserviços potenciais. A granularidade dos microsserviços não é definida inicialmente; em vez disso, você pode sentir a necessidade de dividir microsserviços à medida que partes do sistema se tornam complexas. O autor sugere que a criação de microsserviços seja uma evolução orgânica à medida que você aprofunda sua compreensão do domínio.

- **Benefícios do Mapeamento:** O mapeamento de eventos e a identificação de bounded contexts fornecem um ponto de partida claro para o design e a arquitetura de microsserviços. Isso ajuda a compreender a estrutura do sistema, a relação entre os componentes e a definição dos limites dos contextos, facilitando a criação de microsserviços que são bem definidos e coesos.

### Exemplo de Event Storming na prática

[Exemplo Codeflix](https://whimsical.com/event-storming-LR9ex19rzbFaq4o2yEo9DQ).