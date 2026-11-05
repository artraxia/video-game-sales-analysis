# Video Game Sales Analysis — EDA & Hypothesis Testing (Python)

![Python](https://img.shields.io/badge/python-3.10%2B-blue) ![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white) ![License: MIT](https://img.shields.io/badge/license-MIT-green)

Projeto do programa **Data Scientist** da TripleTen (aprovado pelo revisor).
Análise exploratória de um histórico de vendas de videogames (`games.csv`, ~16,7 mil títulos até 2016)
para orientar a campanha de 2017 de uma loja online fictícia.

## Pergunta de negócio

Quais plataformas, gêneros e classificações devem receber o investimento de marketing em 2017,
e o comportamento do consumidor difere entre América do Norte, Europa e Japão?

## Etapas

1. **Abertura do arquivo** — tipos, valores ausentes (`critic_score`, `rating`, `user_score`), duplicados.
2. **Preparação** — nomes de colunas em minúsculas, `year_of_release` → `Int64`, `'tbd'` em `user_score` → `NaN`, `rating` → `category`, criação de `total_sales`.
3. **Análise exploratória** — lançamentos por ano, ciclo de vida das plataformas (mediana de duração), janela de análise **2013-2016**, boxplots por plataforma, correlação notas × vendas (PS4), títulos multiplataforma, gêneros.
4. **Perfil regional (AN, UE, JP)** — top 5 plataformas e gêneros por região, efeito da classificação ESRB.
5. **Testes de hipótese** (α = 0,05) — notas de usuários Xbox One vs PC; Action vs Sports.
6. **Conclusão geral** e recomendação para 2017.

## Principais conclusões

- O mercado atingiu o pico em 2008-2009; cada plataforma mantém relevância por ~4 a 6 anos, o que justifica a janela 2013-2016 como base para 2017.
- **PS4** e **Xbox One** lideram o período, enquanto PS3, X360, 3DS e Wii U estão em declínio.
- **Action**, **Shooter** e **Sports** concentram as maiores receitas globais.
- A nota da crítica tem correlação moderada com vendas; a nota dos usuários, praticamente nenhuma.
- **Ocidente** (AN/UE): consoles modernos, ação/tiro, classificação M e E. **Japão**: 3DS lidera, RPG domina, Xbox é irrelevante.
- Xbox One vs PC: não há diferença significativa nas notas de usuários (p ≈ 0,15). Action vs Sports: há diferença.

## Estrutura

```
notebook/games_eda.ipynb   # análise completa, com saídas e gráficos (abre renderizado no GitHub)
data/games.csv             # dataset (não versionado; ver abaixo)
requirements.txt
```

## Como reproduzir

O `games.csv` usado no curso é uma versão do dataset público **Video Game Sales with Ratings** (Kaggle),
com as mesmas colunas (`Name, Platform, Year_of_Release, Genre, NA_sales, EU_sales, JP_sales, Other_sales,
Critic_Score, User_Score, Rating`).

```bash
git clone https://github.com/artraxia/video-game-sales-analysis.git
cd video-game-sales-analysis
pip install -r requirements.txt
# baixe o CSV do Kaggle e salve como data/games.csv
#   https://www.kaggle.com/datasets/rush4ratio/video-game-sales-with-ratings
jupyter notebook notebook/games_eda.ipynb
```

O notebook lê `../data/games.csv` e roda de ponta a ponta (Kernel → Restart & Run All). Pequenas diferenças
numéricas em relação às saídas salvas podem ocorrer se a versão do Kaggle tiver linhas a mais ou a menos.

## Stack

Python · pandas · NumPy · Matplotlib · SciPy
