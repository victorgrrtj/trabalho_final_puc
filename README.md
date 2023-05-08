<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Trabalho Final de LUI

#### Aluno: [Victor Ribeiro](https://github.com/victorgrrtj)
#### Aluna: [Thaís Guarize](https://github.com/victorgrrtj)
#### Orientador: [Felipe Borges](https://github.com/link_do_github)

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "LUI - Localização e Uso da Informação".

[Trabalho_LUI.ipynb](https://github.com/victorgrrtj/lui_work/blob/main/Trabalho_LUI.ipynb)

---

### Resumo

<!-- trocar o texto abaixo pelo resumo do trabalho, em português -->

O objetivo deste trabalho é realizar um Web Scraping a fim de gerar um dataframe contendo informações de um site de imóveis. 

### Abstract <!-- Opcional! Caso não aplicável, remover esta seção -->

<!-- trocar o texto abaixo pelo resumo do trabalho, em inglês -->

The work's purpose is to web scrap a website based on properties' rent and sell in order to generate a dataframe.

### 1. Introdução

- Base de Dados: [LINK](https://www.dfimoveis.com.br/aluguel/df/todos/imoveis)

A base é um website que contém dados sobre aluguel e venda de imóveis. O objetivo é extrair os mais relevantes a fim de incluí-los em um dataframe.

### 2. Modelagem

A extração dos dados foi realizada utilizando as bibliotecas BeautifulSoup e Requests. Para tal, criamos uma lista contendo as páginas das quais os dados seriam extraídos e utilizamos as tags de cada imóvel para extrair o título, o valor total, valor por m2, área, descrição, tipo de imóvel, objetivo (aluguel ou venda), quantidade e tipo de cômodos. Utilizamos as bibliotecas Time e Random para definir uma pausa entre as requisições do site para não sobrecarregá-lo e/ou termos nosso acesso bloqueado. Após a extração, criamos um dicionário contendo os dados de cada imóvel publicado no site e geramos para um arquivo json. Para mostrar o resultado, passamos os dados para um dataframe e realizamos uma filtragem e uma ordenação.

### 3. Resultados

Os resultados foram satisfatórios visto que disponibilizamos os dados extraídos para um dataframe a fim de analisá-los.

### 4. Conclusões

Somos gratos ao professor Felipe Borges que demonstrou muito bem como elaborar modelos de Web Scraping. Conforme relatado em aula, não existe um modelo perfeito pois há diversas formas de chegar ao mesmo resultado.

---

Matrícula Victor: 211.100.047

Matrícula Thaís: 211.100.376

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
