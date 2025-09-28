# DDD Reference - Cap. 4, 5 e 6

O Design Estratégico é um conjunto de princípios e padrões para gerir a complexidade de sistemas de software de grande escala, especialmente aqueles que integram múltiplos modelos de domínio. Esta disciplina foca-se em obter uma visão realista e abrangente do ecossistema de modelos de um projeto, definindo fronteiras explícitas e gerindo as interações entre eles, pois na ausência de uma estratégia deliberada, as fronteiras dos modelos tornam-se desfocadas e as interconexões complicam-se. Este relatório apresenta uma síntese analítica dos padrões de Design Estratégico, baseada exclusivamente nos materiais de referência, com a análise organizada em torno dos seus três pilares conceptuais: **Mapeamento de Contexto**, **Destilação**, **Estrutura em Larga Escala**

## Mapeamento de Contexto (Context Mapping)

Este pilar foca-se em criar um "mapa" do ecossistema de software. O seu objetivo é obter uma visão realista de todos os modelos de domínio existentes, definir as suas fronteiras explícitas (os Contextos Delimitados) e, crucialmente, descrever as relações entre eles. Ao mapear os pontos de contacto, as traduções e as dinâmicas de poder entre as equipas, este pilar fornece a base para tomar decisões de integração estratégicas e deliberadas, evitando que as fronteiras se tornem confusas e as interconexões, caóticas. Essencialmente, trata de gerir as fronteiras e relações externas de um modelo.

## Destilação (Distillation)

Este pilar trata de encontrar e proteger a parte mais valiosa do seu domínio. É o processo de "ferver" o modelo para extrair a sua essência — o Domínio Central (Core Domain) — separando-a de componentes de suporte ou genéricos que adicionam complexidade, mas não valor estratégico. O Domínio Central é o verdadeiro ativo de negócio que confere uma vantagem competitiva à organização. A Destilação garante que os recursos mais importantes, como o tempo e o talento dos melhores desenvolvedores, sejam focados na área que gera o maior impacto, impedindo que a equipa se perca em questões secundárias. É o pilar que olha para dentro do modelo para priorizar e refinar.

## Estrutura em Larga Escala (Large-Scale Structure)

: Este pilar fornece um princípio organizador para todo o sistema, garantindo que os desenvolvedores possam "ver a floresta em vez de apenas as árvores". O seu objetivo é criar uma linguagem ou um padrão de alto nível que se estende por todo o sistema, permitindo que todos compreendam o papel de cada parte no todo, sem precisar de conhecer os detalhes de cada componente. Padrões como Camadas de Responsabilidade ou uma Metáfora de Sistema ajudam a coordenar o trabalho de equipas independentes e a gerir a complexidade à medida que o sistema cresce, mantendo a coerência global. É o pilar que fornece a coerência e a compreensibilidade em escala global.

## Conclusão

O Design Estratégico oferece um léxico e um conjunto de ferramentas para navegar na complexidade do desenvolvimento de software em larga escala, revelando uma estrutura coesa de três pilares interdependentes. O mapeamento de Contexto fornece as ferramentas para gerir as fronteiras externas e as relações entre diferentes modelos de domínio, permitindo decisões de integração realistas. A destilação foca os recursos para dentro, num processo contínuo de identificação e proteção do Core Domain, alinhando o esforço técnico com a vantagem competitiva. Por fim, a estrutura em Larga Escala fornece a coerência global, oferecendo princípios organizacionais que permitem que o sistema como um todo seja compreensível e que o trabalho de equipas díspares seja coordenado. A natureza destes padrões é holística, pois a escolha de um padrão de Mapeamento de Contexto tem implicações diretas na capacidade de uma equipa para aplicar técnicas de Destilação, enquanto uma Estrutura em Larga Escala fornece o andaime para que múltiplos Contextos Delimitados coexistam de forma coerente.

[Artigo](pdf/DDD_Reference_2015-03.pdf)
