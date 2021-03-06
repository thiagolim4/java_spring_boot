# Spring Boot 01

- Projeto Web usando Spring Boot
- Usando o Spring initializr, ele já gera tudo que necessita de início do projeto (pom, dependências, etc): ```start.spring.io```
 - Maven Project > Java > Versão Estável
 - Group: br.com.nomeEmpresa
 - Artifact: nomeProjeto
 - Option: Web
- Para executar o projeto é só executar a classe do ```main()``` pois ele já tem o Tomcat embutido
- Criar classe Controller:
```java
@Controller
```
- Mapeando o endereço pro Spring encontrar a classe:
```java
@RequestMapping("/")
```
- Por padrão, o Spring considera que o retorno do método é o nome da página que ele deve carregar, mas ao utilizar a anotação ```@ResponseBody```, indicamos que o retorno do método deve ser serializado e devolvido no corpo da resposta:
```java
@ResponseBody
```
- Por conta dessa notação, adicionamos a notação ```@RestController``` acima da classe para não ter que ficar usando isso em todo método
- Com o Módulo DevTools não precisa ficar reiniciando a aplicação a cada mudança
```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-devtools</artifactId>
  <scope>runtime</scope>
</dependency>
```
- Com o padrão DTO, cria-se uma classe com os valores específicos que eu quero retornar com um endpoint
 - Como vai usar JPA não é bom nos métodos de endpoint retornar listas completas dos objetos, por isso o uso dessas classes
- Nesse tipo de classe eu coloco apenas getters

## REST
- Tipo de arquitetura para sistemas distribuídos
- Ela manipula recursos, e cada recurso é acessado por uma URI (identificador de recurso)
- Pra facilitar a manipulação tem-se os verbos HTTP
 - GET, POST, PUT, DELETE
- A API recebe e devolve representações de recursos (que são feitas pelos media types = JSON, XML)
- Tem comunicação Stateless, não guardam estado da comunicação (sem uso de sessão)
- Spring, por padrão, converte os dados no formato JSON, utilizando a biblioteca ```Jackson```;
