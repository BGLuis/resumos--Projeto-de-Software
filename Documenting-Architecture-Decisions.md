# Documenting Architecture Decisions

No desenvolvimento de software, especialmente em projetos que adotam metodologias ágeis, a arquitetura evolui de forma incremental, com decisões sendo tomadas ao longo de todo o ciclo de vida do projeto, e não de uma só vez no início. Essa natureza dinâmica, embora benéfica para a adaptabilidade, apresenta um desafio significativo: rastrear a motivação por trás de decisões cruciais. Um novo membro da equipe, ao se deparar com uma escolha de design, pode ficar perplexo ou frustrado, sem compreender o raciocínio ou as consequências que levaram a tal caminho.

A documentação tradicional, frequentemente na forma de documentos grandes e monolíticos, falha em resolver esse problema. A prática mostra que documentos extensos raramente são mantidos atualizados e, por seu tamanho, raramente são lidos pelos desenvolvedores. Em contraste, a filosofia ágil não se opõe à documentação, mas sim à documentação sem valor. Documentos pequenos e modulares têm uma chance maior de serem mantidos e consumidos pela equipe.

A ausência de um registro claro do racional das decisões coloca os desenvolvedores diante de dois perigos principais, que podem comprometer a sustentabilidade do projeto.

## Aceitação e Reversão Cegas

Quando um desenvolvedor não compreende o "porquê" de uma decisão arquitetural, ele é forçado a escolher entre dois caminhos igualmente arriscados.

O primeiro perigo é a "Aceitação Cega". Neste cenário, o desenvolvedor aceita a decisão existente sem questionar. Isso pode ser aceitável se o contexto original ainda for válido. No entanto, se as circunstâncias do projeto mudaram, a decisão pode não ser mais a ideal. Um projeto que acumula muitas decisões aceitas sem compreensão torna-se frágil, e a equipe de desenvolvimento passa a ter medo de fazer alterações, arriscando o colapso do projeto sob seu próprio peso.

O segundo perigo é a "Reversão Cega". Aqui, o desenvolvedor, frustrado com uma decisão, opta por alterá-la sem entender completamente suas motivações. Embora isso possa, por acaso, corrigir um problema, também pode danificar o valor geral do projeto sem que ninguém perceba. Por exemplo, a decisão original poderia suportar um requisito não funcional crítico (como segurança ou desempenho) que ainda não foi testado, e a reversão cega poderia introduzir uma vulnerabilidade que só se manifestaria em produção.

## O Registro de Decisão de Arquitetura (ADR)

Para evitar os perigos da aceitação e da reversão cegas, a solução proposta é manter uma coleção de registros para decisões "arquitetonicamente significativas". Esta abordagem visa criar um histórico leve e acessível das escolhas que moldam o sistema.

### O Que é "Arquitetonicamente Significativo"?

Uma decisão é considerada "arquitetonicamente significativa" se afeta um ou mais dos seguintes aspectos :

-   **Estrutura**

-   **Características Não Funcionais**

-   **Dependências**

-   **Interfaces**

-   **Técnicas de Construção**

### A Estrutura do ADR

Cada ADR é um arquivo de texto curto, com um formato simples para garantir que seja fácil de criar e consumir. O documento inteiro deve ter no máximo uma ou duas páginas e ser escrito como se fosse uma conversa com um futuro desenvolvedor, usando frases completas e um bom estilo de escrita.

O formato proposto possui as seguintes seções :

#### Título

Uma frase nominal curta que descreve a decisão. Por exemplo, "ADR 1: Implantação em Ruby on Rails 3.0.10".

#### Contexto

Descreve as forças em jogo (tecnológicas, políticas, sociais, etc.) que levaram à necessidade da decisão. Esta seção deve descrever os fatos de forma neutra, destacando as tensões existentes.

#### Decisão

Uma declaração clara e inequívoca da resposta às forças descritas no contexto. Deve ser redigida em frases completas e com voz ativa, como "Nós iremos...".

#### Status

Rastreia o ciclo de vida da decisão. Os status podem ser "proposto", "aceito", "obsoleto" (deprecated) ou "substituído" (superseded). Se uma decisão for revertida, o registro antigo é mantido, mas marcado como substituído, com uma referência ao novo ADR.

#### Consequências

Descreve o novo contexto que resulta da aplicação da decisão. É crucial listar todas as consequências, sejam elas positivas, negativas ou neutras, pois elas frequentemente se tornam o contexto para decisões futuras.

#### Diretrizes de Gestão

Para garantir a eficácia da prática, os ADRs devem seguir algumas diretrizes de gestão :

-   **Armazenamento**: Os ADRs devem ser mantidos no repositório do projeto, em um diretório como doc/arch/, utilizando uma linguagem de marcação leve como Markdown.

-   **Numeração**: Devem ser numerados de forma sequencial e monotônica. Os números não devem ser reutilizados.

-   **Imutabilidade**: Uma vez que uma decisão é aceita, o registro não deve ser alterado. Se a decisão for revertida, um novo ADR deve ser criado para substituí-la.

## Consequências e Relato de Experiência

A adoção dos ADRs traz benefícios claros, conforme observado na prática.

### Benefícios da Prática

-   **Visibilidade e Continuidade**: Desenvolvedores e stakeholders podem consultar os ADRs mesmo com a mudança da equipe ao longo do tempo. A motivação por trás das decisões permanece visível para todos, eliminando a confusão sobre "o que eles estavam pensando?".

-   **Contexto Evolutivo**: As consequências de um ADR frequentemente se tornam o contexto para decisões subsequentes, criando uma linguagem de padrões onde as decisões maiores abrem espaço para as menores se encaixarem.

-   **Clareza para Mudanças**: Fica claro quando uma decisão antiga deve ser alterada, com base nas mudanças no contexto do projeto.

## Relato de Experiência

Em projetos que utilizaram o formato, o feedback inicial de clientes e desenvolvedores foi bastante positivo. Desenvolvedores que se juntaram aos projetos afirmaram apreciar o grau de contexto que obtiveram ao ler os ADRs. A prática provou ser especialmente útil para capturar intenções de longo prazo, evitando que decisões atuais dificultem futuras reestruturações arquitetônicas.

Uma potencial objeção sobre a acessibilidade dos ADRs (por estarem no controle de versão) foi mitigada pelo uso de repositórios como o GitHub, que renderiza arquivos Markdown automaticamente, tornando-os tão amigáveis quanto uma página de wiki.

## Conclusão

Os Registros de Decisão de Arquitetura (ADRs) se mostram uma ferramenta útil e de baixo custo para documentar decisões arquitetonicamente significativas. Ao capturar o contexto, a decisão e suas consequências em um formato leve e modular, eles resolvem o problema da perda de conhecimento em projetos ágeis, evitam os perigos da aceitação ou reversão cega de decisões e garantem que o racional por trás da arquitetura de um sistema seja preservado ao longo do tempo.

[Artigo](pdf/Documenting-Architecture-Decisions.pdf)
