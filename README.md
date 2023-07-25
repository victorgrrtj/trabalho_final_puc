<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Trabalho Final de LUI - Localização e Uso da Informação

#### Aluno: [Victor Ribeiro](https://github.com/victorgrrtj)
#### Orientador: [Felipe Borges](https://github.com/link_do_github)

---

Script apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como trabalho de conclusão de curso.

---

## Resumo

<!-- trocar o texto abaixo pelo resumo do trabalho, em português -->

O objetivo deste trabalho é realizar um Web Scraping nas vendas de Iphone 14 realizadas no Mercado Livre para construção de um painel Power BI para criação de indicadores e tabela para seleção dos anúncios.

## 1. Introdução

- [Base de Dados](https://lista.mercadolivre.com.br/iphone-14#D[A:iphone%2014])
- [API](https://api.mercadolibre.com/sites/MLB/search?q=Iphone%2014&offset=0)
- [Painel](https://app.powerbi.com/view?r=eyJrIjoiNDkyOGZlODAtNThmMy00MjYxLWI1ZWQtZGQ4YTczM2U0N2FkIiwidCI6ImYxYWU0NGY0LWUzYmEtNDViMC05ZGJhLWNkNGU1ZTZlMGZlNCJ9)

A base é um website que contém anúncios de vendas. No trabalho estamos filtrando apenas smartphones da marca Apple, modelo Iphone 14.

## 2. Modelagem

### 2.1 - Scraping:
**Objetivo:** Obter dado de anúncios de Iphone 14 do site [Mercado Livre](https://lista.mercadolivre.com.br/iphone-14#D%5BA:iphone%2014%5D).

**Arquivo:** [trabalho_final_treino.ipynb](https://github.com/victorgrrtj/trabalho_final_puc/blob/main/trabalho_final_treino.ipynb)

**Como foi realizado:**
A extração dos dados foi realizada utilizando a [API do Mercado Livre](https://api.mercadolibre.com/sites/MLB/search?q=Iphone%2014&offset=0), através da biblioteca [Requests](https://requests.readthedocs.io/en/latest/). A API disponibiliza diversos dados dos anúncios (título, preço, se o produto é novo ou usado, etc) e também dados dos vendedores (nome, reputação, quantidade de vendas e de avaliações, entre outros). Então selecionei os dados que achei útil para elaborar um dashboard personalizado para rápida visualização dos anúncios mais interessantes.
Tive que realizar uma série de limpeza de dados visto que a API estava trazendo dados de aparelhos que não eram objeto da análise (modelos anteriores ao Iphone 14).

### 2.2 - Modelo de Classificação:
**Objetivo:** Classificar modelos de aparelhos de acordo com o título.

**Arquivo:** [trabalho_final_treino.ipynb](https://github.com/victorgrrtj/trabalho_final_puc/blob/main/trabalho_final_treino.ipynb)

**Motivo:** Fonte de dados de modelos dos aparelhos parcialmente inconsistente.

**Como foi realizado:**
Realizei o treinamento de modelo com os dados de modelo que estavam consistentes para posteriormente classificá-los através dos título. Para isso realizei a limpeza dos dados, balanceamento da base dados ([OverSampling](https://imbalanced-learn.org/stable/references/generated/imblearn.over_sampling.RandomOverSampler.html#imblearn.over_sampling.RandomOverSampler)) e utilizei uma matriz esparsa ([CountVectorizer](https://scikit-learn.org/stable/modules/generated/sklearn.feature_extraction.text.CountVectorizer.html)) dos títulos dos anúncios como entrada, o modelo do aparelho como saída e [RandomForest](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html) como classificador. O resultado foi satisfatório, pois obtivemos 100% de acurácia na base de teste. Daí exportei o classificador ([model.joblib](https://github.com/victorgrrtj/trabalho_final_puc/blob/main/model.joblib)) e a matriz esparsa ([cv.joblib](https://github.com/victorgrrtj/trabalho_final_puc/blob/main/cv.joblib)) para utilizar na classificação do modelo.

### 2.3 - Uso do Modelo :
**Objetivo:** Realizar carga de dados em um banco de dados para alimentar painel do Power BI.

**Arquivo:** [trabalho_final_predicao.ipynb](https://github.com/victorgrrtj/trabalho_final_puc/blob/main/trabalho_final_predicao.ipynb)
 
**Motivo:** Visto que os dados de aparelhos estão inconsistentes, é necessário criar uma pipeline para classificar os modelos dos aparelhos de acordo com o modelo treinado.

**Como foi realizado:**
Realizei o upload do classificador (model.joblib) e da matriz esparsa (cv.joblib) para classificar os modelos dos aparelhos corretamente. Utilizo novamente a API do Mercado Livre para obter os dados, formatá-los, gerar indicadores e realizar carga de dados em banco de dados SQL Server.

### 2.4 - Elaboração de Painel:
**Objetivo:** Criar Painel Power BI personalizado para rápida análise de oportunidades de compras de aparelhos.

**Como foi realizado:** A montagem do painel contou com uso de filtros, gráficos, indicadores e tabela. Visto que foi utilizado uma base dados, o processo ficou automático. Atualizando a base de dados, o Painel é também atualizado.

## 3. Resultados

O [dashboard](https://app.powerbi.com/view?r=eyJrIjoiNDkyOGZlODAtNThmMy00MjYxLWI1ZWQtZGQ4YTczM2U0N2FkIiwidCI6ImYxYWU0NGY0LWUzYmEtNDViMC05ZGJhLWNkNGU1ZTZlMGZlNCJ9) ficou bem elaborado com os dados extraídos da API do Mercado Livre, possibilitando uma informação mais rápida e objetiva na busca de um aparelho Iphone 14, visto que também possui o link direto para o anúncio.

## 4. Conclusões

O recurso de extração de dados utilizando API e/ou Web Scraping é bem útil para automatizar fluxo de dados, construir análises de dados e modelos de aprendizagem de máquina.

---

Matrícula Victor: 211.100.047

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
