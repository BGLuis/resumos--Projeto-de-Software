# Software Architecture: A Roadmap

O artigo apresenta uma tese central que embora a arquitetura de software tenha feito progressos significativos na transição de uma prática ad hoc para uma disciplina de engenharia, ela ainda é imatura, e enfrenta novos e profundos desafios impulsionados por mudanças de paradigma na computação.

## Os Papéis Fundamentais

-   **Compreensão**: A arquitetura serve como um mecanismo para gerenciar a complexidade em sistemas de grande escala. Ela o faz através da abstração, apresentando um design de alto nível que expõe as principais restrições e a lógica por trás das decisões de design, tornando o sistema intelectualmente tratável.

-   **Reutilização**: A arquitetura eleva a reutilização para além do nível do componente individual. Ela permite a reutilização de componentes de grande porte e, mais importante, de frameworks e padrões de design completos. O trabalho em arquiteturas de software específicas de domínio é citado como prova desse potencial.

-   **Construção**: A arquitetura funciona como um plano para o desenvolvimento, definindo os componentes principais e suas dependências. Uma arquitetura em camadas, por exemplo, estabelece fronteiras de abstração claras e restringe a comunicação entre componentes, guiando assim o processo de implementação.

-   **Evolução**: Uma arquitetura bem definida torna explícitas as "paredes de sustentação" de um sistema. Isso permite que as equipes de manutenção compreendam as ramificações das mudanças e estimem os custos de modificação com maior precisão. A arquitetura separa a funcionalidade de um componente de seus mecanismos de interação, facilitando a evolução de aspectos como desempenho ou interoperabilidade.

-   **Análise**: Descrições arquitetônicas formais criam oportunidades para análises rigorosas que são impossíveis com diagramas informais. Isso inclui a verificação de consistência, a conformidade com regras estilísticas, a análise de atributos de qualidade (como desempenho e confiabilidade) e a análise de dependências.

-   **Gestão**: A obtenção de uma arquitetura viável é um marco fundamental no processo de desenvolvimento de software industrial. A avaliação arquitetônica força uma compreensão mais clara dos requisitos, das estratégias de implementação e dos riscos potenciais, tornando-se uma ferramenta de gestão crítica.

## A Trajetória

### Ontem: Uma Era de Informalidade

Há uma década, a arquitetura era, em grande parte, uma "questão ad hoc". As descrições dependiam de "diagramas de caixas e linhas" informais que raramente eram mantidos. As escolhas arquitetônicas eram feitas de forma idiossincrática, geralmente adaptando um design anterior, fosse ele apropriado ou não. O conhecimento arquitetônico era artesanal, aprendido através de experiência e não era transferível; os bons arquitetos não conseguiam ensinar seu ofício a outros. Consequentemente, era impossível analisar formalmente os designs ou verificar se uma implementação estava em conformidade com sua arquitetura. Apesar dessa informalidade, as sementes da mudança já estavam sendo plantadas, impulsionadas pelo reconhecimento de padrões de design compartilhados (como "pipeline" ou "cliente-servidor") e pelo desejo de criar frameworks reutilizáveis para famílias de produtos.

### Hoje: Pilares de uma Disciplina em Maturação

O primeiro pilar foi o Formalismo e as Ferramentas, marcados pela ascensão das Linguagens de Descrição de Arquitetura (ADLs). As ADLs surgiram para resolver os problemas de ambiguidade e falta de capacidade de análise das abordagens informais. Linguagens como Wright, Aesop, Rapide e Darwin forneceram sintaxes formais e ferramentas para análise, simulação e verificação de designs. Essa proliferação levou a esforços de unificação, como a linguagem de intercâmbio Acme, e gerou um debate sobre o uso de notações de propósito geral como UML, que ofereciam familiaridade aos profissionais, mas menos poder de análise automatizada.

O segundo avanço foi a Sistematização e a Reutilização, evidenciada pela emergência de linhas de produtos e padrões de integração. A abordagem de linha de produtos mudou o foco do desenvolvimento de sistemas únicos para a criação de uma arquitetura reutilizável para uma família de sistemas relacionados, prometendo redução de custos a longo prazo. Paralelamente, surgiram padrões de integração entre fornecedores, que forneciam a "cola" conceitual e de tempo de execução para integrar componentes de múltiplos fornecedores. Garlan ilustra isso com exemplos como a High Level Architecture (HLA) para simulação distribuída e os Enterprise JavaBeans (EJB) para aplicações empresariais.

O terceiro pilar foi a Disseminação de Conhecimento através da codificação de estilos e padrões arquitetônicos. A publicação de livros e cursos ajudou a criar um corpo de conhecimento compartilhado. Um conceito central foi a documentação de estilos arquitetônicos padrão (por exemplo, pipe-and-filter, blackboard, cliente-servidor). Um estilo especifica um vocabulário de design, restrições e semântica, permitindo que os arquitetos reutilizem soluções comprovadas. Ao mesmo tempo, a necessidade de compor sistemas a partir de partes heterogêneas levou ao reconhecimento do problema do "desajuste arquitetônico" (architectural mismatch), onde componentes fazem suposições conflitantes sobre seu ambiente.

### Amanhã: Paradigmas Emergentes e Desafios Futuros

A primeira tendência é o Imperativo Econômico, ou a mudança no equilíbrio entre construir e comprar ("Changing Build-Versus-Buy Balance"). A pressão para reduzir o tempo de lançamento no mercado estava forçando as empresas a se tornarem integradoras de sistemas, montando soluções a partir de código desenvolvido externamente. Isso exigiria um movimento da engenharia "baseada em componentes" para a "baseada em arquitetura", com ênfase em padrões de integração de alto nível, processos de subcontratação mais rigorosos e a padronização de notações como UML e XML.

A segunda força é o Imperativo da Conectividade, com a transição para a computação centrada na rede. Esse novo paradigma quebra o modelo tradicional de um "sistema fechado" com controle centralizado. Os desafios arquitetônicos decorrentes incluem a necessidade de arquiteturas que escalem para o tamanho e a variabilidade da Internet, o suporte a coalizões dinâmicas de recursos distribuídos e autônomos, e a capacitação de usuários finais para compor seus próprios sistemas e serviços.

A terceira tendência é o Imperativo da Ubiquidade, impulsionado pela computação pervasiva e pela explosão de dispositivos heterogêneos embutidos no ambiente. Essa visão impõe desafios arquitetônicos únicos, como a gestão crítica de recursos em dispositivos limitados, a necessidade de flexibilidade extrema para reconfiguração dinâmica à medida que dispositivos aparecem e desaparecem, e a gestão automatizada para suportar a mobilidade do usuário entre diferentes ambientes computacionais.

Observadas em conjunto, essas três tendências representam um ataque fundamental ao conceito de design de sistema estático e centralmente controlado. O desafio final para a arquitetura futura, conforme previsto por Garlan, é a gestão de sistemas que são inerentemente dinâmicos, descentralizados e carecem de um único ponto de controle. Isso exige uma mudança de projetar um artefato estático para projetar um framework para gerenciar conjuntos dinâmicos.

## Conclusão

Em sua avaliação final, David Garlan conclui que a arquitetura de software, embora tenha crescido consideravelmente, ainda não atingiu a plena maturidade como uma disciplina de engenharia universalmente praticada. Seu sucesso futuro depende de um caminho duplo: a contínua disseminação e amadurecimento das práticas existentes e a necessidade de "inovações significativas" para enfrentar os desafios disruptivos impulsionados pela "paisagem em mudança da computação".

[Artigo](pdf/Software-Architecture-A-Roadmap-1.pdf)
