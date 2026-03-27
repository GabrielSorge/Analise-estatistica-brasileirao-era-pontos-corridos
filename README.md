# Análise Estatística — Brasileirão Série A (2003–2025)

Análise exploratória de **9.166 partidas** do Campeonato Brasileiro com Python e Pandas, respondendo perguntas reais de desempenho com tratamento de outliers e visualizações.

---

## Perguntas respondidas

| # | Pergunta | Critério |
|---|----------|----------|
| 1 | Quais times têm melhor aproveitamento **como visitante**? | Mín. 100 jogos fora |
| 2 | Quais times têm melhor aproveitamento **como mandante**? | Mín. 100 jogos em casa |
| 3 | Qual a distribuição de vitórias, empates e derrotas por time? | Todos os jogos |
| 4 | Como se saíram os times que jogaram **todas as edições**? | Aproveitamento geral |
| 5 | Quais times têm menos de 100 jogos (outliers)? | Participação reduzida |

---

## Resultados

### 🏆 Top 5 — Melhor aproveitamento como visitante (≥ 100 jogos)

| Time | Jogos Fora | Aproveitamento |
|------|-----------|----------------|
| Palmeiras/SP | 405 | 43,79% |
| Flamengo/RJ | 447 | 42,51% |
| São Paulo/SP | 447 | 40,87% |
| Cruzeiro/MG | 390 | 40,17% |
| Corinthians/SP | 428 | 38,94% |

### 🏠 Top 5 — Melhor aproveitamento como mandante (≥ 100 jogos)

*(gerado ao rodar o notebook)*

---

## Stack

- **Python 3.10+**
- **Pandas** — manipulação e agrupamento de dados
- **Matplotlib / Seaborn** — visualizações
- **Google Colab** — ambiente de execução

---

## Como rodar

```bash
# 1. Clone o repositório
git clone https://github.com/GabrielSorge/analise-aproveitamento-fora-times-brasileirao
cd analise-aproveitamento-fora-times-brasileirao

# 2. Instale as dependências
pip install pandas matplotlib seaborn

# 3. Coloque o dataset na raiz do projeto
# Download: https://www.kaggle.com/datasets/rczekster/matches-brazilian-football-from-2003-to-2019
# Renomeie para: matches-2003-2025.txt

# 4. Abra o notebook
jupyter notebook analise_brasileirao_refatorado.ipynb
```

Ou abra diretamente no Colab clicando no badge no topo do notebook.

---

## Estrutura do projeto

```
├── analise_brasileirao_refatorado.ipynb   # Notebook principal
├── matches-2003-2025.txt                  # Dataset (não versionado)
├── visitante_aproveitamento.png           # Gráfico gerado
├── mandante_aproveitamento.png            # Gráfico gerado
├── distribuicao_resultados.png            # Gráfico gerado
├── todas_edicoes_aproveitamento.png       # Gráfico gerado
└── README.md
```

---

## Dataset

- **Fonte:** [Kaggle — Brazilian Football Matches 2003–2019](https://www.kaggle.com/datasets/rczekster/matches-brazilian-football-from-2003-to-2019)
- **Linhas:** 9.166 partidas
- **Colunas:** DATA, HORA, MANDANTE, PLACAR, VISITANTE
- **Times únicos:** 46
- **Período:** março/2003 – dezembro/2025

---

## Decisões técnicas

**Remoção de outliers:** Times com menos de 100 jogos foram excluídos das análises de aproveitamento. Poucos jogos tornam o percentual estatisticamente instável — um time com 19 jogos e 5 vitórias tem 78,9% de "aproveitamento", o que não é comparável com times que jogaram 400+ partidas.

**Aproveitamento (%):** Calculado como `pontos_conquistados / (jogos × 3) × 100`, seguindo o padrão da CBF.

**Parse do placar:** Implementado com tratamento de erro via `ValueError` para garantir robustez em dados com formatação inconsistente.
