# Desafio Desenvolvedor Front-End

Chegou a hora do desafio! 
Neste desafio você deverá desenvolver **um robô autônomo (não assistido) para  acesso e captura de dados no site indicado, bem como criar um arquivo de saída com os dados coletados**.

## Instruções
Você deve clonar este projeto e desenvolvê-lo em seu próprio repositório, em modo privado.
Para o desenvolvimento do robô deve-se utilizar a linguagem Python e a biblioteca Pyppeteer [Pyppeteer](https://pyppeteer.github.io/pyppeteer/reference.html).


## O desafio

### Rota
O robô deve executar autonomamente os passos abaixo, a partir do recebimento de requisição com os parâmetros de entrada.

#### Parâmetros de entrada
Os parâmetros podem ser de tipos/formatos variados, sendo:
* Timeout em milissegundos (obrigatório).
* Nome, CPF ou NIS (obrigatório).
* Opção de refinamento da busca - “BENEFICIÁRIO DE PROGRAMA SOCIAL”.

#### Passos
1. Acessar o Portal da Transparência do Governo Brasileiro: https://www.portaltransparencia.gov.br/
2. Acessar a tela de consulta “Pessoas físicas”
![2](https://user-images.githubusercontent.com/16540224/190150915-3467a4d0-06d3-4c12-a5d5-3605cc95e4bd.jpg)
3. Inserir os parâmetros de entrada e “buscar”.
![3](https://user-images.githubusercontent.com/16540224/190151164-cbf5f1f2-a191-40f2-a545-6e1999964eae.jpg)
4. Em “Resultados” clicar no nome do primeiro resultado apresentado para aceder a tela “Panorama da relação da pessoa com o Governo Federal”
![4](https://user-images.githubusercontent.com/16540224/190151287-880a48eb-66fd-4bc8-8810-30828ba5d612.jpg)
5. Coletar os dados “Nome”, “CPF”, e “Localidade” na tela “Pessoa Física”.
6. Gerar a imagem a partir do print da tela  “Pessoa Física” como forma de evidência da consulta realizada. 
7. No bloco “Recebimentos de recursos”, se houver, coletar o nome do benefício, o  “Valor Recebido” e clicar em “Detalhar” (para cada benefício existente). 
![7](https://user-images.githubusercontent.com/16540224/190151381-2350c151-aad4-4f9e-a8c9-ca4cd43e2248.jpg)
**Obs.**: Pode haver mais de um bloco de informação, para cada tipo de benefício que o cidadão recebeu. Neste caso deve-se coletar os dados dos benefícios e seus respectivos detalhes para: Auxílio Brasil, Auxílio Emergencial e Bolsa Família. Deve-se acessar a página de detalhe respectiva, coletando os dados, retornando à página anterior e repetindo os passos até que se colete os dados dos tipos de benefícios listados acima.
![7-2](https://user-images.githubusercontent.com/16540224/190151599-6c186cd3-5bfe-4737-b769-e2ee263d7582.jpg)
8. Na tela “Auxílio Emergencial - Parcelas Disponibilizadas ao Beneficiário” coletar os dados de todas as linhas e colunas do grid com informações e valores do benefício em questão, de todas as páginas disponíveis.
![8](https://user-images.githubusercontent.com/16540224/190151646-af30daa3-ecc6-4874-837a-ed480b93f01f.jpg)
9. No caso em que a pessoa consultada tenha recebido mais de um benefício, deve-se coletar os dados, como dito na observação do item 7. Abaixo apresentamos exemplos dos dados para cada tipo de benefício a coletar:
9.1. Exemplo dados do Auxilio Brasil:
![9-1](https://user-images.githubusercontent.com/16540224/190151739-19b2bddd-4248-413c-b812-2b3a20776fea.jpg)
9.2. Exemplo dados do Auxílio Emergencial:
![9-2](https://user-images.githubusercontent.com/16540224/190151805-724aa740-1883-4e68-96ee-a3ac52ed0efc.jpg)
9.3. Exemplo Bolsa Família: Para o Bolsa Família são apresentados dois blocos. Deve-se coletar ambos.
![9-3-1](https://user-images.githubusercontent.com/16540224/190151925-8bfc5546-3de1-4ac3-a596-aa34fa2caf49.jpg)
![9-3-2](https://user-images.githubusercontent.com/16540224/190152041-f1450464-43a4-43af-aafb-c4747803b195.jpg)
10. Encerrar o navegador e gerar um Json com todos os dados coletados, de modo organizado, com os dados globais (nome, CPF, Localidade) e os detalhes aninhados por tipo de Benefício. Neste Json, além dos dados coletados, deve-se constar um atributo “file” contendo a imagem da evidência coletada (esta deve estar no formato Base64).

#### Detalhes de execução
* A solução desenvolvida deve permitir a execução de vários bots em simultâneo.
* O bot deve funcionar no modo headless.
* O bot deve respeitar o tempo de resposta passado como parâmetro de entrada (em milisegundos). Caso este seja atingido sem se concluir a coleta dos dados, deve-se retornar um json contendo a mensagem de erro “Não foi possível retornar os dados no tempo de resposta solicitado”.
* Os passos acima são referências de como um humano executaria tal consulta, sendo o objetivo principal a coleta dos dados e da evidência da página. Caso queira desenvolver através de outro caminho que julgue mais otimizado, fique à vontade.

### Itens desejáveis (bônus)
Será considerado um bônus a disponibilização online do bot como serviço, permitindo o teste do seu consumo via interface [swagger](https://swagger.io/docs/) ou em outra ferramenta para documentação interativa de API no padrão OpenAPI.

### Instruções para a apresentação 
Os desafios serão apresentados em data e hora combinados previamente por e-mail.
Durante a apresentação deve-se demonstrar a execução de bots simultaneamente, no mínimo para os cenários abaixo. Os parâmetros específicos para cada cenário serão indicados durante a apresentação.

| Cenário  | Tipo Parâmetro de Entrada | Resultado Esperado |
| ------------- | ------------- | ------------- |
| 1 - Sucesso  | CPF ou NIS  | Json contendo dados coletados e evidência da tela. |
| 2 - Exceção  | CPF ou NIS | CPF ou NIS não será encontrado na base. Deve-se apresentar como resultado o Json contendo mensagem de erro com descrição  “Não foi possível retornar os dados no tempo de resposta solicitado”.  |
| 3 - Sucesso  | Nome completo com paginação nos detalhes  | Json contendo dados coletados e evidência da tela. |
| 4 - Exceção  | Nome completo  | O nome completo não será encontrado na base. Deve-se apresentar como resultado o Json contendo mensagem de erro com descrição “Foram encontrados 0 resultados para o termo …” |
| 5 - Sucesso  | Nome (apenas sobrenome) + opção do filtro “BENEFICIÁRIO DE PROGRAMA SOCIAL”. Deve-se coletar os dados do primeiro registro do resultado da busca.  | Json contendo dados coletados e evidência da tela. |

Serão avaliados todo o processo executado pelo bot, decisões de desenvolvimento e não apenas o alcance do resultado.
