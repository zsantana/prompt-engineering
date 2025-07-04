# 🔧 Prompt Engineering

Repositório destinado a compartilhar técnicas, melhores práticas e automatizações para engenharia de prompts voltada ao uso de LLMs (Large Language Models).

## 📖 Conteúdo

* **Guides/** – tutoriais detalhados sobre estruturas de prompts:

  * Zero-shot
  * Few-shot
  * Chain-of-thought
  * Role prompting
  * Prompt chaining
  * Optimization e avaliação de prompts
* **Notebooks/** – demonstrações em Jupyter com exemplos práticos.
* **scripts/** – utilitários para aplicar templates de prompt ou análise de custos (tokens e inferência).
* **tests/** – experimentos automatizados comparando técnicas (ex.: desempenho vs. custo).
* `LICENSE` – licenciamento de uso.
* `.gitignore`, `README.md` – arquivos padrão de projeto.

## 🎯 Objetivos

1. Consolidar um guia prático de técnicas eficazes de prompt engineering.
2. Automatizar experimentações com LLMs: construção, medição e comparação.
3. Fornecer base para desenvolvedores aperfeiçoarem interações com LLMs.

## 🚀 Começando

### Pré-requisitos

* Python 3.10+
* Dependências em `requirements.txt`, como `openai`, `transformers`, `jupyter`, etc.

```bash
pip install -r requirements.txt
```

### Como utilizar

1. Explore os notebooks em `Notebooks/`:

   ```bash
   jupyter notebook Notebooks/zero_shot.ipynb
   ```
2. Edite e teste /models/prompt\_template.py com sua chave de API e modelo desejado (ex.: GPT‑4, LLaMA, etc.).
3. Execute comparações:

   ```bash
   python scripts/evaluate_prompts.py
   ```
4. Analise os resultados em `results/`, contendo métricas de desempenho e custo.

## 📚 Referências

A engenharia de prompt consiste em estruturar cuidadosamente a entrada a LLMs para melhorar precisão, clareza e/ou eficiência ([researchgate.net][1], [proceedings.neurips.cc][2], [github.com][3]). Técnicas como zero‑shot, few‑shot e chain‑of‑thought são amplamente utilizadas para obter melhores respostas ([researchgate.net][1]).

## 💡 Boas práticas

* Seja claro e específico: defina papel (“act as…”), formato (`bullet list`, `JSON`), estilo (formal, técnico).
* Utilize ilustrações do tipo “role prompting” ou “context injection” para guiar o modelo ([medium.com][4]).
* Balanceie custo vs. performance — prompts longos (ex.: chain-of-thought) podem consumir mais tokens ([researchgate.net][1]).

## 🧠 Contribuições

1. Fork no projeto
2. Crie uma feature ou técnica nova: `git checkout -b feature/my-technique`
3. Adicione tutorial ou testes
4. Commit + pull request
5. Aguarde revisão e merge

## 🔓 Licença

Esse projeto está disponível sob a [MIT License](LICENSE).
