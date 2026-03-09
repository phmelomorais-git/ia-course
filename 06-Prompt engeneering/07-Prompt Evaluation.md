## Introdução a Prompt Evaluation
## O que devemos avaliar
Prompt Evaluation
- Avaliação de modelos, NLP, Avaliação de Prompts
- Como as instruçoes dadas ai LLM incluenciam a qualidade das respostas
- Pequenas mudanças no primpr podem melhorar ou degradar a performance nas execuções

Ao avaliar qualquer tipo de prompt
[Objetivos-Why?] - [Tipos de avaliação-How?] - [Avaliadores-Who?]

Comparar prompts versionados
[Dataset] -> [Critério] -> [Análise]

## Entendendo Objetivos
- Correctness
Se a saída está correta de acordo com uma referencia ou fato
- Relevance
Se a saída realmente responde a pergunta feira
- Faithfulness / Groundedness
Se a saída se mantém fiel ao contexto e não alucina informações
- Coinciseness
Se a saída é objetiva, sem enrolação desnecessária
- Helpfulness
Se a saída é útil e clara para o usuário
- Harmfulness / Bias / Toxicity
Se a saída não contém conteúdo tóxico, enviesado ou prejudicial
- Format Adherence (as vezes chamado de Output format)
Se a saída segue o formato esperado (Ex: Json válido, regex, schema)
- Efficiency
Métricas de execução: latência, custo em tokens, throughtput
- Comparative Evaluation / Pairwise Preference.
Comparação entre duas ou mais versões de prompts


## Métricas e tipos de avaliação
Objetivas (determinísticas)
- Precision, Recall, F1, Accuracy: Usados em classificação, extração de campos e detecção de entidades
- Exact Match: Classificação “fechada” — certo ou errado
- String Distance / Edit Distance: Quão próximo o texto gerado está de uma referência
- Embedding Similarity: Medir proximidade semântica entre saída e referência (cosseno, L2)
- JSON validity, Schema validation: Usado para outputs estruturados

Subjetivas (LLM-as-judge ou humanos)
- Correctness: Se a resposta está correta de acordo com uma referência
- Relevance: Se a saída responde à pergunta de fato
- Faithfulness / Groundedness: Não alucina além do contexto dado
- Conciseness: Objetivo ou prolixo
- Helpfulness, Harmfulness, Bias, Toxicity: Segurança e qualidade subjetiva

OBS
Nomes similares em diferentes plataformas ou artigos:
- Criteria evaluators
- Custom rubric
- LLM Judge
- Rating criteria

Sistêmicas (foca na execução, não no conteúdo)
- Latência: tempo de resposta do modelo
- Custo: tokens usados × preço
- Throughput: quantas requisições por segundo o sistema aguenta
- Pass Rate: % de exemplos que passaram em um critério

Comparativas
- Pairwise Evaluation / model comparison: comparar duas saídas A vs B
- A/B Testing: medir taxas de aceitação de usuários em produção

Ground truth
- Referência de “verdade”
- Respostas corretas / conhecidas usadas como base para comparar a saída


## Evaluators (who?)
Avaliadores / Evaluators
Code Evaluator
- Executa código determinístico para avaliar uma saída.
- Criação de uma função que recebe input, output, reference (opcional) e retorna métricas (número, boolean, string).
Exemplo:
Pergunta: Qual banco de dados mais utilizado no mundo?
Referência: PostGreSQL
Saída: PostGreSQL
Avaliação: exact_match
Resultado: {"key": "exact_match", "score": 1}

LLM-as-Judge
- Usa LLM para julgar as saídas com base em uma “rubrica”.
- Definimos critérios (relevance, correctness, etc).
Exemplo:
Pergunta: Como usar goroutines em Go?
Saída: fala sobre threads em Java.
Avaliação: relevance
Resultado: {"key": "relevance", "score": 0.2, "comment": "Resposta não fala de Go"}

Pairwise Evaluator
- Compara duas respostas para o mesmo input.
- Configuração de critérios e o avaliador escolhe a melhor saída.
Exemplo:
Pergunta: Como trabalhar com timeout em uma HTTP Request em Go?
Resposta A: context.WithTimeout
Resposta B: time.Sleep
Avaliação: correctness
Resultado: {"key": "pairwise_preference", "value": "A"}

Summary Evaluator
- Calcula métricas agregadas
- Consolida “scores” de muitos exemplos em métricas finais (ex: pass rate, F1)
Exemplo:
Dataset com 100 exemplos de QA
87 respostas foram corretas
Avaliação: pass rate
Resultado:
[
  {"key": "precision", "score": 0.80},
  {"key": "recall", "score": 0.84},
  {"key": "f1", "score": 0.82}
]

Composite Evaluator
- Combina múltiplas métricas diferentes em um score único ponderado
- Define pesos para métricas já existentes e gera uma métrica final
Exemplo:
correctness = 0.9
relevance = 0.7
conciseness = 0.8
Fórmula:
0.5 × correctness + 0.3 × relevance + 0.2 × conciseness
Resultado:
{"key": "quality_weighted", "score": 0.83}


## Datasets

06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\dataset.jsonl

{
  "inputs": {
    "language": "go",
    "task": "Analise o código e retorne um JSON com os problemas encontrados em 'findings' e um 'summary' curto.",
    "code": "package main\nimport (\n \"net/http\"\n \"io/ioutil\"\n)\n\nfunc fetch(url string) string {\n  resp, _ := http.Get(url)\n  body, _ := ioutil.ReadAll(resp.Body)\n  return string(body)\n}",
    "meta": {
      "topic": "http_client",
      "category": "robustness"
    }
  },
  "outputs": {
    "findings": [
      {
        "type": "missing_timeout",
        "line": 8,
        "description": "http.Get sem contexto ou timeout pode travar indefinidamente",
        "severity": "medium"
      },
      {
        "type": "ignored_error",
        "line": 8,
        "description": "erro de http.Get ignorado",
        "severity": "high"
      },
      {
        "type": "ignored_error",
        "line": 9,
        "description": "erro de ReadAll ignorado",
        "severity": "medium"
      },
      {
        "type": "missing_status_check",
        "line": 9,
        "description": "não verifica status code antes de ler o corpo",
        "severity": "low"
      }
    ],
    "summary": "Adicionar timeout via contexto, checar erros de http.Get e io.ReadAll e validar status code antes de ler o corpo."
  }
}

## Entendendo estrutura dos exemplos
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\dataset.jsonl

## Executando primeira avaliação
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\1-format-eval.py

## Evaluators binarios
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\2-criteria-binary-eval.py

## Score com range
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\3-criteria-score-eval.py

## Additional criteria
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\4-correctness-eval.py
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\5-additional-criteria.py

## Embedding distance
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\6-embedding-distance-eval.py

## Revisor otimista
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\7-bad-text-before.py

## Revisor verboso
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\8-bad-verbose.py

## Alucinação e sem utilidade
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\9-bad-hallucination.py
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\1-basic\10-bad-not-helpful.py

## Cenas para os próximos capítulos
Review...
Explica que não usou Recal e F1. As métricas de precisão ficou para o próximo capitulo.