````markdown
# API de Autenticação e Autorização JWT com Spring Boot

## 📋 Descrição
Esta aplicação Spring Boot implementa uma API de autenticação com emissão e validação de tokens JWT, baseada em **boas práticas de segurança, testabilidade e documentação**.

Ela inclui:
- API RESTful segura
- Autenticação e autorização JWT
- Validação de tokens JWT pelo próprio backend
- Integração com banco H2 (em memória)
- Documentação automática com Swagger
- Testes unitários e de integração
- Testes de carga com JMeter
- Pronto para integração com projetos CRUD

---

## 🚀 Tecnologias Utilizadas
- Java 17
- Spring Boot 3.x
- Spring Security
- OAuth2 Resource Server
- JPA / Hibernate
- H2 Database
- JWT (com Auth0)
- Swagger (Springdoc OpenAPI)
- JUnit 5 e Mockito
- JMeter

---

## 📦 Instalação

### 1. Clone o Repositório
```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
````

### 2. Configure o `application.yml`

O projeto já vem configurado com banco H2 e chave JWT para ambiente de desenvolvimento.

```yml
server:
  port: 8080

spring:
  datasource:
    url: jdbc:h2:mem:testdb;DB_CLOSE_DELAY=-1;DB_CLOSE_ON_EXIT=FALSE
    username: sa
    password:
  h2:
    console:
      enabled: true
      path: /h2-console
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true

jwt:
  secret: umaChaveSecretaMuitoLongaEComplexaParaAssinarTokensJWT
  expiration: 3600000

springdoc:
  swagger-ui:
    path: /swagger-ui.html
```

---

## ▶️ Execução da Aplicação

### Via Spring Boot

```bash
./mvnw spring-boot:run
```

Acesse:

* API: `http://localhost:8080`
* Swagger: `http://localhost:8080/swagger-ui.html`
* H2 Console: `http://localhost:8080/h2-console`

---

## 🔐 Usuários de Teste Criados Automaticamente

| Username | Senha    | Role  |
| -------- | -------- | ----- |
| admin    | 123456   | ADMIN |
| user     | password | USER  |

---

## 📚 Endpoints Principais

### Autenticação

* `POST /auth/login` – Realiza login e retorna token JWT
* `POST /auth/validate` – Valida o token JWT

### Endpoints Protegidos

* `GET /api/hello` – Acesso para usuários autenticados
* `GET /api/admin` – Acesso exclusivo para administradores

### Documentação

* `http://localhost:8080/swagger-ui.html`

---

## ✅ Como Testar

### Testes Unitários e de Integração

Execute:

```bash
./mvnw test
```

Os testes abrangem:

* Login com credenciais válidas
* Login com credenciais inválidas
* Acesso a endpoints protegidos com e sem token

---

## 🔥 Testes de Carga com JMeter

### Como Executar:

* Abra o arquivo `login_stress_test.jmx` no JMeter.
* Configure o número de usuários e ramp-up conforme o cenário desejado.
* Execute o teste para simular carga no endpoint `/auth/login`.

### Arquivo de Teste

Incluído no repositório: `/jmeter-tests/login_stress_test.jmx`

---

## 📦 Deploy

Sugestão de plataformas:

* [Render](https://render.com/)
* [Railway](https://railway.app/)

Inclua variáveis de ambiente para as chaves JWT no ambiente de produção.

### Conteinerização

Você pode criar um Dockerfile para facilitar o deploy.

---

## 🔭 Monitoramento (AV2)

Para a continuidade do projeto:

* Utilize **Spring Boot Actuator** para expor métricas.
* Conecte com **Prometheus** para coleta.
* Crie dashboards no **Grafana** para visualização em tempo real.

---

## 💡 Recomendações

* Integre esta API com seu projeto CRUD da AV1.
* Proteja os endpoints CRUD usando os tokens JWT gerados.
* Implemente roles para restringir ações (ex: deletar apenas com role ADMIN).
