## Era da IA
### Documentação
- É um ativo extremamente relevante para o processo de desenvolvimento (como testes automatizados são)
- Tornou-se uma das formas mais eficientes para que os modelos de IA possam utilizá-las como contexto para desenvolvimento, manutenção, planejamento, etc.
- Possibilidade de geração de forma mais rápida, eficiente e assertiva
- Ela realmente pode se tornar um "documento vivo"

### Tipos de documentação
- **Produto (Define o que e por quê)**               → Docs do Produto (Não técnico)
- **Design e Arquitetura (como)**                    → Design Docs (Técnico)
- **Infraestrutura (onde e com o que)**              → Design Docs (Técnico)
- **Operacional (como manter)**                      → Design Docs (Técnico)
- **Conhecimento e Referência (como trabalhar)**     → Design Docs (Técnico)

## PRD (Product Requirement Document)
- É um documento de PRODUTO que visa alinhar equipes de produto com a equipe técnica
- Ele existe quando há uma entrega de valor percebido pelo usuário ou negócio.
- Ele deve ser tratado como um Produto / Feature "independente", com objetivos e métricas e escopo próprio.
- Nem toda feature "merece" um PRD, principalmente quando ela é apenas um dos requisitos funcionais de um sistema.

#### Níveis de PRDs
- Produto
- Módulo / Epic
- Feature
- Etc.


### Seções encontradas em um PRD
Um PRD pode ser totalmente flexível e em muitos casos nem todas as seções necessariamente devem ser utilizadas, principalmente em um projeto pequeno.

#### Seções:
- Visão e propósito
- Contexto e oportunidade
- Público e personas
- Objetivos e métricas
- Escopo
- Requisitos de alto nível (capacidades macro que o produto deve oferecer)
- Estratégia e fases
- Riscos
- KPIs
- Stakeholders


### PRD de alto nível - como contextualização macro de um projeto
#### Um PRD para um grande projeto é um artefato extremamente importante, pois responderá perguntas como:
   - Por que esse produto existe?
   - O que queremos alcançar com esse produto?
   - O que esse projeto vai entregar e o que não vai
   - Para quem estamos construindo isso?
   - Qual problema esse produto resolve e por que ele importa?
   - Como pretendemos alcançar os objetivos?
   - O que o produto deve ser capaz de fazer em linhas gerais?
   - Como saberemos se o produto deu certo?
   - O que pode dar errado e como vamos lidar com isso?
   - Qual o roadmap desse projeto?
   - Quem está envolvido e qual o papel de cada um?
   - Como esse produto se conecta à estratégia da empresa?


### Quando um PRD pode ser necessário como módulo / feature
OBS: Chamamos de Módulo no contexto técnico e Epic no contexto de produto, pois ambos representam o mesmo nível de granularidade — um agrupamento de funcionalidades relacionadas.

#### Caso 1: Sistema de Autenticação / Login
- Para que a plataforma de estudo da Full Cycle funcione, ela obrigatoriamente precisa de um sistema de login.
Olhando dessa forma isso é apenas mais um pré-requisito técnico para acessar ao sistema, ou seja, não há nada de novo, nenhuma inovação, nem decisão de produto envolvida.
- É commodity (não gera valor de negócio específico).
- Já existe modelo padrão de implementação.
- Não muda a experiência nem o modelo do produto.
- As decisões são puramente técnicas, não de produto.
- Provavelmente faria parte dos requisitos funcionais de um sistema maior que pode possuir um PRD

#### Caso 2: Login é uma feature com valor e decisões de produto
- Você está criando uma plataforma multi-tenant para desenvolvedores, com foco em segurança corporativa.
- O time precisa implementar um novo sistema de login com Single Sign-On (SSO), 2FA, OAuth e política de acesso corporativo.
- Nesse caso:
    - Muda a experiência do usuário.
    - Impacta compliance, onboarding e integrações.
    - Tem objetivos mensuráveis (ex: reduzir fricção no login, aumentar adoção, reduzir acessos indevidos).
    - Envolve decisões mais específicas sobre integrações e segurança.


### Seções encontradas em um PRD de "feature"

Um PRD pode ser totalmente flexível e em muitos casos nem todas as seções necessariamente devem ser utilizadas, principalmente em um projeto pequeno.

#### Seções:
- Resumo da Feature
- Contexto e problema a ser resolvido
- Objetivo e métricas
- Escopo
- Requisitos funcionais
- Requisitos não funcionais
- Fluxo do Usuário (User Flow)
- Dependências
- Critérios de Aceitação
- Riscos e Considerações


