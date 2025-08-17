# The Big Ball of Mud

O artigo analisa a arquitetura de software que, embora raramente discutida em âmbitos acadêmicos, é a mais comum na prática: a "Grande Bola de Lama" (Big Ball of Mud - BBoM). Um BBoM é um sistema com uma estrutura casual, desorganizada e que se desenvolve a favor de uma maior conveniência do que por um design deliberado.
Em vez de simplesmente condenar esta abordagem, os autores investigam, parte por parte e suas causas, por que ela é tão popular e eficaz, argumentando por que ela deve ser entendida como um padrão legítimo, uma solução recorrente para problemas reais e não apenas como um padrão a ser evitado.

## Definição

BBoM é um sistema de software com uma estrutura desorganizada, comparado a um "código espaguete", onde a informação é fragmentada de forma descuidada e a arquitetura original, se em algum momento existiu, foi esquecida pelo tempo.
Caracteriza-se por crescimento irregular, remendos ou "gambiarras" no código, duplicidade de dados e dependências globais.

## Motivos

Alguns motivos comuns levam à implementação forçada ou consciente do BBoM:

-   **Tempo e Custo**: A pressão para entregar rapidamente e com orçamento limitado faz com que a arquitetura, uma preocupação de longo prazo, seja vista como um luxo.
-   **Experiência e Habilidade**: A falta de experiência no domínio do problema ou de competências arquitetónicas na equipa pode levar a soluções que não são bem estruturadas.

-   **Complexidade**: Muitas vezes, o software reflete a "complexidade essencial" do problema que está a resolver. Se o problema é inerentemente confuso, o software também o será.

-   **Mudança:** Requisitos inesperados podem forçar alterações que "cortam" a estrutura da arquitetura original, degradando-a ao longo do tempo.

## Padroes

O BBoM não existe isoladamente. foram reconhecido apguns pádroes ou lemas que exenplificao o cilco de dica desse sistema

-   **THROWAWAY CODE (Código Descartável)**: Protótipos ou soluções rápidas que funcionam e, por isso, nunca são deitados fora, tornando-se a base de um futuro BBoM.
-   **PIECEMEAL GROWTH (Crescimento Fragmentado)**: O sistema evolui de forma incremental, com novas funcionalidades a serem adicionadas sem um plano geral, o que leva à erosão da arquitetura.
-   **KEEP IT WORKING (Mantenha a Funcionado)**: A prioridade passa a ser manter o sistema estável e funcional, favorecendo pequenas alterações de baixo risco que solidificam a estrutura caótica existente.

-   **SWEEPING IT UNDER THE RUG (Varrer para Debaixo do Tapete)**: Quando a desordem se torna esmagadora, as partes mais caóticas são isoladas atrás de interfaces bem definidas para conter o problema em vez de o resolver.

-   **RECONSTRUCTION (Reconstrução)**: Eventualmente, o sistema torna-se tão degradado que a única solução é descartá-lo e começar de novo, usando as lições aprendidas com o sistema antigo para guiar a nova implementação.

## Conclusão

Os autores não condenam o "The Big Ball of Mud", mas, após o estudo, o sistema é visto como um caminho natural e, de certa forma, até racional perante as pressões do mundo real do desenvolvimento de software. Mas é ressaltada a importância de um aprendizado contínuo, tanto da equipe quanto da organização, sobre o domínio do problema e as oportunidades arquitetônicas à medida que o sistema evolui.

[Artigo](pdf/The-Big-Ball-of-Mud.pdf)
