# Hotspot Patterns

O artigo introduz e define o conceito de "hotspot patterns" como uma solução para o desafio crítico de identificar problemas arquiteturais que realmente impactam os custos de manutenção. A tese central é que as ferramentas de análise estática tradicionais geram um volume excessivo de alertas de baixo impacto, dificultando a priorização. Em contraste, os "hotspot patterns" são um conjunto de problemas de arquitetura recorrentes e de alto custo, detectados pela combinação da análise estrutural com o histórico de evolução do projeto. O objetivo é focar a atenção nos problemas que comprovadamente aumentam a propensão a erros e a frequência de alterações, fornecendo um guia baseado em dados para a gestão do débito técnico

# O Desafio do Software em Evolução

A manutenção de software complexo enfrenta o desafio do "débito técnico", onde a arquitetura se degrada com o tempo. Ferramentas de análise estática existentes são insuficientes, pois geram muito "ruído" ao identificar problemas de código que não se correlacionam com custos de manutenção reais, deixando gestores sem saber onde priorizar a refatoração.

Para resolver esse dilema, o artigo propõe os "hotspot patterns", um conjunto de problemas arquiteturais de alto impacto. A inovação está em sua metodologia, que combina a análise estrutural do código com o histórico de evolução do projeto. Com essa abordagem, uma falha estrutural só é considerada um "hotspot" de alta prioridade se o histórico mostrar que ela tem sido custosa, como em arquivos que mudam juntos com frequência. Isso muda o foco da análise de uma simples verificação estática para uma avaliação pragmática do impacto econômico de um problema, medido pelo custo de manutenção.

# Os Cinco Hotspot Patterns

-   **Unstable Interface (Interface Instável):**: Ocorre quando uma interface central e influente do sistema, que deveria ser estável, muda com frequência. Isso provoca um efeito cascata, forçando alterações em todos os módulos que dependem dela e aumentando drasticamente os custos de manutenção.

-   **Implicit Cross-module Dependency (Dependência Implícita Entre Módulos)**: Acontece quando módulos que são estruturalmente independentes mudam consistentemente em conjunto. Isso indica uma dependência oculta, não declarada no código, que viola os princípios da modularidade e aumenta a complexidade.

-   **Unhealthy Inheritance Hierarchy (Hierarquia de Herança Não Saudável)**: Captura violações de princípios de design orientado a objetos. Os casos mais comuns são uma classe pai que depende de uma de suas classes filhas ou um cliente que depende de toda a hierarquia de classes, em vez de apenas da classe base, quebrando o polimorfismo.

-   **Cross-Module Cycle (Ciclo Entre Módulos)**: Identifica ciclos de dependência que atravessam as fronteiras de módulos que deveriam ser independentes. Esses ciclos são particularmente prejudiciais porque fundem componentes distintos em um bloco monolítico e fortemente acoplado.

-   **Cross-Package Cycle (Ciclo Entre Pacotes)**: Um problema bem conhecido que ocorre quando a estrutura de pacotes de um sistema, que deveria ser hierárquica e sem ciclos, contém dependências mútuas. Isso torna o sistema difícil de entender, testar e implantar de forma incremental.

# A Metodologia de Deteção

Para identificar e formalizar os "hotspot patterns", os autores introduzem um modelo conceptual que serve de alicerce para toda a sua abordagem: o Design Rule Space (DRSpace). Este modelo baseia-se na teoria das regras de design (design rule theory) de Baldwin e Clark, que postula que um sistema bem modularizado é composto por "regras de design" estáveis (como interfaces centrais ou classes abstratas) e "módulos independentes" que dependem dessas regras, mas não uns dos outros.

-   **O DRSpace** é, portanto, um novo modelo de arquitetura que vai além das representações tradicionais de componentes e conectores. Ele modela uma porção da arquitetura como um conjunto de ficheiros e as suas relações (herança, agregação, dependência), mas organiza-os em função da sua importância como regras de design. Por exemplo, num sistema que implementa o padrão de projeto

-   **Observer**, a interface do observador seria considerada uma regra de design, pois desacopla o sujeito dos observadores concretos, permitindo que estes últimos sejam modificados ou adicionados sem impactar o primeiro. Da mesma forma, numa arquitetura pipe-and-filter, a classe abstrata que define o pipe seria uma regra de design, e os filtros concretos seriam os módulos independentes.

# Análises

## Quantitativa

-   **Hotspots estão correlacionados com o esforço de manutenção**: Os arquivos envolvidos em qualquer um dos "hotspot patterns" são significativamente mais propensos a erros e a alterações do que a média. O aumento nas métricas de manutenção (como frequência de bugs e de alterações) variou de 40% a mais de 200%, confirmando que os hotspots identificam problemas com custos de manutenção reais e elevados.

-   **O acúmulo de hotspots agrava o problema**: Há uma forte correlação positiva entre o número de hotspots em que um arquivo está envolvido e seu custo de manutenção. À medida que o número de problemas arquiteturais em um arquivo aumenta, as métricas de bugs e alterações crescem drasticamente, o que justifica priorizar a refatoração de arquivos com múltiplos hotspots.

-   **Nem todos os hotspots têm o mesmo impacto**: A análise revelou uma clara hierarquia de severidade. Os padrões Unstable Interface e Cross-Module Cycle mostraram ter, de longe, o maior impacto nos custos de manutenção. Em contraste, a "Implicit Cross-module Dependency" teve um impacto consideravelmente menor. Essa descoberta oferece uma estratégia baseada em dados para priorizar quais problemas arquiteturais corrigir primeiro para obter o maior retorno sobre o investimento.

## Qualitativa

A análise qualitativa foi um estudo de caso em um projeto comercial para validar a utilidade prática da abordagem:

-   **Validação Industrial**: A ferramenta "Hotspot Detector" identificou vários hotspots no projeto da empresa. O arquiteto chefe confirmou que a maioria dos problemas encontrados eram "questões arquiteturais significativas e de alta manutenção", validando que a ferramenta aponta para problemas relevantes para os profissionais da indústria.

-   **Descoberta de Problemas Ocultos**: O arquiteto destacou que o padrão Implicit Cross-module Dependency revelou um problema fundamental que outras ferramentas de análise não conseguiam detectar. Isso ressalta o valor único de integrar o histórico de alterações para expor dependências que não são visíveis apenas no código estático.

-   **Orientação para Ação**: A análise não apenas identificou problemas, mas também forneceu orientações claras para a refatoração. As visualizações ajudaram a equipe a entender as causas dos problemas, como uma "Unstable Interface" que era, na verdade, uma "God interface" precisando ser decomposta. Como resultado direto, a empresa iniciou um plano de refatoração detalhado para corrigir os problemas apontados.

# Conclusão

A pesquisa sobre "hotspot patterns" oferece uma contribuição significativa para a engenharia de software, fornecendo uma metodologia formal e uma ferramenta automatizada para identificar problemas estruturais que impulsionam o débito técnico. A validação empírica demonstra que estes padrões estão fortemente correlacionados com maiores frequências de bugs, alterações e esforço de manutenção. Mais do que apenas encontrar problemas, a abordagem ajuda os desenvolvedores a priorizar a refatoração e a compreender as causas profundas dos problemas, transformando a gestão da qualidade da arquitetura numa atividade estratégica e orientada por dados, essencial para a sustentabilidade de sistemas de software a longo prazo.

[Artigo](pdf/Hotspot-Patternsb.pdf)
