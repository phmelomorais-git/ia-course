## Fundamentos de documentação
Contexto
Processo de documentação acompanha a Engenharia de Software

Nos anos 1970 e 1980, processos sequenciais como Waterfall e metodologias baseadas em RUP (Rational Unified Process)

Documentos de requisitos, especificações de sistemas e modelos UML eram extensos e formais

No Waterfall, a documentação era vista como um contrato, e as decisões eram registradas antes da implementação.

Waterfall (Cascata)
Ordem linear e rígida, onde cada fase precisa ser concluída completamente antes de a próxima começar

### Fluxo
- Levantamento de Requisitos
Todos os requisitos do sistema são definidos e documentados de forma detalhada logo no início do projeto.

- Análise e Projeto (Design)
Com base nos requisitos, é feito o projeto da arquitetura, das interfaces e dos componentes.

- Implementação (Codificação)
Os desenvolvedores escrevem o código conforme o projeto definido.

- Testes
O sistema é testado para verificar se atende aos requisitos.

- Deploy
"Produto" era "entregue" ao cliente

- Manutenção
Correções e melhorias são feitas após a entrega.

Observação final:
O cliente só vê o resultado no final. Se algo estiver errado nos requisitos, o retrabalho é alto.


## RUP (Rational Unified Process)
- O Rational Unified Process (RUP) foi criado pela Rational Software (hoje IBM) para oferecer um processo mais iterativo e flexível que o Waterfall, mas ainda com forte controle e documentação.

- Ele é baseado em disciplinas (como requisitos, análise, design, implementação, testes e gerenciamento de configuração) e se organiza em quatro fases principais, que se repetem de forma iterativa.

### Fluxo
- Inception (Concepção)
Define o escopo, os objetivos do projeto e a viabilidade do negócio.

- Elaboration (Elaboração)
Detalha a arquitetura do sistema, identifica riscos e refina os requisitos principais.

- Construction (Construção)
Desenvolvimento incremental do produto com base na arquitetura aprovada.

- Transition (Transição)
Entrega do sistema, treinamento dos usuários e correção de falhas.

### Diferenciais do RUP
- Iterativo: permite ciclos de desenvolvimento menores dentro de cada fase.
- Dirigido por casos de uso: os requisitos são modelados a partir de como o usuário interage com o sistema.
- Arquitetura centralizada: define uma arquitetura sólida antes de construir o produto.
- Baseado em papéis: define claramente os papéis de analistas, desenvolvedores, testadores, etc.

### Vantagens sobre Waterfall
- Permite revisões e ajustes em cada iteração.
- Reduz riscos, pois partes do sistema são validadas progressivamente.
- Melhora a comunicação entre times e stakeholders.

### Desvantagens
- Mais complexo de gerenciar do que o Waterfall.
- Ainda exige bastante documentação e planejamento.
- Pode ser custoso para projetos pequenos.


## Agile / Manifesto Ágil
- Manifesto Ágil foi criado em 2001, ele trouxe a frase que marcou essa transição.
- "Software em funcionamento mais que documentação abrangente."
- Isso não significava eliminar a documentação, mas mudar seu propósito:
- A documentação deixa de ser um fim em si mesma e passa a ser um meio para comunicação e alinhamento rápido.

## Problemas conhecidos e comuns ao trabalharmos com documentação
- Muitas vezes acaba sendo inexistente
- Desatualizadas
- Priorização na criação do software ao invés de documentar *
- Processo extremamente massante e lento
- Raramente é lida por todo o time (muitas vezes agrega pouco valor)
- Muitos desenvolvedores / líderes, área de produto, etc não sabem criar o documento para cada caso de uso.
