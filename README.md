<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Trabalho Final de LUI

#### Aluno: [Victor Ribeiro](https://github.com/victorgrrtj)
#### Orientador: [Felipe Borges](https://github.com/link_do_github)

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como trabalho de conclusão de curso.

---

### Resumo

<!-- trocar o texto abaixo pelo resumo do trabalho, em português -->

O objetivo deste trabalho é realizar um Web Scraping nas vendas de Iphone 14 realizadas no Mercado Livre.

### 1. Introdução

- Base de Dados: [LINK](https://lista.mercadolivre.com.br/iphone-14#D[A:iphone%2014])
- API: [LINK](https://api.mercadolibre.com/sites/MLB/search?q=Iphone%2014&offset=0)

A base é um website que contém anúncios de vendas. No trabalho estamos filtrando apenas smartphones da marca Apple, modelo Iphone 14.

### 2. Modelagem

A extração dos dados foi realizada utilizando a API do Mercado Livre, através da biblioteca Requests. A API disponibiliza diversos dados dos anúncios (título, preço, se o produto é novo ou usado, etc) e também dados dos vendedores (nome, reputação, qtde de vendas, qtde de avaliações, etc). Então selecionei os dados que achei útil para elaborar um dashboard para realizar uma filtragem personalizada para rápida visualização dos anúncios mais interessantes. Porém um dos desafios foi classificar o modelo dos aparelhos, visto que os anúncios estavam com dados inconsistentes (por exemplo, havia anúncios cujo modelo era totalmente divergente ou até um modelo que não existe). Daí tive a ideia de treinar um classificador de acordo com o título do anúncio. Então eu realizei o treinamento de modelo com os dados de modelo que estavam consistentes para posteriormente classificá-los através dos título.

### 3. Resultados

Os resultados foram satisfatórios visto que disponibilizamos os dados extraídos para um dataframe a fim de analisá-los.

### 4. Conclusões

Somos gratos ao professor Felipe Borges que demonstrou muito bem como elaborar modelos de Web Scraping. Conforme relatado em aula, não existe um modelo perfeito pois há diversas formas de chegar ao mesmo resultado.

---

Matrícula Victor: 211.100.047

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
