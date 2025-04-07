# Sistema de Reserva de Salas — Arquitetura em Microserviços

Este projeto é um sistema de reserva de salas desenvolvido com base em microserviços. Utiliza um monorepositório, onde cada serviço possui seu próprio Dockerfile e banco de dados PostgreSQL isolado. A orquestração dos serviços é feita via Docker Compose

## ⚙️ Tecnologias Utilizadas

- Java 17
- Adminer
- Spring Boot
- Docker
- PostgreSQL
  
## 📁 Estrutura do Projeto

```
reserva-salas/
├── SalaMicroService/
│   └── sala/
│       ├── Dockerfile
│       └── src/
├── UserMicroService/
│   └── user/
│       ├── Dockerfile
│       └── src/
├── ReservaMicroService/
│   └── reserva/
│       ├── Dockerfile
│       └── src/
├── docker-compose.yml
└── README.md
```

## 🚀 Como Executar o Projeto

### 1️⃣ Subindo os serviços com Docker Compose

No diretório raiz do projeto, execute:

```bash
docker-compose up -d --build
```

### Esse comando irá iniciar:

- 3 microserviços (UserService, SalaService, ReservaService)
- 3 bancos de dados PostgreSQL
- Adminer

## 🧪 Testando as APIs

### **📌 SalaService (`8082`)**
#### ➕ Criar uma Sala
**POST** `http://localhost:8082/salas`
```json
{
  "nome": "Sala Teste",
  "capacidade": 6
}
```


#### 📄 Listar Salas
**GET** `http://localhost:8082/salas`

---

### **📌 UserService (`8081`)**
#### ➕ Criar um Usuário**
**POST** `http://localhost:8081/users`
```json
{
  "nome": "Haas",
  "email": "haasteste@gmail.com",
  "senha": "senha123",
  "telefone": "45999546789",
  "rua": "Rua Alcides",
  "numero": "255",
  "cidade": "Toledo",
  "cep": "85909-222",
  "cpf": "123456789-10",
  "dataNascimento": "2000-05-04",
  "dataCadastro": "2024-03-10"
}
```

#### 📄 Listar Usuários
**GET** `http://localhost:8081/users`

---

### **📌 ReservaService (`8083`)**
#### ➕ Criar uma Reserva
**POST** `http://localhost:8083/reservas/salvar
```json
{
  "dataHora": "2025-03-05T10:00:00",
  "sala_id": 2,
  "usuario_id": 2
}
```

#### 📄 Listar Reservas
**GET** `http://localhost:8083/reservas`

---
