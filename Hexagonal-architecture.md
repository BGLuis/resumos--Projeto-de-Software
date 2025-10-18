# Hexagonal architecture

No cerne da arquitetura de software, um desafio persistente tem sido a tendência da lógica de negócio a se infiltrar e se emaranhar com o código da interface do utilizador (UI). Alistair Cockburn, no seu artigo seminal de 2005, identifica este fenómeno como um dos "grandes papões" (bugaboos) das aplicações de software, um problema fundamental que gera consequências sistémicas profundas. A infiltração da lógica de negócio no código da UI cria um problema tripartido que compromete a testabilidade, a flexibilidade e a interoperabilidade do sistema. Primeiramente, a aplicação torna-se intratável para testes automatizados. Em segundo lugar, a transição de um sistema operado por humanos para um sistema executado em lote (batch) torna-se impraticável. Finalmente, a capacidade de a aplicação ser controlada por outro programa é severamente dificultada.

A solução convencional—introduzir uma nova camada na arquitetura—está condenada ao fracasso a longo prazo devido a uma falha crítica: a ausência de um "mecanismo para detetar quando ocorre uma violação". Um problema simétrico existe no lado da base de dados, onde o forte acoplamento interrompe o desenvolvimento sempre que o servidor fica indisponível. Cockburn percebe que ambos os problemas são manifestações do mesmo erro de design: o acoplamento entre a lógica de negócio e a interação com entidades externas.

## A Solução Proposta: Portas e Adaptadores

A arquitetura proposta emerge não apenas como um padrão estrutural, mas também como um mecanismo de diagnóstico e fiscalização. A premissa é que toda a funcionalidade da aplicação deve ser acessível através de uma API. Esta condição cria um ambiente onde testes de regressão automatizados podem ser executados diretamente contra o núcleo da aplicação, tornando-se o mecanismo de deteção de violações que faltava.

Para resolver o problema do emaranhado, a Arquitetura Hexagonal, também conhecida como Portas e Adaptadores, propõe uma mudança fundamental. O seu objetivo é "Permitir que uma aplicação seja igualmente controlada por utilizadores, programas, testes automatizados ou scripts em lote, e que seja desenvolvida e testada isoladamente dos seus dispositivos e bases de dados de tempo de execução". Em vez de se focar nas assimetrias tradicionais de cima-para-baixo, o padrão explora a assimetria fundamental "entre o interior e o exterior da aplicação". A regra de ouro é que "o código pertencente à parte interior não deve vazar para a parte exterior".

# Componentes Fundamentais

A arquitetura é composta por três elementos centrais: o núcleo da aplicação (o "interior"), as portas e os adaptadores.

### O Núcleo da Aplicação (Interior)

O núcleo da aplicação é onde reside a lógica de negócio. Este componente é o coração do sistema e deve ser mantido puro de quaisquer dependências tecnológicas externas, sendo "felizmente ignorante da natureza do dispositivo de entrada". Toda a sua funcionalidade é exposta através de uma ou mais APIs, e é contra esta fronteira que as especificações funcionais e os casos de uso devem ser escritos.

### Portas: Interfaces com Propósito

Uma porta define uma interface para uma "conversa com propósito" entre o núcleo da aplicação e o mundo exterior. A palavra "porta" é usada intencionalmente para evocar a natureza plug-and-play de sistemas operativos ou dispositivos eletrónicos. O protocolo de uma porta é formalizado pela sua API. Por exemplo, uma aplicação de comércio eletrónico pode ter uma porta para "Gestão de Encomendas", cuja API define operações como criarEncomenda e consultarEstado.

### Adaptadores: A Ponte Tecnológica

Se uma porta define o quê e o porquê de uma interação, o adaptador define o como. Para cada dispositivo ou tecnologia externa, existe um "adaptador que converte a definição da API [da porta] para os sinais necessários por esse dispositivo e vice-versa". Um adaptador é, essencialmente, um tradutor. Uma característica fundamental é que pode haver múltiplos adaptadores para uma única porta. Para a porta de "Gestão de Encomendas", poderiam existir um adaptador de GUI, um adaptador de teste e um adaptador de API REST. Da mesma forma, para uma port

## Nuances e Conceitos Avançados

### Atores Primários vs. Secundários

Embora o padrão enfatize a simetria, Cockburn introduz a distinção entre portas e adaptadores primários e secundários, também referidos como condutores (driving) e conduzidos (driven).

-   Um **ator primário** é aquele que "conduz a aplicação", como um utilizador numa GUI ou um script de teste. Ele inicia a conversa.

-   Um **ator secundário** é aquele que "a aplicação conduz", como uma base de dados da qual se obtêm respostas ou um serviço de e-mail que é notificado.

Esta distinção leva a um emparelhamento natural com tecnologias de teste: test harnesses (como FIT) são ideais para substituir atores primários, enquanto mocks são ideais para substituir atores secundários. A diferença pode ser resumida da seguinte forma:

-   **Portas/Adaptadores Primários (Condutores)**: Nestes, o ator externo inicia a conversa e conduz o comportamento da aplicação. Exemplos típicos incluem uma GUI, um test harness FIT ou um batch driver. A estratégia de teste correspondente utiliza test harnesses com scripts.

-   **Portas/Adaptadores Secundários (Conduzidos)**: Aqui, a aplicação inicia a conversa e conduz o ator externo, que fornece serviços ou recebe notificações. Exemplos incluem uma base de dados, um mock de base de dados ou um adaptador de e-mail. A estratégia de teste correspondente utiliza objetos mock que respondem a consultas da aplicação.

### Implicações para Casos de Uso

Cockburn adverte contra a prática de escrever casos de uso que contêm "conhecimento íntimo da tecnologia situada fora de cada porta". Em vez disso, os casos de uso devem ser escritos "na fronteira da aplicação (o hexágono interior), para especificar as funções e eventos suportados pela aplicação, independentemente da tecnologia externa". Isto torna os casos de uso mais curtos, estáveis e focados no valor de negócio.

# Conclusão

A Arquitetura Hexagonal oferece uma solução robusta para o acoplamento indesejado entre a lógica de negócio e as tecnologias externas, reorientando a perspetiva para um modelo de interior-exterior que trata todas as interações externas como simétricas e garante que o núcleo permaneça puro e agnóstico à tecnologia. Os benefícios sistémicos desta abordagem incluem uma testabilidade aprimorada, permitindo que a lógica de negócio seja validada de forma exaustiva e automatizada em completo isolamento; flexibilidade tecnológica, onde interfaces de utilizador e bases de dados podem ser trocadas com impacto mínimo; e a promoção de um desenvolvimento paralelo eficiente que reduz as dependências entre equipas. Em última análise, a disciplina imposta pela Arquitetura Hexagonal—separar o propósito (portas) do mecanismo (adaptadores)—capacita as equipas a construir sistemas que são resilientes à mudança tecnológica, mais fáceis de manter e mais adaptáveis às futuras necessidades do negócio.

[Artigo](pdf/Hexagonal-architecture.pdf)
