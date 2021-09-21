# Anotações realizadas durante o curso: "Introdução aos Conceitos de API e Clean Architecture"

Link do curso: [https://web.digitalinnovation.one/course/introducao-aos-conceitos-de-api-e-clean-architecture/learning/577d2f85-ec84-4204-a4b6-249a9ea08b18?back=/browse](https://web.digitalinnovation.one/course/introducao-aos-conceitos-de-api-e-clean-architecture/learning/577d2f85-ec84-4204-a4b6-249a9ea08b18?back=/browse)

## *REST* - *RE*presentational *S*tate *T*ransfer

* REST é um "estilo" de implementação de API'S.
* Interoperável, isto é, é capaz de "conversar" com outras tecnologias.
* Agnóstico, então independe de linguagem específica.

### Características

* Uniform Interface - Recurso por onde é feito o ponto de entrada para a comunicação do cliente com o servidor.
* Client-Server - Independência entre o Cliente e o Servidor.
* Stateless - O servidor não armazena estados/sessões. Isso ajuda na escalabilidade horizontal!
* Cache - Funcionalidade que permite a necessidade de buscar no servidor alguns dados.
* Sistema em camadas - Permite a distribuição dos "recursos", isto é, a API pode estar em determinado provedor, o armazenamento em outro e o autenticador em um terceiro.
* Código sobre demanda - É o envio de um código executável pelo servidor para o cliente, como os jogos em flash ou JS.

### Principais verbos HTTP

* GET - Recuperar uma informação.
* POST - Criar recursos. (Ex: Criar um login)
* PUT - Atualizar um objeto como um todo.
* PATCH - Atualizar um objeto parcialmente. (Ex: Alterar apenas a senha de um login)
* DELETE - Remove logicamente um recurso.

### Códigos HTTP

* 1XX - Informações;
* 2XX - Sucesso na requisição;
* 3XX - Erro no lado do cliente;
* 4XX - Erro no lado do servidor.
  
Site com mais detalhes sobre tais códigos: [https://httpstatuses.com](https://httpstatuses.com)

### Idempotência

* Um método idempotente é aquele que o retorno é sempre o mesmo apesar do número de vezes que é executado.

### OBS: O problema do N+1 ocorre quando é necessário realizar mais de uma requisição no servidor para montar um componente

### Conceitos para se aprofundar

* Swagger;
* PostegreSQL;
* Postman;
* Clean Architecture;
* TDD.
  