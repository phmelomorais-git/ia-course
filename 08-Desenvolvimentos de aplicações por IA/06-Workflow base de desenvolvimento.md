# Desenvolvimento de aplicações com IA

## Arquitetura do StreamTube
![alt text](image-37.png)

 
## Dinâmica de desenvolvimento do projeto
- Back-end (Nest.js)
- Fundação de IA para Back-end
- Front-end (Next.js)
- Fundação de IA para Front-end
- Dev Fullstack - ambos ao mesmo tempo

## Workflow de desenvolvimento com IA
![alt text](aovivoimage.png)

## Worflow Plan --> Implement
![alt text](aovivoimage-1.png)

## Workflow com Design First
![alt text](aovivoimage-2.png)

## Fundação da IA
![alt text](aovivoimage-3.png)

## Artefatos de fundação com Claude Code / Copilot
![alt text](aovivoimage-4.png)


## Claude Code Configurations (How artefacts helps)
![alt text](aovivoimage-5.png)

## Engenharia de contexto
![alt text](aovivoimage-6.png)

![alt text](aovivoimage-7.png)


## Criando Projeto backend com Nest.JS
- sudo apt update && sudo apt upgrade -y
- sudo apt autoremove -y
- Install Node with NVM https://nodejs.org/en/download
- npm install -g @nestjs/cli
- nest new nestjs-project
- npm run start:dev


## Configurando Docker no Projeto
- Criar o docker file e o compose.
- Instalar o docker desktop e linkar o docker com o wsl

## A fundação de IA que vamos implementar
![alt text](image-39.png)


## Criando arquivo CLAUDE.md global
No video ele copia e cola o conteúdo e mostra o conteudo do arquivo. 
Regras inegociaveis

## Criando o sub CLAUDE.md do Nest.JS
No video ele copia e cola o conteúdo e mostra o conteudo do arquivo. 
Regras inegociaveis

## Criando as Rules (Code conventions)
frontmatter com paths
Ele copiou e colou tudo também...
Regras inegociaveis

## Dicas de curadoria de skills no projeto

### Avaliando a própria SKILL e de terceiros

- Li o SKILL.md e todos os arquivos auxiliares por completo?
- A description é precisa? Não vai disparar falsos positivos/negativos?
- A estrutura é modular (index leve + referências lazy)? (Para skill grandes)
- O impacto na context window é aceitável?
- Não há instruções suspeitas, prompt injection ou chamadas externas estranhas?
- Testei em cenários reais do meu projeto?
- Testei em mais de um modelo (se aplicável)?
- A skill é compatível com meu stack e convenções?
- Não conflita com outras skills ativas?
- Sei quem é o autor e se a skill é mantida?


## Curadoria da skill de boas praticas do nest.js
Ele baixou a skill nestjs-best-practice
Apagou o readme, agent.md e a pasta scripts
E alterou com o prompt:
![alt text](image-40.png)

Não deu certo e ele pediu para refazer. Ele quer um frontmatter mais objetivo com menos de 100 tokens

Alterou na mão até dar 92 tokens

Teste de planejamento...
![alt text](image-41.png)


## Curadoria  da skill de vboas praticas do TypeORM
Problemas: 600 linhas e descrição ruim.


## Confrontando as Regras e as skills
Boa ideia...
![alt text](image-42.png)


## Introdução ao MCP
![alt text](image-43.png)

![alt text](image-44.png)


## Workflow dos servidores MCP do projeto
![alt text](image-45.png)


## Configurando MCP do Context7
![alt text](image-46.png)

![alt text](image-47.png)

![alt text](image-48.png)

## Configurando MCP do PostgreeSQL
![alt text](image-49.png)


