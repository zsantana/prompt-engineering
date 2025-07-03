# Prompt para Geração de Código Java com Spring Boot

## Objetivo
Gerar um microsserviço em Java utilizando o framework Spring Boot, seguindo as melhores práticas de engenharia de software, arquitetura limpa, padrões de design, e garantindo escalabilidade, manutenibilidade e testabilidade. O código deve ser baseado em uma especificação técnica de critérios de negócio fornecida, com foco em qualidade, segurança e desempenho.

## Instruções para Geração do Código

### 1. **Especificação Técnica**
- A especificação técnica será fornecida pelo usuário e deve conter:
  - Requisitos funcionais e não funcionais.
  - Entidades de negócio (modelos de dados, relacionamentos, etc.).
  - Regras de negócio detalhadas.
  - Casos de uso (ex.: endpoints REST, fluxos de integração, etc.).
  - Requisitos de segurança (autenticação, autorização, etc.).
  - Requisitos de performance e escalabilidade.
- Caso a especificação esteja incompleta, faça perguntas claras para esclarecer os pontos necessários antes de prosseguir.

### 2. **Estrutura do Projeto**
- Utilize o **Spring Boot** na versão estável mais recente.
- Estruture o projeto seguindo a **Arquitetura Limpa** (Clean Architecture) ou **Arquitetura Hexagonal** para desacoplamento e manutenibilidade.
- Organize o código em camadas claras:
  - **Controller**: Endpoints RESTful (APIs REST).
  - **Service**: Lógica de negócio.
  - **Repository**: Acesso a dados (usando Spring Data JPA).
  - **Model/DTO**: Entidades de domínio e objetos de transferência de dados.
  - **Configuration**: Configurações do Spring (beans, profiles, etc.).
  - **Exception**: Tratamento de erros personalizado.
- Use o **Maven** ou **Gradle** como ferramenta de build (preferencialmente Maven, salvo instrução contrária).
- Inclua dependências essenciais, como:
  - `spring-boot-starter-web`
  - `spring-boot-starter-data-jpa`
  - `spring-boot-starter-validation`
  - `spring-boot-starter-test` (para testes)
  - Banco de dados (ex.: H2 para desenvolvimento, PostgreSQL para produção, conforme especificação).
  - Bibliotecas para logging (ex.: SLF4J com Logback).
  - Opcional: `spring-boot-starter-security` para autenticação/autorização, caso necessário.

### 3. **Melhores Práticas de Engenharia de Software**
- **SOLID**: Aplique os princípios SOLID para garantir um código modular e de fácil manutenção.
- **Padrões de Design**:
  - Use o padrão **Repository** para abstrair o acesso a dados.
  - Aplique o padrão **DTO** para transferência de dados entre camadas.
  - Utilize o padrão **Factory** ou **Builder** para criação de objetos complexos, se aplicável.
- **Validação**: Implemente validações com `@Valid` e anotações do Bean Validation (`javax.validation`).
- **Tratamento de Exceções**:
  - Crie uma classe `GlobalExceptionHandler` com `@ControllerAdvice` para centralizar o tratamento de erros.
  - Retorne respostas HTTP consistentes com códigos de status apropriados (ex.: 400, 404, 500).
- **Logging**: Adicione logs significativos em pontos críticos (início/fim de operações, erros, etc.) usando SLF4J.
- **Documentação**:
  - Use **Springdoc OpenAPI** ou **Swagger** para documentar a API automaticamente.
  - Inclua comentários no código (JavaDoc) para métodos públicos e classes principais.
- **Testes**:
  - Crie testes unitários com **JUnit 5** e **Mockito** para a camada de serviço.
  - Crie testes de integração com **Spring Boot Test** para endpoints REST.
  - Cubra pelo menos 80% do código com testes (foco em casos de uso principais e cenários de erro).
- **Segurança**:
  - Se a especificação exigir autenticação, implemente com **Spring Security** (ex.: JWT, OAuth2).
  - Proteja endpoints sensíveis com `@PreAuthorize` ou configurações de segurança.
  - Valide entradas para prevenir ataques como SQL Injection e XSS.
- **Configuração**:
  - Use **application.properties** ou **application.yml** para configurações externas.
  - Suporte múltiplos perfis (ex.: `dev`, `prod`) com o Spring Profiles.
- **Performance**:
  - Implemente paginação para endpoints que retornam listas grandes (`Pageable` com Spring Data).
  - Use cache quando apropriado (ex.: Spring Cache com EhCache ou Redis).
  - Evite consultas N+1 com fetch adequado no JPA.

### 4. **Critérios de Negócio**
- Mapeie as entidades de negócio a partir da especificação fornecida.
- Implemente as regras de negócio na camada de serviço, mantendo a lógica desacoplada do controller e repository.
- Garanta que as APIs REST sigam as convenções RESTful (ex.: uso correto de verbos HTTP, URIs semânticas).
- Se a especificação incluir integrações externas (ex.: APIs de terceiros, filas), use **RestTemplate**, **WebClient**, ou **Spring Cloud** (conforme o caso).

### 5. **Saída do Código**
- Gere o código completo, incluindo:
  - Estrutura de diretórios (ex.: `src/main/java/com/empresa/projeto`).
  - Classes para cada camada (Controller, Service, Repository, Model, DTO, etc.).
  - Arquivos de configuração (ex.: `application.yml`).
  - Testes unitários e de integração.
- Forneça instruções claras para executar o projeto (ex.: `mvn spring-boot:run`).
- Inclua um `README.md` com:
  - Descrição do projeto.
  - Pré-requisitos (ex.: Java 17, Maven).
  - Instruções para configurar o ambiente.
  - Como rodar os testes.
  - Como acessar a documentação da API (ex.: Swagger UI).

### 6. **Exemplo de Especificação Técnica**
Se nenhuma especificação for fornecida, use este exemplo como base para demonstração:
- **Nome do Microsserviço**: `ProductService`
- **Funcionalidade**: Gerenciar produtos (CRUD).
- **Entidades**:
  - `Product`: `id` (Long), `name` (String), `price` (Double), `stock` (Integer).
- **Regras de Negócio**:
  - O preço do produto deve ser maior que zero.
  - O estoque não pode ser negativo.
  - Não é permitido deletar produtos com estoque maior que zero.
- **Endpoints**:
  - `POST /api/products`: Criar produto.
  - `GET /api/products/{id}`: Buscar produto por ID.
  - `GET /api/products`: Listar produtos (com paginação).
  - `PUT /api/products/{id}`: Atualizar produto.
  - `DELETE /api/products/{id}`: Deletar produto.
- **Requisitos Não Funcionais**:
  - Banco de dados: PostgreSQL.
  - Autenticação: JWT.
  - Documentação: Swagger.
  - Testes: Cobertura de 80%+.

### 7. **Formato da Saída**
- Forneça o código em arquivos separados dentro de um único artefato, usando a estrutura de diretórios padrão do Maven.
- Cada arquivo deve ser identificado com seu caminho relativo (ex.: `src/main/java/com/empresa/projeto/controller/ProductController.java`).
- Use o formato Markdown para descrever a estrutura, mas o código-fonte deve estar no formato nativo (Java, YAML, etc.).
- Inclua todos os arquivos necessários para que o projeto seja executável.

### Exemplo de Estrutura de Arquivo
```plaintext
project-root/
├── pom.xml
├── src/
│   ├── main/
│   │   ├── java/com/empresa/projeto/
│   │   │   ├── controller/
│   │   │   ├── service/
│   │   │   ├── repository/
│   │   │   ├── model/
│   │   │   ├── dto/
│   │   │   ├── exception/
│   │   │   ├── config/
│   │   ├── resources/
│   │       ├── application.yml
│   ├── test/
│   │   ├── java/com/empresa/projeto/
│   │   │   ├── controller/
│   │   │   ├── service/
├── README.md
```

### 8. **Validação Final**
- Certifique-se de que o código gerado:
  - Está livre de erros de sintaxe.
  - Segue as convenções de nomenclatura do Java (camelCase, PascalCase, etc.).
  - É compatível com a versão do Java especificada (preferencialmente Java 17 ou superior).
  - Atende a todos os critérios de negócio fornecidos.
  - Inclui tratamento de erros robusto e logs apropriados.
- Valide que o projeto pode ser compilado e executado com as instruções fornecidas.
