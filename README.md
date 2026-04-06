# 📚 PRIMEIRA AVALIAÇÃO - API Java Spring Boot

## 📌 Descrição do Projeto

Este projeto consiste no desenvolvimento de uma API REST utilizando o framework Spring Boot, com o objetivo de gerenciar dados de **Alunos** e **Professores**.

A aplicação permite realizar operações de CRUD (Create, Read, Update e Delete), possibilitando o cadastro, consulta, atualização e remoção de registros no banco de dados.

O sistema foi desenvolvido seguindo boas práticas de organização em camadas, separando responsabilidades entre Controller, Service, Repository e Model.

---

## 🛠️ Tecnologias Utilizadas

* Java
* Spring Boot
* Spring Data JPA
* Maven
* Lombok
* Banco de Dados Relacional
* Insomnia (testes de API)
* DBeaver (visualização do banco)

---

## 🧱 Arquitetura do Projeto

O projeto segue o padrão de arquitetura em camadas:

### 📂 Model (Entidade)

Responsável por representar as tabelas do banco de dados.

### 📂 Repository

Responsável pelo acesso aos dados utilizando Spring Data JPA.

### 📂 Service

Contém a lógica de negócio da aplicação.

### 📂 Controller

Responsável por expor os endpoints da API.

---

## 🔍 Detalhamento do Código

### 📁 Entidade Aluno

A classe `Aluno` representa a tabela `aluno` no banco de dados.

```java
@Entity
@Table(name = "aluno")
public class Aluno {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String nomeCompleto;
    private String email;
    private String cpf;
}
```

* `@Entity`: define que a classe é uma entidade JPA
* `@Table`: define o nome da tabela no banco
* `@Id`: chave primária
* `@GeneratedValue`: geração automática do ID

---

### 📁 Repository

```java
public interface AlunoRepository extends JpaRepository<Aluno, Long> {
}
```

* Interface responsável pela comunicação com o banco
* Herda métodos prontos como:

  * `save()`
  * `findAll()`
  * `findById()`
  * `deleteById()`

---

### 📁 Service

Responsável pela lógica da aplicação:

```java
public void criarAluno(Aluno aluno) {
    alunoRepository.save(aluno);
}
```

Outras funções implementadas:

* Listar alunos
* Buscar por ID
* Atualizar dados
* Deletar registros

---

### 📁 Controller

```java
@RestController
@RequestMapping("/alunos")
public class AlunoController {
```

Responsável pelos endpoints da API.

#### 📌 Endpoints disponíveis:

| Método | Rota         | Descrição     |
| ------ | ------------ | ------------- |
| POST   | /alunos      | Criar aluno   |
| GET    | /alunos      | Listar todos  |
| GET    | /alunos/{id} | Buscar por ID |
| PUT    | /alunos/{id} | Atualizar     |
| DELETE | /alunos/{id} | Deletar       |

---

## 👨‍🏫 Entidade Professor

A estrutura de **Professor** segue o mesmo padrão da entidade Aluno, com:

* Model
* Repository
* Service
* Controller

A única diferença está nos nomes das classes e rotas (`/professores`).

---

## 🔗 Endpoints da API

### 📌 Alunos

* GET `/alunos`
* POST `/alunos`
* GET `/alunos/{id}`
* PUT `/alunos/{id}`
* DELETE `/alunos/{id}`

### 📌 Professores

* GET `/professores`
* POST `/professores`
* GET `/professores/{id}`
* PUT `/professores/{id}`
* DELETE `/professores/{id}`

---

## 📸 Testes no Insomnia

### 🔹 Criar Aluno (POST)

<img width="1315" height="641" alt="{C2562B5F-574A-44AA-A9DA-9F0D7E009A8C}" src="https://github.com/user-attachments/assets/9db43c6f-bdda-4ff4-8423-ea01a54948eb" />


### 🔹 Listar Alunos (GET)

<img width="1310" height="602" alt="{CA033DA1-49B7-4E04-B88D-244F7C93B045}" src="https://github.com/user-attachments/assets/eb2c32e0-991b-4c17-be29-dc7452360d47" />

### 🔹 Editar Alunos (PUT)

<img width="649" height="271" alt="{FE17C1D3-2CFC-4D28-A644-57AE4DFA53F6}" src="https://github.com/user-attachments/assets/656a6d50-43de-4174-99b2-98e8e03d91c3" />

### 🔹 Buscar Aluno Por ID (GET)

<img width="669" height="295" alt="{5DADE794-F393-4E32-9D4F-CED46904C74A}" src="https://github.com/user-attachments/assets/28109954-48d3-4543-bed9-1abcca3aedfe" />

### 🔹 Deletar Aluno Por ID (DEL)

<img width="641" height="318" alt="{8A1A3123-819F-42FB-9738-2AF41A8914A4}" src="https://github.com/user-attachments/assets/31cff566-90f8-46be-8448-189149e75e67" />

----------------------------------------------------------------------------------------------------------------------------------------------------------------------




### 🔹 Criar Professor (POST)

<img width="1315" height="628" alt="{DD67D399-55F0-4C86-8EF8-C53664132CCD}" src="https://github.com/user-attachments/assets/73381186-cd8d-445e-8847-1d6a334e3fbd" />

### 🔹 Listar Professores (GET)

<img width="1316" height="632" alt="{DA6A9F5E-AEE5-45B1-B605-29D6FFBB37A4}" src="https://github.com/user-attachments/assets/64f9794a-4778-4971-be4a-1ec571e4abf5" />

### 🔹 Editar Professores (PUT)

<img width="652" height="287" alt="{CA880AE0-A2D6-45FC-966C-79E9F772943C}" src="https://github.com/user-attachments/assets/23f23f79-64a8-4905-9381-49f161da6436" />

### 🔹 Buscar Professor Por ID (GET)

<img width="782" height="282" alt="{38ECF419-B64C-4501-B995-14AA705CC427}" src="https://github.com/user-attachments/assets/e94d8c8c-d8cf-4a65-8a76-760ae49de1b8" />

### 🔹 Deletar Professor Por ID (DEL)

<img width="787" height="296" alt="{AED6AEF5-ED90-4FCC-8593-BE2C6FA4A17D}" src="https://github.com/user-attachments/assets/57e38e67-155b-4b36-a989-c91eb2bcda2f" />

----------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🗄️ Banco de Dados (DBeaver)

### 🔹 Tabela Aluno

<img width="652" height="555" alt="{6D5E4054-3F82-458C-B93E-8CA8759F6B54}" src="https://github.com/user-attachments/assets/f3eb6c11-4b11-490b-90d6-c302ba695b0d" />


### 🔹 Tabela Professor

<img width="632" height="563" alt="{DF588A0A-0229-40CE-977B-FD02651547D5}" src="https://github.com/user-attachments/assets/ea3d5533-90b5-4f35-b260-02b72b0b6a01" />


---

## ▶️ Como Executar o Projeto

1. Clonar o repositório:

```bash
git clone https://github.com/DaviGaleno/PRIMEIRA_AVALIACAO_JavaSpring.git
```

2. Entrar na pasta:

```bash
cd PRIMEIRA_AVALIACAO_JavaSpring
```

3. Executar o projeto:

```bash
./mvnw spring-boot:run
```

4. Acessar a API:

```
http://localhost:8080/alunos
```

---

## 📌 Considerações Finais

O projeto demonstra a aplicação prática de:

* Desenvolvimento de APIs REST com Spring Boot
* Uso do Spring Data JPA
* Organização em arquitetura em camadas
* Integração com banco de dados

Além disso, foram utilizados ferramentas como Insomnia e DBeaver para testes e validação dos dados.

---
