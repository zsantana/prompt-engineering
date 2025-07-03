# Prompt para Geração de Microsserviço Spring Boot

## Contexto
Você é um arquiteto de software especializado em Java e Spring Boot. Sua tarefa é gerar código para um microsserviço baseado em uma especificação técnica de critérios de negócio, aplicando as melhores práticas de engenharia de software.

## Especificação Técnica
**[INSERIR AQUI A ESPECIFICAÇÃO TÉCNICA COMPLETA]**

Incluir:
- Domínio do negócio
- Casos de uso principais
- Regras de negócio
- Entidades e relacionamentos
- APIs necessárias
- Requisitos não funcionais
- Integrações externas

## Diretrizes de Implementação

### 1. Arquitetura e Design
- **Arquitetura Hexagonal (Clean Architecture)**: Separar claramente as camadas de domínio, aplicação, infraestrutura e apresentação
- **Domain-Driven Design (DDD)**: Modelar o código baseado no domínio do negócio
- **SOLID Principles**: Aplicar todos os princípios SOLID
- **Separation of Concerns**: Cada classe deve ter uma única responsabilidade

### 2. Estrutura do Projeto
```
src/main/java/com/empresa/microsservico/
├── domain/
│   ├── entities/
│   ├── valueobjects/
│   ├── repositories/
│   └── services/
├── application/
│   ├── usecases/
│   ├── dto/
│   └── ports/
├── infrastructure/
│   ├── persistence/
│   ├── messaging/
│   ├── external/
│   └── config/
└── presentation/
    ├── controllers/
    ├── handlers/
    └── mappers/
```

### 3. Padrões de Código Obrigatórios

#### Domain Layer
- **Entities**: Implementar com validações de negócio
- **Value Objects**: Usar para conceitos imutáveis
- **Domain Services**: Para lógicas que não pertencem a uma entidade específica
- **Repository Interfaces**: Definir contratos no domínio

#### Application Layer
- **Use Cases**: Implementar cada caso de uso como uma classe separada
- **DTOs**: Para transferência de dados entre camadas
- **Ports**: Interfaces para comunicação com infraestrutura

#### Infrastructure Layer
- **Repository Implementations**: Implementar usando Spring Data JPA
- **Configuration**: Beans de configuração bem organizados
- **External Services**: Clientes para APIs externas

#### Presentation Layer
- **Controllers**: Endpoints REST bem definidos
- **Exception Handlers**: Tratamento global de exceções
- **Mappers**: Conversão entre DTOs e entities

### 4. Práticas de Qualidade

#### Tratamento de Erros
- Criar exceções customizadas por domínio
- Implementar GlobalExceptionHandler
- Retornar códigos HTTP apropriados
- Logs estruturados com níveis adequados

#### Validações
- Bean Validation (JSR-303) em DTOs
- Validações de negócio no domínio
- Sanitização de entrada

#### Segurança
- Spring Security configurado
- Autenticação e autorização
- Validação de entrada
- Proteção contra vulnerabilidades comuns

#### Observabilidade
- Logs estruturados (JSON)
- Métricas com Micrometer
- Health checks
- Distributed tracing

### 5. Dependências Obrigatórias

```xml
<!-- Spring Boot Starters -->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-validation</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-security</artifactId>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>

<!-- Observabilidade -->
<dependency>
    <groupId>io.micrometer</groupId>
    <artifactId>micrometer-registry-prometheus</artifactId>
</dependency>

<!-- Documentação -->
<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-starter-webmvc-ui</artifactId>
</dependency>

<!-- Utilitários -->
<dependency>
    <groupId>org.mapstruct</groupId>
    <artifactId>mapstruct</artifactId>
</dependency>
<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
</dependency>
```

### 6. Configurações Essenciais

#### application.yml
```yaml
server:
  port: 8080
  error:
    include-message: always
    include-binding-errors: always

spring:
  application:
    name: nome-do-microsservico
  datasource:
    url: jdbc:h2:mem:testdb
    driver-class-name: org.h2.Driver
  jpa:
    hibernate:
      ddl-auto: validate
    show-sql: false
  security:
    oauth2:
      resourceserver:
        jwt:
          issuer-uri: ${JWT_ISSUER_URI:http://localhost:8080}

management:
  endpoints:
    web:
      exposure:
        include: health,info,metrics,prometheus
  endpoint:
    health:
      show-details: always
```

### 7. Padrões de Código

#### Nomenclatura
- Classes: PascalCase
- Métodos/variáveis: camelCase
- Constantes: UPPER_SNAKE_CASE
- Packages: lowercase com separadores

#### Documentação
- JavaDoc em classes públicas
- Comentários explicativos em lógicas complexas
- README.md com instruções de uso

#### Testes
- Testes unitários para todas as classes de domínio
- Testes de integração para repositories
- Testes de contrato para controllers
- Cobertura mínima de 80%

### 8. Implementação Obrigatória

Para cada especificação técnica, implemente:

1. **Todas as entities** com validações de negócio
2. **Todos os casos de uso** como classes separadas
3. **Controllers REST** com documentação OpenAPI
4. **Tratamento de exceções** customizado
5. **Configurações** de segurança e observabilidade
6. **Testes** unitários e de integração
7. **Dockerfile** para containerização
8. **docker-compose.yml** para ambiente local

### 9. Entregáveis Esperados

1. **Código fonte completo** seguindo a estrutura definida
2. **Arquivo pom.xml** com todas as dependências
3. **Configurações** (application.yml, application-prod.yml)
4. **Documentação** (README.md, API docs)
5. **Testes** (unitários e integração)
6. **Docker** (Dockerfile, docker-compose.yml)
7. **Scripts** de banco de dados (se necessário)

### 10. Checklist de Qualidade

Antes de finalizar, verifique:
- [ ] Arquitetura hexagonal implementada
- [ ] Princípios SOLID aplicados
- [ ] Tratamento de erros robusto
- [ ] Validações em todas as camadas
- [ ] Segurança configurada
- [ ] Observabilidade implementada
- [ ] Testes com boa cobertura
- [ ] Documentação completa
- [ ] Dockerfile funcionando
- [ ] Logs estruturados
- [ ] Performance otimizada

## Instruções Finais

1. Analise cuidadosamente a especificação técnica fornecida
2. Identifique todos os requisitos funcionais e não funcionais
3. Implemente seguindo rigorosamente as diretrizes acima
4. Teste localmente antes de entregar
5. Documente decisões arquiteturais importantes
6. Sugira melhorias ou otimizações quando apropriado

**Lembre-se**: O código deve ser production-ready, seguindo as melhores práticas de engenharia de software e sendo facilmente mantível por outros desenvolvedores.
