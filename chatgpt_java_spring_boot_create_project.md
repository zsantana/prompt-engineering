
# 🧩 Prompt para Geração de Microsserviço Java com Spring Boot

## 🎯 Objetivo

Gerar um microsserviço em **Java** utilizando **Spring Boot 3.x**, baseado em uma **especificação técnica de critérios de negócio**, aplicando as **melhores práticas de engenharia de software** e os **padrões modernos de microsserviços**.

---

## ⚙️ Requisitos Técnicos

- Java **17 ou superior**
- Spring Boot **3.x**
- Estrutura de projeto com arquitetura em camadas ou arquitetura hexagonal (ports & adapters)
- Aplicar os princípios **SOLID**, **DRY**, **YAGNI**
- Separação clara entre lógica de negócio e infraestrutura
- Utilização de **DTOs** entre camadas
- Validações com `javax.validation` (ex: `@NotNull`, `@Future`, `@CPF`, `@CNPJ`)
- Tratamento global de exceções com `@ControllerAdvice`
- Versionamento de API REST (`/api/v1`)
- Testes unitários com **JUnit 5** e **Mockito**
- Configuração por `application.yml`
- Documentação automática com **Swagger / OpenAPI**

---

## 🔌 Integrações e Persistência

- Persistência com **Spring Data JPA** (adaptável para NoSQL, se necessário)
- Banco de dados: **PostgreSQL** (usar **H2** para testes)
- Integração assíncrona opcional: **Kafka** ou **REST via WebClient**
- Suporte a containers via **Docker**

---

## 📦 Convenções de Projeto

- Pacote base: `com.<empresa>.microservice.<contexto>`
- Estrutura modular de pacotes:
  - `controller`
  - `service`
  - `repository`
  - `model`
  - `dto`
  - `exception`
  - `config`
- Uso de **Lombok** para reduzir boilerplate (`@Getter`, `@Builder`, `@AllArgsConstructor`, etc.)
- Código pronto para deploy em ambientes de cloud

---

## 🧱 Padrões e Engenharia

- Aplicar padrões de projeto quando apropriado:
  - **Factory**, **Builder**, **Strategy**, **Adapter**, entre outros
- Utilizar **MapStruct** para mapeamento entre entidades e DTOs (se aplicável)
- Documentar o código com comentários explicativos nas classes principais

---

## 📘 Especificação Técnica (Exemplo)

```
Serviço: Registro de Boleto Bancário

Funcionalidades:
- Registrar um boleto com os seguintes campos obrigatórios:
  - valor (decimal)
  - vencimento (data futura)
  - pagador (nome, CPF)
  - beneficiário (nome, CNPJ)

- Validar:
  - vencimento deve ser uma data futura
  - CPF e CNPJ devem ser válidos

- Endpoints:
  - POST /api/v1/boletos → Criar um novo boleto
  - GET  /api/v1/boletos/{id} → Consultar boleto por ID

- Regras de erro:
  - 400 - Dados inválidos (validação)
  - 404 - Boleto não encontrado

- Persistir os dados em banco relacional
- Expor documentação via Swagger
```

---

## ✅ Saída Esperada

- Projeto Java/Spring Boot com estrutura completa
- Código limpo, modular e testável
- Endpoints documentados
- Testes automatizados na camada de serviço
- Pronto para execução local e deployment via Docker

---
