# Spring Boot 03

## Verbo em HTTP
- Para mapear URIs iguais para os recursos mas com funções diferentes:
```java
@RequestMapping(value = "/atributo", method = GET)
```
- Pode colocar a notação acima da classe e acima dos métodos põe apenas ```@GetMapping, @PostMapping, etc```
 - Dentro do Post, no parâmetro, como ele não vem pela URL, pega isso do corpo da requisição: ```@RequestBody```
- Melhorando retorno do sucesso do POST: família do código 200
 - Tipo de retorno ```ResponseEntity<ClasseDto>``` e mandar:
```java
URI uri = uriBuilder.path("/topicos/{id}").builderAndExpand(topico.getId()).toUri();
return ResponseEntity.created(uri).body(new TopicoDto(topico));
```
- O importante é devolver o caminho/localização do recurso criado
- Pra fazer requisições pode usar o POSTMAN

## Bean Validation
- Validação de atributos na Controller é feita através de anotações
```java
@NotNull @NotEmpty @Length(min = 5)
```
 - Também pode criar validações
 - Dizer ao Spring pra chamar: ```@Valid``` dentro do parâmetro que tem ```@RequestBody```

## Controller Advice
 - Pra cada método que gerar Exception, posso fazer uma classe que trata (no caso, uma classe que trata todos os erros)
 - Acima da nova classe coloca-se ```@RestControllerAdvice```, acima do método ```handle(...)``` ```@ExceptionHandler(MethodArgumentNotValidException exception)``` e ```@ResponseStatus(code = HttpStatus.BAD_REQUEST)``` para modificar o status code padrão a ser devolvido

## Usando PUT
 - URL dinâmica usa-se com ```@GetMapping("/{id}")``` e pra dizer pro parâmetro do método pegar o que vem da URL passa-se ```(@PathVariable Long id)```
- PUT e PATCH servem para atualização de valores
 - PUT: quer sobrescrever o recurso inteiro
 - PATCH: uma pequena atualização, não quero sobrescrever o recurso inteiro
- Coloca acima do método:
```java
@PutMapping("/{id}")
@Transactional
```
- O Transacional serve pra logo depois do método ele atualizar no banco de dados (commit)
- Retorna ```ResponseEntity.ok(new objetoDto())```

## Usando DELETE
- Método com:
```java
@DeleteMapping("/{id}")
@Transactional
```
- Garante que eles sempre vão rodar dentro de uma transação
- Usa o método do Spring ```deleteById("id")```
- Retornar ```RespondeEntity.ok().build()```

## Erro 404
- No Get, Delete e Put, utilizar como retorno um Optional
- Modificar os ```getOne``` por ```findById```
- Se não retornar nada, faz retorno:
```java
return ResponseEntity.notFound().build();
```
