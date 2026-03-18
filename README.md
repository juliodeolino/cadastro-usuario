# Cadastro de Usuário

Este projeto é uma API REST para cadastro, busca, atualização e remoção de usuários, desenvolvida com Spring Boot, Spring Data JPA e banco de dados H2 em memória.

## Tecnologias Utilizadas

- **Java 24**
- **Spring Boot 3.5.11**
- **Spring Data JPA**
- **H2 Database** (em memória)
- **Lombok**
- **Maven**

## Como Rodar o Projeto

1. **Pré-requisitos:**
   - Java 17+ (recomendado Java 24)
   - Maven

2. **Clone o repositório:**
   ```bash
   git clone <url-do-repositorio>
   cd cadastro-usuario-master
   ```

3. **Execute o projeto:**
   ```bash
   mvn spring-boot:run
   ```
   O servidor irá rodar na porta **8081**.

4. **Acesse o H2 Console (opcional):**
   - URL: [http://localhost:8081/h2-console](http://localhost:8081/h2-console)
   - JDBC URL: `jdbc:h2:mem:usuario`
   - Usuário: `sa`
   - Senha: `1234`

## Principais Endpoints

- `POST /usuario` — Cadastra um novo usuário
- `GET /usuario?email={email}` — Busca usuário pelo e-mail
- `DELETE /usuario?email={email}` — Remove usuário pelo e-mail
- `PUT /usuario?id={id}` — Atualiza usuário pelo ID

## Principais Classes e Métodos

### Controller
- **UsuarioController**: expõe os endpoints REST.
  - `salvarUsuario(Usuario usuario)` — Cria usuário
  - `buscarPorEmail(String email)` — Busca usuário
  - `deletarUsuarioPorEmail(String email)` — Remove usuário
  - `atualizarUsuarioPorId(Integer id, Usuario usuario)` — Atualiza usuário

### Service
- **UsuarioService**: lógica de negócio.
  - `savarUsuario(Usuario usuario)` — Salva usuário
  - `buscarUsuarioPorEmail(String email)` — Busca usuário
  - `deletarUsuarioPorEmail(String email)` — Remove usuário
  - `atualizarUsuarioPorId(Integer id, Usuario usuario)` — Atualiza usuário

### Repository
- **UsuarioRepository**: interface para acesso ao banco de dados.
  - `findByEmail(String email)` — Busca por e-mail
  - `deleteByEmail(String email)` — Remove por e-mail

### Entity
- **Usuario**: representa o usuário no banco de dados.
  - Campos: `id`, `email`, `nome`

## Exemplo de Requisição (JSON)

```json
{
  "nome": "João Silva",
  "email": "joao@email.com"
}
```

