# Desafio Full Stack Developer - Python (RPA e Hiperautomação)

# 1\. Introdução

Bem-vindo ao nosso desafio técnico\! Este teste avaliará suas habilidades em automação robótica de processos (RPA) e hiperautomação, combinando desenvolvimento Python com integração de ferramentas low-code/no-code.

## O que esperamos de você:

* Implementação de um robô autônomo para coleta de dados.  
* Criação de um workflow automatizado (parte bônus) para acionamento do robô e integração com APIs do Google (Drive e Sheets).  
* Boas práticas de código e documentação.

# 2\. Detalhes do Desafio

## Parte 1: Automação Web (Obrigatório)

**Parâmetros de Entrada**

* **Nome, CPF ou NIS (obrigatório).**  
* **Filtro de Busca:** "BENEFICIÁRIO DE PROGRAMA SOCIAL" (opcional).

**Objetivo:** Desenvolver um robô em Python para:

1. Acessar o **Portal da Transparência** e navegar até a consulta de "Pessoas Físicas e Jurídicas".  
    ![chrome_S2XSb3O3Qi](https://github.com/user-attachments/assets/580c2da2-8f5c-4546-9d46-a365111786e7)
2. Inserir os parâmetros e realizar a busca.  
   ![chrome_s3kInqbppX](https://github.com/user-attachments/assets/664b728a-733a-4c65-9601-c4fafc66fb7c)
3. Coletar os dados disponíveis na tela " Pessoa Física \- Panorama da relação da pessoa com o Governo Federal".  
   ![chrome_HLYqU5kFHx](https://github.com/user-attachments/assets/193c2888-b9b5-4094-994e-c79c440c7e84)
4. Capturar uma **imagem da tela** como evidência e convertê-la para Base64.  
5. Para cada benefício encontrado (Auxílio Brasil, Auxílio Emergencial, Bolsa Família), acessar os detalhes e coletar as informações.  
   ![chrome_00MI1mmOOF](https://github.com/user-attachments/assets/2ae5f207-9431-4c5a-b529-222da43ec886) 
6. Encerrar a automação e gerar um **JSON** contendo os dados coletados e a imagem Base64.

### Requisitos técnicos:

* Linguagem: Python.  
* Biblioteca recomendada: [**Playwright**](https://playwright.dev/).  
  * Caso opte por outra biblioteca, justifique tecnicamente a escolha e demonstre benefícios.  
* O robô deve funcionar em **modo headless** e permitir execuções simultâneas.

Se a Parte 2 for implementada, o bot deve ser disponibilizado como API online para testes. Caso desenvolva apenas a Parte 1, é um diferencial fornecer a API documentada via Swagger ou OpenAPI.

## Parte 2: Hiperautomação (Bônus)
![image](https://github.com/user-attachments/assets/70d1f110-2b49-4344-b929-7e2179c7ccd0)

**Objetivo:** Criar um workflow automatizado que:

1. Faça requisição via API ao robô desenvolvido na Parte 1\.  
2. Obtenha e armazene automaticamente o arquivo JSON no Google Drive (nome padrão: \[`IDENTIFICADOR_UNICO]_[DATA_HORA].json`).  
3. Atualize um registro centralizado no Google Sheets contendo:  
   * Identificador único da consulta, Nome, CPF, data/hora da consulta.  
   * Link direto para o arquivo JSON respectivo no Drive.

### Ferramentas sugeridas (free tier):

* [Activepieces](https://www.activepieces.com/)  
* [Make.com](http://Make.com)  
* [Zapier](https://zapier.com/)

# 3\. Critérios de Avaliação

| Categoria | Detalhes |
| :---- | :---- |
| Funcionalidade | Execução correta do robô em todos os cenários de teste. |
| Código | Legibilidade, modularização, tratamento de erros. |
| Integrações | Uso eficiente da plataforma de workflow e das APIs do Google (se aplicável). |
| Segurança | Boas práticas (OAuth 2.0, variáveis de ambiente). |
| Documentação | README claro, comentários relevantes. |
| Bônus | Implementação da Parte 2 e/ou diferenciais (notificações, testes, etc.) |

# 4\. Entrega e Processo

1. **Envio:** Finalizando o desafio, encaminhar e-mail para [rh@most.com.br](mailto:rh@most.com.br) com:  
   * Código fonte do robô (Git repository ou arquivo compactado).  
   * Incluir um breve relatório explicando:  
     * Decisões técnicas.  
     * Desafios enfrentados.  
     * Plataforma escolhida para Parte 2 (se aplicável) e motivos.

   

2. **Apresentação**:  
   * Os desafios pré-selecionados terão uma apresentação técnica agendada.  
     * Para uma apresentação clara e objetiva, sugerimos que o candidato organize seu fluxo em duas etapas: primeiro, utilize um PPT para explicar a abordagem, decisões técnicas e desafios enfrentados no desenvolvimento. Em seguida, passe para a demonstração prática, evidenciando o funcionamento da solução e respondendo a perguntas dos avaliadores.  
   * Durante a apresentação, será necessário demonstrar execução simultânea dos bots e o armazenamento correto dos dados.

**Prazo estimado:** 12-20 horas

# 5\. Cenários de Teste

| Cenário | Entrada | Saída Esperada |
| :---- | :---- | :---- |
| Sucesso (CPF) | CPF ou NIS válido | JSON com dados coletados e evidência da tela. |
| Erro (CPF) | CPF ou NIS inexistente | JSON com mensagem de erro: "Não foi possível retornar os dados no tempo de resposta solicitado". |
| Sucesso (Nome) | Nome completo | JSON com dados do primeiro registro equivalente encontrado \+ evidência |
| Erro (Nome) | Nome inexistente | JSON com mensagem de erro: "Foram encontrados 0 resultados para o termo …". |
| Filtrado | Sobrenome \+ filtro social | JSON com dados do primeiro registro equivalente encontrado \+ evidência |

# 6\. Considerações Finais

Este desafio simula um projeto real de hiperautomação.   
Valorizamos:

* Soluções bem arquitetadas.  
* Documentação clara.  
* Justificativas técnicas para decisões.

## **mostQI**

Acesse nosso [Linkedin](https://www.linkedin.com/company/mobile-solution-technology) para mais informações sobre vagas e novidades.

Até breve\! 🤩  


