## Precision
- De tudo que o modelo detectou, quanto estava correto?
Ex: De 10 bugs em um sistema, o modelo detectou 5.
- FP (False Positives): Quando o modelo detecta algo errado.
Ex: Classificou algo que não era bug como um bug.
- Fórmula:
\mathrm{Precision}=\frac{TP}{TP+FP}- Exemplo:
Temos 20 logs no sistema, onde 10 realmente são bugs.
O sistema identificou 8 bugs, porém também identificou 5 logs como bug (que não eram bug).
\mathrm{Precision}=\frac{8}{8+5}=0.61
- Alta precisão: Baixo índice de FP
- Baixa precisão: Alto índice de FP

## Recall
- De tudo o que deveria ser detectado, quanto o modelo encontrou?
Ex: De 10 bugs, encontrou apenas 7.
- FN (False Negatives):
3 falsos negativos, pois 3 bugs não foram detectados.
- Fórmula:
\mathrm{Recall}=\frac{TP}{TP+FN}\mathrm{Recall}=\frac{7}{7+3}=0.7
- Alto recall: Encontra a maioria dos bugs (poucos escapam)
- Baixo recall: Perde muitos bugs (deixa passar problemas)

## F1 — (F-measure ou F-score)
- Combinação de Precisão e Recall em um único número.
Mostra o equilíbrio entre acertar bem e não deixar passar casos importantes.
- Fórmula:
F1=2\times \frac{\mathrm{Precision}\times \mathrm{Recall}}{\mathrm{Precision}+\mathrm{Recall}}
- Exemplo:
F1=2\times \frac{0.61\times 0.7}{0.61+0.7}=0.65
- F1 alto: Bom equilíbrio (encontra bugs sem muitos falsos positivos)
- F1 baixo: Desequilíbrio (perde bugs ou inventa bugs)

## Quando usar no mundo real

## Entendendo 3 tipos de prompt
Apresentando os prompts:
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\2-precision\prompts\aggressive.yaml
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\2-precision\prompts\balanced.yaml
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\2-precision\prompts\conservative.yaml

## Calculando as métricas
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\2-precision\metrics.py

## Comparação na prática
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\2-precision\1-conservative-high-precision.py
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\2-precision\2-aggressive-high-recall.py
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\2-precision\3-balanced-best-f1.py

## Entendendo Pairwise Evaluator vs Evaluation
Pairwise Evaluator
- Compara duas respostas para o mesmo input
- Configuração de critérios e o avaliador escolhe a melhor saída
Exemplo:
Pergunta: Como trabalhar com timeout em uma HTTP Request em Go?
Resposta A: context.WithTimeout
Resposta B: time.Sleep
Avaliação: correctness
Resultado:
{"key": "pairwise_preference", "value": "A"}

## Contexto do nosso experimento
Upload dataset
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\3-pairwise\upload_dataset.py

Criar prompts
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\3-pairwise\create_prompts.py

## Executando Pairwise
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\3-pairwise\run.py

## Refazendo evaluation com prompt otimizado
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\3-pairwise\prompts\security_expert_v2.yaml

## Pairwise com justificativa do LLM-as-Judge

Files são datasets no código
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\4-pairwise-doc\prompts\prompt_doc_a.yaml

Esse juiz vai explicar e justificar
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\4-pairwise-doc\prompts\llm_judge_pairwise.yaml

Create prompt
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\4-pairwise-doc\create_prompt.py

Load dataset
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\4-pairwise-doc\dataset.jsonl

Run
06-Prompt engeneering\sourcecode\mba-ia-prompt-engineering\7-evaluation\4-pairwise-doc\run.py