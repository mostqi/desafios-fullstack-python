# Desafio Estágio - Full Stack Developer (Python)

Chegou a hora do desafio! 

Você está prestes a demonstrar suas habilidades em hiperautomação em um cenário realista. 

# Instruções

Você deve clonar este projeto e desenvolvê-lo em seu próprio repositório, em modo privado.

A implementação deve ficar na pasta correspondente ao desafio. Fique à vontade para adicionar qualquer tipo de conteúdo que julgue útil ao projeto como, alterar/acrescentar um README com instruções de como executá-lo, etc.

O projeto deverá ser apresentado à equipe do mostQi, onde serão avaliados o domínio das tecnologias envolvidas e a contextualização do candidato com o problema apresentado. A qualidade do código, versionamento, documentação, entre outros itens também serão avaliados.

# O desafio

Seu desafio é desenvolver um robô autônomo (não assistido) que:

1. Acesse o Portal da Transparência do Governo Federal.  
2. Consulte e extraia dados de beneficiários com base nos parâmetros fornecidos.  
3. Gere um arquivo JSON estruturado com os dados coletados e uma evidência em Base64.

Este desafio avaliará sua capacidade de:  
✅ Implementar automações Web.  
✅ Garantir resiliência com tratamento robusto de erros.  
✅ Organizar e documentar soluções. 

O robô deve ser capaz de executar em modo headless, respeitar timeouts configuráveis e suportar execuções simultâneas.

**Diferenciais (opcionais):**

* Documentar e publicar API para teste via Swagger/OpenAPI.

## Premissas técnicas

O desenvolvimento deve ser realizado utilizando:

* Linguagem: **Python**.  
* Biblioteca principal: [**Playwright**](https://playwright.dev/) para automação web.

## Automação Web

O robô deve executar autonomamente os passos abaixo, a partir do recebimento de requisição com os parâmetros de entrada.

### Parâmetros de Entrada

* **Nome, CPF ou NIS** (obrigatório): Dados para a busca. O CPF deve ser fornecido com ou sem pontuação, e o NIS com ou sem máscara.  
* **Filtro de Busca**: "BENEFICIÁRIO DE PROGRAMA SOCIAL" \- se fornecido, o robô deve aplicar esse filtro na busca.

### Passos

1. Acessar o [Portal da Transparência](https://www.portaltransparencia.gov.br/) e navegar até a tela de consulta de "Pessoas Físicas e Jurídicas".  
   ![chrome_7t8SmOCwGd](https://github.com/user-attachments/assets/5544006a-e8e5-4b57-b14c-39f97d37ab4b)

2. Acessar a tela de “Busca de Pessoa Física”  
   ![chrome_S2XSb3O3Qi](https://github.com/user-attachments/assets/580c2da2-8f5c-4546-9d46-a365111786e7)

3. Inserir os parâmetros de entrada e realizar a busca.  
   ![chrome_s3kInqbppX](https://github.com/user-attachments/assets/664b728a-733a-4c65-9601-c4fafc66fb7c)

4. Em “Resultados” clicar no nome do primeiro resultado apresentado para aceder a tela “Panorama da relação da pessoa com o Governo Federal”  
   ![chrome_UfrdAZp5Wn](https://github.com/user-attachments/assets/f74baf99-7f31-46cf-9f2e-1e480488d1af)

5. Na tela “Pessoa Física” Coletar os dados do primeiro resultado, incluindo nome, CPF, localidade, e detalhes dos benefícios recebidos (Auxílio Brasil, Auxílio Emergencial, Bolsa Família).  
6. Capturar uma imagem da tela como evidência e convertê-la para Base64.  
7. No bloco “Recebimentos de recursos”, se houver, clicar em “Detalhar” (para cada benefício existente).   
   ![chrome_HLYqU5kFHx](https://github.com/user-attachments/assets/193c2888-b9b5-4094-994e-c79c440c7e84)


8. Deve-se acessar a página de detalhe respectiva, coletando os dados, retornando à página anterior e repetindo os passos até que se colete os dados dos tipos de benefícios listados na observação abaixo.  
![chrome_00MI1mmOOF](https://github.com/user-attachments/assets/2ae5f207-9431-4c5a-b529-222da43ec886) 
**Obs**.: Pode haver mais de um bloco de informação, para cada tipo de benefício que o cidadão recebeu. **Neste caso deve-se coletar os dados dos benefícios e seus respectivos detalhes para: Auxílio Brasil, Auxílio Emergencial e Bolsa Família.**  

9. Encerrar o navegador e gerar um JSON com os dados coletados, incluindo a imagem em Base64.

### Detalhes adicionais

* O robô deve funcionar em modo headless.  
* Os passos acima são referências de como um humano executaria tal consulta, sendo o objetivo principal a coleta dos dados e da evidência da página. Caso queira desenvolver através de outro caminho que julgue mais otimizado, fique à vontade.

## Bônus

Será considerado um bônus a disponibilização online do bot como API, permitindo o teste do seu consumo via interface [swagger](https://swagger.io/docs/) ou em outra ferramenta para documentação interativa de API no padrão OpenAPI.

## Cenários de Teste

Os desafios serão apresentados em data e hora combinados previamente por e-mail.

Durante a apresentação deve-se demonstrar a execução de bots, no mínimo para os cenários abaixo. 

**Os parâmetros específicos para cada cenário serão indicados pelos avaliadores durante a apresentação.**

| Cenário | Tipo Parâmetro de Entrada | Resultado Esperado |
| :---- | :---- | :---- |
| 1 \- Sucesso | CPF ou NIS | Json contendo dados coletados e evidência da tela. |
| 2- Exceção | CPF ou NIS | CPF ou NIS não será encontrado na base. Deve-se apresentar como resultado o Json contendo mensagem de erro com descrição  “Não foi possível retornar os dados no tempo de resposta solicitado”. |
| 3 \- Sucesso | Nome completo com paginação nos detalhes | Json contendo dados coletados e evidência da tela. |
| 4- Exceção | Nome completo | O nome completo não será encontrado na base. Deve-se apresentar como resultado o Json contendo mensagem de erro com descrição “Foram encontrados **0** resultados para o termo …” |
| 5 \- Sucesso | Nome (apenas sobrenome) \+ opção do filtro “BENEFICIÁRIO DE PROGRAMA SOCIAL”. Deve-se coletar os dados do primeiro registro do resultado da busca. | Json contendo dados coletados e evidência da tela. |

## Avaliação

* Demonstração do funcionamento do bot, com execução de todos os cenários de teste propostos no desafio.  
* Qualidade do código (legibilidade, modularização, boas práticas).  
* Documentação (README, comentários no código).  
* Versionamento (uso de Git, organização do repositório).

## Considerações Finais

O candidato pode incluir um breve relatório explicando as decisões de desenvolvimento e desafios enfrentados.   
O tempo estimado para conclusão do desafio é de 4-6 horas.

## **mostQI**

Acesse nosso [Linkedin](https://www.linkedin.com/company/mobile-solution-technology/posts/?feedView=all) para mais informações sobre vagas e novidades.

Até breve! 🤩  
