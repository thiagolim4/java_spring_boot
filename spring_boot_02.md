# Spring Boot 02

## Spring Data

- Dependência no POM do Hibernate como implementação da JPA
- Dependências do banco de dados (h2, banco em memória)
- Configurar info's do banco de dados e do JPA no ```application.properties```
 - Driver de acesso
 - URL de acesso
 - Usuário
 - Senha
 - Hibernate: dialeto do banco de dados
 - Opção para criar automaticamente e sempre que tiver uma nova propriedade na classe ele puxa e atualiza o banco automático
 - Habilitar interface gráfica de gerenciamento pro h2
 - Endereço para acessar a interface

## Classes do Spring
 - Usar notação ```@Entity```
 - Exige que tenha o construtor default (sem parâmetros)
 - Em cima do atributo que representa a chave primária, deve-se ter ```@Id``` e definir um ```@GeneratedValue```
 - Para dado do tipo Enum, usa ```@Enumerated``` e define o tipo
 - Definir cardinalidade de certos atributos com ```@ManyToOne``` ou ```@OneToMany```
 - No diretório ```src/main/resources``` pode deixar um ```data.sql``` com comandos sql que o Spring automaticamente executa esse script no banco

## Padrão Repository
- Ao invés de usar o padrão DAO, em que cada classe é semelhante na parte do CRUD, usa-se o padrão Repository do Spring Data
  - Criar uma interface que herda de outra do Spring Data que já implementa algumas funções
  - Não precisa colocar anotação alguma nela, só preenche o generics com a classe e o tipo do atributo da chave primária
  - Depois tem que injetar ele no Controller com ```@Autowired```

## Filtro

- Receber parâmetros no Controller para filtrar a listagem, posso passar pela URL
- Cria o método específico na interface, e não precisa colocar a implementação, o Spring faz automaticamente
 - Usa ```findByEntidadeAtributo()```, para evitar ambiguidades pode usar ```_```
 - Pode usar notação com JPQL ```@Query("SELECT atrib FROM tabela WHERE...")``` para substituir algum método que quer mudar o nome, e colocar ```@Param("parametro")``` dentro do argumento do método
