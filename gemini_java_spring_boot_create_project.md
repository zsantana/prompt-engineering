Sim, consigo gerar o prompt no formato Markdown. Aqui está ele:

---

## **Prompt para Geração de Microsserviço Java com Spring Boot**

"Eu preciso de um **microsserviço Java** usando **Spring Boot** que implemente a seguinte **especificação técnica de critérios de negócio**. O código gerado deve aderir estritamente às **melhores práticas de engenharia de software**, com foco em:

1.  **Arquitetura Limpa (Clean Architecture) / Arquitetura Hexagonal:**
    * Separar claramente as camadas de domínio (core), aplicação (serviços), infraestrutura (repositórios, integração externa) e apresentação (controladores).
    * Garantir que as dependências fluam para dentro, ou seja, as camadas externas dependam das camadas internas, mas não o contrário.
    * Utilizar interfaces para definir contratos entre as camadas, promovendo inversão de dependência.

2.  **Domain-Driven Design (DDD):**
    * Modelar as entidades, agregados, objetos de valor e serviços de domínio de acordo com a linguagem ubíqua da especificação de negócio.
    * Encapsular a lógica de negócio complexa dentro do domínio, protegendo a consistência dos dados.
    * Evitar vazamento de lógica de negócio para camadas externas (e.g., controladores ou serviços de aplicação).

3.  **Princípios SOLID:**
    * **Single Responsibility Principle (SRP):** Cada classe e método deve ter uma única responsabilidade.
    * **Open/Closed Principle (OCP):** Entidades de software (classes, módulos, funções, etc.) devem ser abertas para extensão, mas fechadas para modificação.
    * **Liskov Substitution Principle (LSP):** Subtipos devem ser substituíveis por seus tipos base sem alterar a corretude do programa.
    * **Interface Segregation Principle (ISP):** Clientes não devem ser forçados a depender de interfaces que não utilizam.
    * **Dependency Inversion Principle (DIP):** Módulos de alto nível não devem depender de módulos de baixo nível. Ambos devem depender de abstrações.

4.  **Tratamento de Erros e Exceções:**
    * Implementar um tratamento de exceções robusto e padronizado, utilizando `@ControllerAdvice` e `@ExceptionHandler` para globalizar a resposta de erro.
    * Definir exceções customizadas para erros de negócio, fornecendo mensagens claras e códigos de erro específicos.
    * Evitar capturar exceções genéricas (e.g., `Exception`), a menos que seja para relançar exceções mais específicas.

5.  **Validação de Dados:**
    * Utilizar **Bean Validation (JSR 380)** com anotações como `@NotNull`, `@Size`, `@Pattern`, etc., para validar os dados de entrada nos DTOs.
    * Realizar validações de negócio mais complexas dentro dos serviços de domínio ou aplicação.

6.  **Segurança (Spring Security):**
    * Configurar o Spring Security para autenticação (e.g., JWT, OAuth2) e autorização (baseada em roles/permissões), caso a especificação de negócio inclua requisitos de segurança.
    * Proteger os endpoints adequadamente.

7.  **Persistência de Dados:**
    * Utilizar **Spring Data JPA** para abstrair a camada de acesso a dados.
    * Modelar as entidades JPA de forma eficiente, considerando índices e relacionamentos.
    * Empregar transações de forma adequada para garantir a consistência dos dados.

8.  **Testabilidade:**
    * Projetar o código para ser facilmente testável, utilizando injeção de dependência.
    * Fornecer exemplos de **testes unitários** (com Mockito) para as camadas de serviço e domínio.
    * Fornecer exemplos de **testes de integração** (com `@SpringBootTest`) para os controladores e repositórios.

9.  **Configuração Externa:**
    * Utilizar o sistema de configuração do Spring Boot (`application.properties` ou `application.yml`) para gerenciar parâmetros de ambiente.

10. **Documentação:**
    * Adicionar comentários Javadoc relevantes em classes e métodos públicos para explicar a intenção e o comportamento.
    * Gerar endpoints de documentação da API utilizando **SpringDoc OpenAPI (Swagger UI)**.

---

**[INSERIR A ESPECIFICAÇÃO TÉCNICA DE CRITÉRIOS DE NEGÓCIO AQUI. Exemplos abaixo:]**

**Exemplo de Especificação Técnica de Critérios de Negócio:**

**Nome do Microsserviço:** Gerenciamento de Produtos

**Endpoints:**

* `POST /products`: Cria um novo produto.
    * **Entrada:** `{ "name": "String", "description": "String", "price": "BigDecimal", "category": "String" }`
    * **Critérios:**
        * `name` é obrigatório e único.
        * `price` deve ser positivo.
        * `category` deve ser um dos valores pré-definidos (e.g., "Eletrônicos", "Alimentos", "Vestuário").
    * **Saída:** Detalhes do produto criado com um ID gerado.
    * **Exceções:** `ProductAlreadyExistsException`, `InvalidProductDataException`.
* `GET /products/{id}`: Busca um produto por ID.
    * **Critérios:** `id` é um UUID válido.
    * **Saída:** Detalhes do produto.
    * **Exceções:** `ProductNotFoundException`.
* `PUT /products/{id}`: Atualiza um produto existente.
    * **Entrada:** `{ "name": "String", "description": "String", "price": "BigDecimal", "category": "String" }` (campos opcionais para atualização parcial)
    * **Critérios:** Mesmos critérios de validação do POST.
    * **Saída:** Detalhes do produto atualizado.
    * **Exceções:** `ProductNotFoundException`, `InvalidProductDataException`.
* `DELETE /products/{id}`: Deleta um produto por ID.
    * **Saída:** Status de sucesso.
    * **Exceções:** `ProductNotFoundException`.

**Regras de Negócio Adicionais:**

* Apenas usuários autenticados com a role "ADMIN" podem criar, atualizar ou deletar produtos.
* A busca de produtos é pública.
* Ao criar um produto, a data de criação e a última data de atualização devem ser automaticamente preenchidas.

---

**Formato da Resposta Esperada:**

O código deve ser apresentado com a estrutura de diretórios padrão de um projeto Spring Boot, incluindo:

* `src/main/java/{base_package}/`
    * `config/`
    * `domain/` (entities, aggregates, value objects, domain services, exceptions)
    * `application/` (use cases, application services, dtos)
    * `infrastructure/` (repositories, adapters, external integrations)
    * `presentation/` (controllers)
    * `ProductApplication.java` (classe principal)
* `src/test/java/{base_package}/`
    * Testes unitários e de integração.
* `pom.xml` (com as dependências necessárias)
* `application.properties` ou `application.yml`

Por favor, gere o código completo seguindo essas diretrizes."
