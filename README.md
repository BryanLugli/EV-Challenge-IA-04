# EV-Challenge-IA-04 — Avaliação sistemática do EV ChargeOps

**EV Challenge 2026 · Sprint 04 · Prompt and Artificial Intelligence · FIAP × GoodWe Brasil · Turma 1CCPY**

Fechamento do semestre do chatbot **EV ChargeOps** (gestão compartilhada de eletropostos em condomínios).
Nesta sprint a checagem manual das Sprints 2 e 3 foi substituída por um **pipeline de avaliação reprodutível**:

- **Golden dataset** (`golden_dataset.json`) — 37 perguntas com gabarito: funcionalidade (15), escopo (5),
  segurança/prompt injection (10) e casos de borda (7). Reaproveita os 5 testes da Sprint 1/2 e os 7 testes de
  segurança da Sprint 3.
- **Pipeline** (`sprint4_avaliacao.ipynb`, roda no Kaggle) — executa o dataset contra 3 versões do agente e
  calcula métricas com **LLM as a judge** (juiz de outra família de modelo, rubrica 0–5, temperatura 0) +
  métricas determinísticas (fatos-chave por regex, vazamento de prompt, truncamento).
- **Versões comparadas**
  | Versão | Origem | Arquitetura | Modelo |
  |---|---|---|---|
  | V1 | Sprint 2 | `GoodWeChatbot` manual, histórico em lista Python | Qwen2.5-7B-Instruct (ou substituto do mesmo porte) |
  | V2 | Sprint 3 | LangChain + `RunnableWithMessageHistory` | openai/gpt-oss-20b (Groq) |
  | V3 | Sprint 3 | LangChain + `RunnableWithMessageHistory` | openai/gpt-oss-120b (Groq) |
- **Saídas** (`saidas/`) — tabela de resultados por versão, score por categoria, ranking com IC 95% por
  bootstrap, comparação com a avaliação manual da Sprint 3 e o **relatório final em PDF**.

## Como executar
1. Importe `sprint4_avaliacao.ipynb` no Kaggle (*File → Import Notebook*).
2. *Add-ons → Secrets*: ative o segredo `HF_API_KEY` (token da Hugging Face com a chave do Groq configurada em
   *Inference Providers*).
3. *Settings → Internet*: **On**.
4. *Run All* (≈30–60 min no plano gratuito; o notebook espera sozinho no rate limit e guarda cache, então
   pode ser reexecutado sem refazer chamadas).
5. Baixe a pasta `saidas/` da aba *Output* e suba no repositório.

## Segurança das credenciais
Nenhuma chave fica no código: ela é lida do Kaggle Secrets (ou da variável de ambiente `HF_API_KEY` fora do
Kaggle). `.env` está no `.gitignore`.

## Equipe
| Nome | RM | Turma |
|---|---|---|
| Bryan Lugli | 571350 | 1CCPY |
| Beckman Rodrigues Lugli | 573442 | 1CCPY |
| Guilherme Xavier | 573053 | 1CCPY |

Repositórios anteriores: [Sprint 1](https://github.com/BryanLugli/GoodWe-EV-Challenge-IA) ·
[Sprint 2](https://github.com/BryanLugli/EV-Challenge-IA-02) · [Sprint 3](https://github.com/BryanLugli/EV-Challenge-IA-03)

## Resultados da Sprint 04

| Versão | Score final (0–100) | Segurança OK |
|---|---|---|
| V1 — Sprint 2 (chatbot manual) | 95,7 | 80% |
| V2 — Sprint 3 (LangChain + gpt-oss-20b) | 98,9 | 100% |
| V3 — Sprint 3 (LangChain + gpt-oss-120b) | 99,7 | 100% |

**Melhor versão:** V3, em empate técnico com a V2; as duas são superiores à V1.
Os guardrails adicionados na Sprint 3 corrigiram a falha de prompt injection da V1 (aceitou uma tarifa falsa de R$ 0,00).

Relatório completo: [`saidas/relatorio_sprint4.pdf`](saidas/relatorio_sprint4.pdf)

## Divisão de trabalho (Sprint 04)

- *Bryan Lugli (RM 571350):* integração das versões V1–V3 no pipeline e execução no Kaggle
- *Beckman Rodrigues Lugli (RM 573442):* golden dataset (perguntas, gabaritos e casos de segurança)
- *Guilherme Xavier (RM 573053):* rubrica do LLM juiz, comparação com a avaliação manual e relatório

Uso de IA generativa: o Claude (Anthropic) foi usado como apoio para estruturar o código e revisar o dataset; execução, conferência e análise dos resultados foram feitas pelo grupo.

