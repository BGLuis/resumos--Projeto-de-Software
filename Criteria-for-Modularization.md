# On the Criteria To Be Used in Decomposing Systems into Modules

O artigo aborda a falta de critérios claros para a decomposição de sistemas em módulos. Embora a programação modular fosse promovida por seus benefícios esperados, como tempo de desenvolvimento reduzido, flexibilidade do produto e melhor compreensibilidade. Parnas argumenta que a eficácia da modularização depende inteiramente dos critérios utilizados para a divisão.

## Índice KWIC

Para ilustrar sua tese, o artigo apresenta um sistema de índice KWIC (Key Word in Context) e propõe duas decomposições modulares distintas para ele.

### A Abordagem baseada em Fluxograma

-   **Critério**: Fazer de cada passo em um fluxograma de processamento um módulo separado.
-   **Módulos**:

    -   **Input**:Lê os dados e os armazena.
    -   **Circular Shift**: Cria um índice de todos os deslocamentos circulares.
    -   **Alphabetizing**: Ordena alfabeticamente o índice de deslocamentos.
    -   **Output**: Gera a listagem formatada.
    -   **Master Control**:Controla a sequência de execução.

-   **Interfaces**: As interfaces entre os módulos são complexas e concretas, definidas por formatos de memória, convenções de ponteiros e estruturas de tabelas. Essas decisões precisam ser tomadas em conjunto por todas as equipes antes que o desenvolvimento independente possa começar.

### A Abordagem de Ocultação de Informação

-   **Critério**: Cada módulo é projetado para ocultar uma "decisão de projeto difícil ou que provavelmente mudará" de todos os outros módulos. Os módulos não correspondem mais a etapas de processamento.
-   **Módulos**:

    -   **Line Storage**:Oculta a estrutura de dados interna e o método de armazenamento das linhas.
    -   **Input**:Oculta o formato específico dos dados de entrada.
    -   **Circular Shifter**: Oculta como e quando os deslocamentos circulares são calculados ou armazenados.
    -   **Alphabetizer**:Oculta o algoritmo de ordenação e o momento em que a ordenação é realizada.
    -   **Output**:Oculta o formato da saída.
    -   **Master Control**:Coordena os outros módulos.

-   **Interfaces**: As interfaces são abstratas, consistindo principalmente em nomes de funções e seus parâmetros. Elas revelam o mínimo possível sobre o funcionamento interno de cada módulo.

### Analize das abordagens

A análise da primeira abordagem, baseada em fluxograma, revela fragilidades significativas. Sua flexibilidade é baixa, pois uma mudança em uma decisão de projeto central, como o formato de armazenamento de dados, se propaga por quase todos os módulos, que dependem de uma estrutura de dados compartilhada. O desenvolvimento independente é dificultado, uma vez que as equipes precisam primeiro concordar com as complexas interfaces de dados em um esforço conjunto, atrasando o início do trabalho paralelo. Além disso, a compreensibilidade é baixa, pois para entender o funcionamento de um módulo, é necessário conhecer os detalhes internos dos outros, tornando o sistema compreensível apenas como um todo.

Em contraste, a segunda abordagem, baseada na ocultação de informação, demonstra ser superior em todos os aspectos. Ela oferece alta flexibilidade, pois o impacto de uma mudança é isolado dentro do módulo que "oculta" a decisão de projeto correspondente. O desenvolvimento independente é facilitado por interfaces abstratas e simples (nomes de funções e parâmetros), permitindo que o trabalho comece muito mais cedo e com menos comunicação entre as equipes. A compreensibilidade também é alta, pois cada módulo pode ser estudado e entendido de forma isolada através de sua interface bem definida, sem a necessidade de conhecer os detalhes de implementação dos outros.

## Princípios para uma Boa Decomposição

Com base na análise, o artigo estabelece o princípio da ocultação de informação como o critério orientador para a modularização. Ele sugere começar com uma lista de decisões de projeto difíceis ou voláteis e projetar cada módulo para ocultar uma delas. Exemplos específicos de decisões a serem ocultadas incluem:

-   **Estruturas de Dados**: Uma estrutura de dados e todos os seus procedimentos de acesso e modificação devem pertencer a um único módulo.

-   **Formatos de Blocos de Controle**: Formatos usados em filas de sistemas operacionais devem ser ocultados dentro de um módulo, em vez de servirem como interface pública.

-   **Sequência de Chamada de Rotinas**: A sequência de instruções para chamar uma rotina deve ser parte do mesmo módulo que a própria rotina.

-   **Códigos de Caracteres e Ordenação**: Detalhes como códigos de caracteres e sequências de ordenação devem ser isolados em seu próprio módulo.

-   **Sequência de Processamento**: A ordem em que os itens são processados deve, sempre que possível, ser ocultada dentro de um único módulo.

## Conclusão

O artigo conclui que "é quase sempre incorreto começar a decomposição de um sistema em módulos com base em um fluxograma". Os fluxogramas modelam a sequência de execução no tempo, mas as decisões de projeto mais críticas podem não ser vistas pelo fluxograma. Por outro lado, a proposta de ocultação de informação inverte o processo de projeto: em vez de modelar o fluxo de trabalho, o projetista modela a incerteza e a mudança, identificando decisões difíceis ou voláteis e encapsulando cada uma delas em um módulo dedicado. O resultado é uma arquitetura de software mais robusta, flexível e compreensível, capaz de evoluir com mais facilidade ao longo do tempo.

[Artigo](pdf/Criteria-for-Modularization.pdf)
