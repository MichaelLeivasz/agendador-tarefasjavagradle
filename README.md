# Microsserviço Agendador de Tarefas

Este microsserviço, desenvolvido em Java com Spring Boot e **Gradle**, gerencia o agendamento de tarefas para usuários. Ele utiliza um banco de dados NoSQL para persistência e autenticação via JWT.

## Tecnologias Utilizadas

* **Java:** Linguagem de programação principal.
* **Gradle:** Sistema de build automatizado.
* **Spring Boot:** Framework para desenvolvimento rápido de aplicações Java.
* **Spring Web:** Para criação de APIs REST.
* **Spring Security:** Framework para segurança de aplicações.
* **JWT (JSON Web Tokens):** Para autenticação e autorização.
* **Banco de Dados NoSQL:** (Substitua por seu banco específico, ex: MongoDB, Cassandra, etc.)
* **Swagger/OpenAPI:** Para documentação da API.

## Pré-requisitos

* Java JDK 17 ou superior.
* Gradle 7 ou superior.
* Banco de dados NoSQL instalado e configurado.

## Endpoints da API

### Tarefas

* **`POST /tarefas`**: Grava uma nova tarefa.
    * Header da requisição: `Authorization: Bearer <token>`
    * Corpo da requisição: `TarefasDTO` (descrição, data/hora, etc.).
    * Retorno: `TarefasDTO`.
* **`GET /tarefas/eventos`**: Busca uma lista de tarefas por período.
    * Parâmetros da requisição:
        * `dataInicial` (LocalDateTime, ISO 8601)
        * `dataFinal` (LocalDateTime, ISO 8601)
    * Retorno: `List<TarefasDTO>`.
* **`GET /tarefas`**: Busca tarefas por email do usuário autenticado.
    * Header da requisição: `Authorization: Bearer <token>`
    * Retorno: `List<TarefasDTO>`.
* **`DELETE /tarefas`**: Deleta uma tarefa por ID.
    * Parâmetro da requisição: `id` (String).
* **`PATCH /tarefas`**: Altera o status de notificação de uma tarefa.
    * Parâmetros da requisição:
        * `status` (StatusNotificacaoEnum).
        * `id` (String).
    * Retorno: `TarefasDTO`.
* **`PUT /tarefas`**: Atualiza uma tarefa por ID.
    * Parâmetro da requisição: `id` (String).
    * Corpo da requisição: `TarefasDTO`
    * Retorno: `TarefasDTO`.

## Segurança

* A API utiliza JWT para autenticação e autorização.
* Os endpoints protegidos requerem um token JWT válido no cabeçalho `Authorization`.
