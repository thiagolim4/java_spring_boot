# Java Spring Boot

- Projeto Web usando Spring Boot
- Usando o Spring initializr, ele já gera tudo que necessita de início do projeto (pom, dependências, etc): ```start.spring.io```
 - Maven Project > Java > Versão Estável
 - Group: br.com.nomeEmpresa
 - Artifact: nomeProjeto
 - Option: Web
- Para executar o projeto é só executar a classe do ```main()``` pois ele já tem o Tomcat embutido
- Criar classe Controler:
```java
@Controller
```
- Mapeando o endereço pro String encontrar a classe:
```java
@RequestMapping("/")
```
- Soltar o retorno do método direto no navegador (senão o Spring vai considerar que nosso retorno é uma página e vai procurar isso dentro do projeto):
```java
@ResponseBody
```
- Por padrão, o Spring considera que o retorno do método é o nome da página que ele deve carregar, mas ao utilizar a anotação ```@ResponseBody```, indicamos que o retorno do método deve ser serializado e devolvido no corpo da resposta
