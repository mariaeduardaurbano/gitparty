# 🎉 Sistema de Gestão de Eventos - GitParty

Este projeto consiste no desenvolvimento de uma **API para gerenciamento de eventos e inscrições**, criada para resolver problemas de controle manual enfrentados pela empresa **GitParty**.

A aplicação permite gerenciar participantes, eventos e inscrições de forma organizada, evitando inconsistências como duplicidade de cadastro e excesso de participantes.

---

## 🚀 Objetivo

Automatizar o controle de eventos e inscrições, garantindo:

- Organização dos participantes  
- Controle de capacidade dos eventos  
- Gerenciamento eficiente de cancelamentos  
- Eliminação de inscrições duplicadas  

---

## 🛠️ Tecnologias Utilizadas

- Node.js  
- Express  
- MariaDB
- Prisma
- Java Script

---

## 📂 Estrutura do Projeto

```
src/
 ┣ controllers/
 ┣ models/
 ┣ routes/
 ┣ services/
 ┗ app.js / server.js
```

---

## 📌 Entidades do Sistema

### 👤 Usuários
Representam os participantes dos eventos.

- id  
- nome  
- email  
- senha  
- data_cadastro  

---

### 📅 Eventos
Representam os eventos disponíveis.

- id  
- titulo  
- descricao  
- data_evento  
- local  
- capacidade_maxima  
- status (ativo, cancelado, encerrado)  

---

### 📝 Inscrições
Relacionam usuários aos eventos.

- id  
- usuario_id  
- evento_id  
- data_inscricao  
- status (confirmada, lista_espera, cancelada)  

---

## ⚙️ Regras de Negócio

### 1️⃣ Limite de participantes
- Um evento não pode ultrapassar sua capacidade máxima.  
- Quando atingir o limite, novas inscrições vão para **lista de espera**.  

### 2️⃣ Inscrição duplicada
- Um usuário **não pode se inscrever duas vezes** no mesmo evento.  

### 3️⃣ Cancelamento
- Só é permitido cancelar até **24h antes do evento**.  

### 4️⃣ Lista de espera
- Quando alguém cancela:
  - O primeiro da lista de espera é promovido automaticamente para **confirmado**.  

---

## ▶️ Como Executar o Projeto

1. Clone o repositório:

```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
```

2. Acesse a pasta:

```bash
cd gitparty
```

3. Instale as dependências:

```bash
npm install
```

4. Inicie o servidor:

```bash
npm start
```

ou (se usar nodemon):

```bash
npm run dev
```

---

## 📡 Rotas da API (exemplo)

### Usuários
- `POST /usuarios/cadastrar`  
- `GET /usuarios/listar`  

### Eventos
- `POST /eventos/cadastrar`  
- `GET /eventos/listar`  

### Inscrições
- `POST /inscricoes/cadastrar`  
- `GET /inscricoes/listar`  
- `PUT /inscricoes/atualizar/:id`  
- `DELETE /inscricoes/excluir/:id`
- `PUT /cancelar/:id`
- `PUT /encerrar/:id`
