# 🎟️ API de Gerenciamento de Eventos

Uma API RESTful desenvolvida em **Java + Spring Boot** para gerenciamento de eventos e inscrições de participantes. O sistema permite o controle de capacidade, cadastro, consulta, atualização e exclusão tanto de eventos quanto de participantes.

Este projeto faz parte da **Fase 1** da atividade prática integrada (Back-end) para posterior consumo por uma aplicação Front-end.

---

## 👥 Integrantes da Equipe

* **Leonardo de Aguiar Silva Ramalho** — Matrícula: `2515050011` — GitHub: [@leonardo](https://github.com/thatleonardo)
* **Vandemberg Lucas Lima Melo** — Matrícula: `2112090004` — GitHub: [@vanderlucas40](https://github.com/vanderlucas40)

---

## 📌 Sobre o Projeto e Arquitetura

O sistema foi estruturado seguindo o padrão de **arquitetura em camadas** ensinado em sala de aula, garantindo baixo acoplamento e separação clara de responsabilidades:

```text
src/main/java/com/projeto/evento/
├── entities/       # Modelos das tabelas mapeadas com JPA/Hibernate
├── repositories/   # Interfaces de persistência que estendem JpaRepository
├── services/       # Regras de negócio e validações
└── controllers/    # Endpoints REST e controle de requisições HTTP
```
---

## 📋 Entidades Modeladas

### 1. Evento

| Campo | Tipo | Descrição |
| :--- | :--- | :--- |
| `id` | `Long` | Identificador único (auto-incremental) |
| `nome` | `String` | Nome do evento |
| `local` | `String` | Local ou endereço de realização |
| `data` | `LocalDate` | Data do evento (formato `AAAA-MM-DD`) |
| `capacidadeMaxima` | `Integer` | Limite máximo de participantes permitidos |

---

### 2. Participante

| Campo | Tipo | Descrição |
| :--- | :--- | :--- |
| `id` | `Long` | Identificador único (auto-incremental) |
| `nome` | `String` | Nome completo do participante |
| `email` | `String` | E-mail para contato e confirmação |
| `eventoId` | `Long` | Chave estrangeira que referencia o Evento |

---

## 🚀 Tecnologias Utilizadas

- **Linguagem:** Java 17+
- **Framework:** Spring Boot 3.x
- **Gerenciador de Dependências:** Maven
- **Persistência de Dados:** Spring Data JPA / Hibernate / Spring Web
- **Banco de Dados:** H2 Database (em memória)
- **Testes de Integração:** Postman

---

## 🛣️ Endpoints da API

### Entidade: Eventos (`/eventos`)

| Método | Endpoint | Descrição | Status de Retorno |
| :--- | :--- | :--- | :--- |
| `GET` | `/eventos` | Retorna todos os eventos cadastrados | `200 OK` |
| `GET` | `/eventos/{id}` | Retorna um evento específico por ID | `200 OK` / `404 Not Found` |
| `POST` | `/eventos` | Cadastra um novo evento | `201 Created` |
| `PUT` | `/eventos/{id}` | Atualiza todos os dados de um evento existente | `200 OK` / `404 Not Found` |
| `DELETE` | `/eventos/{id}` | Remove um evento do sistema | `204 No Content` / `404 Not Found` |

#### Exemplo de Payload para Evento (`POST` / `PUT`):

```json
{
  "nome": "Semana de Tecnologia 2026",
  "local": "Auditório Central",
  "data": "2026-11-20",
  "capacidadeMaxima": 200
}
