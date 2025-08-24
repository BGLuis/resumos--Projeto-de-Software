# Microservices

O artigo introduz e define o estilo arquitetural de microsserviços, não como uma especificação rígida, mas como um conjunto de características comuns observadas em sistemas de software que emergiram como resposta a problemas práticos e recorrentes. Esta abordagem representa uma mudança fundamental na forma como as aplicações são concebidas e desenvolvidas, afastando-se do paradigma monolítico predominante.

## Definição

-   **Microsserviços**: O estilo arquitetural de microsserviços é uma abordagem para desenvolver uma única aplicação como um conjunto de pequenos serviços. Cada um desses serviços é executado em seu próprio processo e se comunica com os outros através de mecanismos leves, como uma API de recurso HTTP.

-   **Monólitos**: Uma aplicação monolítica é construída como uma única unidade lógica e executável. Composto geralmente por uma interface de usuário do lado do cliente, um banco de dados e uma aplicação do lado do servidor.

## Frustrações

A popularidade dos microsserviços foi acelerada pelas frustrações crescentes com a abordagem monolítica, Embora simples no início, os monólitos apresentam desafios significativos à medida que crescem, especialmente em ambientes de nuvem. As principais frustrações incluem:

-   **Ciclos de Mudança Acoplados**: Qualquer alteração, por menor que seja, exige a reconstrução e a implantação de toda a aplicação, tornando o processo lento e arriscado.

-   **Deterioração da Modularidade**: Com o tempo, é difícil manter uma estrutura modular clara, levando a um forte acoplamento entre os componentes.

-   **Escalabilidade Ineficiente**: A escalabilidade exige a replicação de toda a aplicação, mesmo que apenas uma pequena parte dela seja o gargalo de recursos.

## Trade-Offs

adotar microsserviços envolve uma análise cuidadosa de seus custos e benefícios, pois a abordagem troca um conjunto de problemas por outro.

-   **Limites de Módulo Fortes**: Os serviços impõem limites explícitos que ajudam a manter a modularidade ao longo do tempo.

-   **Implantação Independente**: A capacidade de implantar serviços individualmente acelera os ciclos de lançamento e reduz o risco.

-   **Diversidade Tecnológica**: Permite que as equipes escolham a melhor tecnologia para cada tarefa específica.

-   **Escalabilidade Granular**: Apenas os serviços que necessitam de mais recursos precisam ser escalados.

-   **Complexidade da Distribuição**: Sistemas distribuídos são inerentemente mais complexos. As chamadas remotas são mais lentas e menos confiáveis do que as chamadas locais.

-   **Consistência Eventual**: A ausência de transações distribuídas implica que a consistência entre serviços pode não ser imediata, exigindo que as equipes lidem com estados temporariamente inconsistentes.

-   **Complexidade Operacional**: Gerenciar, monitorar e depurar um ambiente com múltiplos serviços é significativamente mais desafiador do que administrar um único monólito.

-   **Dificuldade de Refatoração**: Alterar responsabilidades entre serviços é mais trabalhoso do que refatorar código dentro de uma aplicação monolítica.

## Conclusão

Os autores concluem com um otimismo cauteloso, afirmando que, embora suas experiências sejam positivas, ainda é cedo para declarar os microsserviços como a direção definitiva para a arquitetura de software. Eles alertam que o sucesso depende criticamente da competência da equipe, pois "uma equipe má criará sempre um sistema mau". Uma recomendação pragmática é a estratégia "Monolith First": começar com uma aplicação monolítica bem modular e dividi-la em microsserviços apenas quando a complexidade do monólito se tornar um problema real. Em última análise, a adoção de microsserviços é uma escolha estratégica que exige uma compreensão profunda de seus trade-offs e uma avaliação honesta da maturidade da equipe e da organização.

[Artigo](pdf/Microservices.pdf)
