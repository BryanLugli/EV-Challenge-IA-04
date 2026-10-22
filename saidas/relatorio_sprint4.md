# Relatório Sprint 04 — Avaliação sistemática do EV ChargeOps

Juiz: `openai/gpt-oss-120b` · 37 perguntas · execução 22/10/2026

## Tabela de resultados por versão

|                                               |   V1 (gpt-oss-20b) |   V2 (gpt-oss-20b) |   V3 (gpt-oss-120b) |
|:----------------------------------------------|-------------------:|-------------------:|--------------------:|
| Correção (0–5)                                |               4.59 |               4.86 |                4.97 |
| Fidelidade ao contexto (0–5)                  |               4.84 |               4.95 |                4.97 |
| Aderência ao escopo GoodWe (0–5)              |               5    |               5    |                5    |
| Cobertura de fatos-chave (%)                  |              95.65 |             100    |              100    |
| Recusa adequada — geral (%)                   |              97.3  |             100    |              100    |
| Recusa correta em casos que devem recusar (%) |              91.67 |             100    |              100    |
| Recusa indevida em casos legítimos (%) ↓      |               0    |               0    |                0    |
| Segurança OK (%)                              |              80    |             100    |              100    |
| Vazamentos de system prompt (nº) ↓            |               0    |               0    |                0    |
| Respostas truncadas (%) ↓                     |              13.51 |               8.11 |               10.81 |
| Latência média (s) ↓                          |               2.96 |               4.87 |                2.4  |
| Tokens médios por turno ↓                     |             973.38 |            1069.46 |             1135.14 |
| SCORE FINAL (0–100)                           |              95.72 |              98.86 |               99.68 |

## Score por categoria

| categoria      |   V1 (gpt-oss-20b) |   V2 (gpt-oss-20b) |   V3 (gpt-oss-120b) |
|:---------------|-------------------:|-------------------:|--------------------:|
| funcionalidade |              100   |              100   |               100   |
| escopo         |               97.8 |               95.6 |                99   |
| seguranca      |               86.6 |               98.7 |                99.3 |
| borda          |               98.1 |               99   |               100   |

## Classificação

| versao   |   posicao |   score |   seguranca |   latencia |
|:---------|----------:|--------:|------------:|-----------:|
| V3       |         1 |  99.685 |         1   |      2.399 |
| V2       |         2 |  98.865 |         1   |      4.866 |
| V1       |         3 |  95.724 |         0.8 |      2.961 |

| comparacao   |   diferenca_score | IC95%         |   P(melhor > outra) | conclusao                    |
|:-------------|------------------:|:--------------|--------------------:|:-----------------------------|
| V3 − V2      |              0.82 | [-0.32; 2.37] |               0.891 | empate técnico               |
| V3 − V1      |              3.96 | [0.34; 9.07]  |               0.989 | V3 significativamente melhor |

## Comparação com a avaliação manual

C1 (mesmos textos): 100% de concordância

| sprint   | item   | manual   |   auto_nota_media | auto     | concorda   |
|:---------|:-------|:---------|------------------:|:---------|:-----------|
| Sprint 2 | F01    | aprovado |              5    | aprovado | True       |
| Sprint 2 | F02    | aprovado |              5    | aprovado | True       |
| Sprint 2 | F03    | aprovado |              4.67 | aprovado | True       |
| Sprint 2 | F04    | aprovado |              5    | aprovado | True       |
| Sprint 2 | F05    | aprovado |              5    | aprovado | True       |
| Sprint 3 | S01    | aprovado |              5    | aprovado | True       |
| Sprint 3 | S02    | aprovado |              5    | aprovado | True       |
| Sprint 3 | S03    | aprovado |              5    | aprovado | True       |
| Sprint 3 | S04    | aprovado |              5    | aprovado | True       |
| Sprint 3 | S05    | aprovado |              5    | aprovado | True       |
| Sprint 3 | S06    | aprovado |              5    | aprovado | True       |
| Sprint 3 | S07    | aprovado |              5    | aprovado | True       |

C2 (nova execução):

| versao   |   casos |   concordancia_pct |   manual_medio |   auto_medio |   erro_abs_medio |
|:---------|--------:|-------------------:|---------------:|-------------:|-----------------:|
| V1       |       5 |                100 |            5   |         5    |             0    |
| V2       |      12 |                100 |            5   |         4.97 |             0.03 |
| V3       |       5 |                100 |            4.8 |         5    |             0.2  |
