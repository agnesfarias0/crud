# crud
Criação de um sistema CRUD utilizando Java Spring Boot e MySQL, seguindo a vídeo aula do canal Build &amp; Run no Youtube.

Passo 1 - Ir em start.spring.io e gerar projeto com dependências Spring Web, Spring Data JPA, MySql Driver,  Spring Data JDBC e Lombok.

Passo 2 - Adicionar arquivo compose.yml com seguinte conteúdo: 

services:
  mysql:
    container_name: 'guide-mysql'
    image: 'mysql:latest'
    environment:
      - 'MYSQL_DATABASE=mydatabase'
      - 'MYSQL_PASSWORD=secret'
      - 'MYSQL_ROOT_PASSWORD=verysecret'
      - 'MYSQL_USER=myuser'
    ports:
      - '3306:3306'

Passo 3 - No terminal, dentro do diretório do programa, rodar docker compose up.

Passo 4 - Adicionar o seguinte conteúdo no application.properties:

spring.jpa.hibernate.ddl-auto=update
spring.datasource.url=jdbc:mysql://localhost:3306/mydatabase
spring.datasource.username=myuser
spring.datasource.password=secret
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.show-sql=true


Passo 5 - Criar e configurar entidades e outros arquivos, etc.

------------------------------------------------------------------------

  Notas:

Entity (anotação @Entity) -> Tipo de classe. contém anotações adicionais com atributos da tabela, como @Id, @Column.

DTO (Data Transfer Object) -> Tipo de classe para construir objetos. Transporta dados entre camada de Controle e camada de Serviço. Servem para reduzir número de chamadas ao banco de dados. Encapsula dados recebidos ou enviados ao cliente.

Controller (@RestController ou @Controller) -> Tipo de classe para lidar com as requisições HTTP. Recebem as solicitações, invocam métodos apropriados nos serviços e retornam as respostas. Usa-se @RequestMapping para definir a url padrão.

Repository -> Tipo de Interface que abstrai a lógica de acesso a dados. Intaração com banco de dados usando métodos de consulta (findById, save, delete, etc). Extendemos a interface JpaRepository que fornece a implementação básica desses métodos.

Service (anotação @Service) -> tipo de classe que chama repositórios para obter/manipular dados. Separa lógica de negócios da lógica de apresentação (controller).

------------------------------------------------------------------------

Referências: 

[https://docs.spring.io/spring-boot/index.html](https://spring.io/guides/gs/accessing-data-mysql)

https://youtu.be/Tnl4YnB6E54
