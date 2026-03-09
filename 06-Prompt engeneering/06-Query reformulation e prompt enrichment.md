## Introdução a prompt enrichement
...

## Necessidades para reformulação e enriquecimento de prompts
...

## Fluxo basico e considerações importantes
...

## Qyery2Doc
- Geração de um documento que explica o que a consulta realmente quer
- Utilização do texto gerado para expandir a query antes de exexutar
Passo a Passo
1-recebe query curta do usuário
-Prompt few-shot para LLM pedindo um "mini-documento" bem objetivo sobre o tema da query
-Concatena esse documento com a query original
-Realiza a busca léxica (BM25/Elastic)
-Retorna os trechos recuperados
-Gera resposta final

## Hyde (Hypothetical Document Embeddings)
- Geração de um documento com a intenção de ser a resposta final.
- Utilização do documento para fazer busca
Passo a passo:
- Recebe query do usuário
- Prompt para gerar o documento
- Concatena esse documento com a query original
- Gera embeddings
- Realiza busca semantica
- Retorna os trechos recuperados
- Gera resposta final

Query2Doc vs Hyde
- Query2Doc 
  - Precisa da descrição neutra
  - Pede um mini-artigo explicativo/neutro para enriquecer o vocabilário
  - Nasceu focada para quem ja utiliza BM25.Elastic e quer enriquecer as queries
- HyDE 
  - Precisa da resposta hipotética
  - Pede um documento que parece a resposta real para capturar a semantica e contexto relevantes
  - Nasceu para quem ja usa bancos vetoriais e precisa melhorar o "dense retrieval zero-shot"

Prompt para Query2Doc:
Escreva um texto informativo e neutro de 100 a 150 palavras que explique  o topico abaixo.
inclua definições, termos tecnicos, sinonimos e contexto relacionado, mas não dê uma resposta direta se for uma pergunta.
Tópico: "{query}"

Prompt para Hyde:
Escreva um paragrafo conciso que responda de forma clara a pergunta abaixo. A resposta deve parecer um documento real, com datas, fatos ou descrições prováveis, mesmo que hipotéticas.
Não use linguagem especulativa. (Não diga talvez ou possívelmente)
Pergunta: "{query}"

## Iter-Retgen
- Loop iterativo que alterna entre geração e recuperação
- Gera rascunhos e depois usa o rascunho para buscar de forma mais específica.
Passo a passo:
- Gere um rascunho com "missing markers".
- Transforma lacunas em buscas
- Busca informações relevantes
- Reescreve a resposta e verifica se já mais lacunas ou possibilidade de expansão
Exemplo:
- Draft
- Query
- Fill
- Expansion (Caso tenhamos poucas iterações, expandimos para mais perguntas)

[Input] -> [Draft com partes faltantes] -> [Gera perguntas das partes faltantes] -> [Gera resposta completa]

