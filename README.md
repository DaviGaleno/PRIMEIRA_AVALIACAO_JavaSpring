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

<img width="600" height="278" alt="{85C1AAF9-B90A-433D-8333-2FCD8A724EB0}" src="https://github.com/user-attachments/assets/074b37a5-4599-450d-aed9-270e1e3eb021" />


### 🔹 Listar Alunos (GET)

<img width="727" height="581" alt="{1A37BFEA-8F05-4C12-9EB4-8678398F478A}" src="https://github.com/user-attachments/assets/1b2330fc-47d4-426e-8db8-2332940b1764" />


### 🔹 Editar Alunos (PUT)

<img width="622" height="237" alt="{BBCBC833-2603-4707-B07B-D0B9E9EEFF9E}" src="https://github.com/user-attachments/assets/8b517247-6c56-4e3c-8858-5468ea622a05" />


### 🔹 Buscar Aluno Por ID (GET)

<img width="669" height="295" alt="{5DADE794-F393-4E32-9D4F-CED46904C74A}" src="https://github.com/user-attachments/assets/28109954-48d3-4543-bed9-1abcca3aedfe" />

### 🔹 Deletar Aluno Por ID (DEL)

<img width="632" height="287" alt="{BF5AF717-C138-477B-AE7D-C5D49D9329E4}" src="https://github.com/user-attachments/assets/7199bf5a-9705-43de-bdeb-c287a162ac8b" />


----------------------------------------------------------------------------------------------------------------------------------------------------------------------




### 🔹 Criar Professor (POST)

<img width="617" height="280" alt="{6468324D-045A-49CE-BF04-0001CB3B3BCF}" src="https://github.com/user-attachments/assets/aea8a4a0-b1fe-4361-bc5d-e3eebf7bd238" />


### 🔹 Listar Professores (GET)

<img width="666" height="314" alt="{C1DBD3C7-C0EC-41BC-AF00-B9BA69649ABE}" src="https://github.com/user-attachments/assets/75e68a3d-300b-4535-9996-e2dddad94ac9" />


### 🔹 Editar Professores (PUT)

<img width="618" height="250" alt="{3C67B37D-EAB2-49EC-9B14-B880F1AFBBEB}" src="https://github.com/user-attachments/assets/34ce6652-2559-4eae-93de-cf41d4bd20b4" />


### 🔹 Buscar Professor Por ID (GET)

<img width="687" height="261" alt="{2C201424-55AC-4E5B-9684-87405AAE4327}" src="https://github.com/user-attachments/assets/13c152a9-1258-4cdc-b1a9-e552fbbe35a7" />


### 🔹 Deletar Professor Por ID (DEL)

<img width="620" height="231" alt="{40765108-139A-42D5-ABE2-BB9071F733AF}" src="https://github.com/user-attachments/assets/f9d3a403-1bee-447e-90a0-4f842533da82" />


----------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🗄️ Banco de Dados (DBeaver)

### 🔹 Tabela Aluno

<img width="549" height="292" alt="{18A1FC81-EEA9-4B31-B944-413873C47DA1}" src="https://github.com/user-attachments/assets/a72ab0bb-9651-4004-b979-2dd38b452ea8" />



### 🔹 Tabela Professor

<img width="550" height="295" alt="{A84D46AA-BCA0-4248-9BB1-BEC88F8F6B5D}" src="https://github.com/user-attachments/assets/91096a00-13e3-42af-b208-7a3eaf3c8961" />



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
