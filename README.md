<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Trabalho Final de LUI

#### Aluno: [Victor Ribeiro](https://github.com/victorgrrtj)
#### Orientador: [Felipe Borges](https://github.com/link_do_github)

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como trabalho de conclusão de curso.

---

### Resumo

<!-- trocar o texto abaixo pelo resumo do trabalho, em português -->

O objetivo deste trabalho é realizar um Web Scraping nas vendas de Iphone 14 realizadas no Mercado Livre para construção de um painel Power BI para criação de indicadores e tabela para seleção dos anúncios.

### 1. Introdução

- [Base de Dados](https://lista.mercadolivre.com.br/iphone-14#D[A:iphone%2014])
- [API](https://api.mercadolibre.com/sites/MLB/search?q=Iphone%2014&offset=0)
- [Painel](https://app.powerbi.com/view?r=eyJrIjoiNDkyOGZlODAtNThmMy00MjYxLWI1ZWQtZGQ4YTczM2U0N2FkIiwidCI6ImYxYWU0NGY0LWUzYmEtNDViMC05ZGJhLWNkNGU1ZTZlMGZlNCJ9)

A base é um website que contém anúncios de vendas. No trabalho estamos filtrando apenas smartphones da marca Apple, modelo Iphone 14.

### 2. Modelagem

A extração dos dados foi realizada utilizando a API do Mercado Livre, através da biblioteca Requests. A API disponibiliza diversos dados dos anúncios (título, preço, se o produto é novo ou usado, etc) e também dados dos vendedores (nome, reputação, qtde de vendas, qtde de avaliações, etc). Então selecionei os dados que achei útil para elaborar um dashboard para realizar uma filtragem personalizada para rápida visualização dos anúncios mais interessantes. 

Tive que realizar uma série de limpeza de dados visto que a API estava trazendo dados de aparelhos que não eram objeto da análise (modelos anteriores ao Iphone 14).

Um dos desafios foi classificar o modelo dos aparelhos, visto que os anúncios estavam com dados inconsistentes (por exemplo, havia anúncios cujo modelo era totalmente divergente ou até um modelo que não existe). Daí tive a ideia de treinar um classificador de acordo com o título do anúncio. Então eu realizei o treinamento de modelo com os dados de modelo que estavam consistentes para posteriormente classificá-los através dos título. Para isso utilizei uma matriz esparsa (CountVectorizer) dos títulos dos anúncios como entrada, o modelo do aparelho como saída e RandomForest como classificador. O resultado foi satisfatório, pois obtive 100% de acurácia na base de teste. Daí exportei o classificador (model.joblib) e a matriz esparsa (cv.joblib) para utilizar na classificação do modelo. O notebook trabalho_final_predicao.ipynb possui o treinamento do classificador e o notebook trabalho_final_treino.ipynb possui a utilização do classificador e ingestão de dados em um banco de dados.

Um desafio parecido foi criar uma classificação pelo armazenamento do aparelho (128Gb, 256Gb, 512Gb ou 1Tb). Para isso utilizei a técnica de regex para extração do título do anúncio.

Por fim gravei os dados em um banco de dados SQL Server para posterior acesso através do Power BI. Construií o dashboard de um modo personalizado, onde poderia realizar as consultas dos aparelhos e melhor filtrar os modelos dos aparelhos anunciados.

### 3. Resultados

O [dashboard](https://app.powerbi.com/view?r=eyJrIjoiNDkyOGZlODAtNThmMy00MjYxLWI1ZWQtZGQ4YTczM2U0N2FkIiwidCI6ImYxYWU0NGY0LWUzYmEtNDViMC05ZGJhLWNkNGU1ZTZlMGZlNCJ9) ficou bem elaborado com os dados extraídos da API do Mercado Livre, possibilitando uma informação mais rápida e objetiva na busca de um aparelho Iphone 14.

### 4. Conclusões

O recurso de extração de dados utilizando API e/ou Web Scraping é bem útil para automatizar fluxo de dados e realizar análises. 

---

Matrícula Victor: 211.100.047

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
