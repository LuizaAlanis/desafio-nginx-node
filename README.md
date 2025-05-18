# Projeto Docker com Nginx, Node.js e MySQL

Este projeto configura um ambiente de desenvolvimento utilizando **Docker**, **Nginx**, **Node.js** e **MySQL**. O
objetivo do projeto é expor uma API simples com Node.js que interage com um banco de dados MySQL e exibe uma lista de
nomes cadastrados diretamente em uma página HTML servida pelo Nginx.

## Visão Geral

Quando você acessa o servidor via **Nginx** (na URL `localhost:8080`), ele realiza uma requisição à aplicação **Node.js**, que:

1. Gera um nome aleatório.
2. Insere esse nome na tabela `people` no banco de dados **MySQL**.
3. Exibe a lista de todos os nomes cadastrados.

### Tecnologias Utilizadas

- **Nginx**: Servidor web responsável por fazer o proxy reverso e encaminhar requisições para a aplicação Node.js.
- **Node.js**: Backend da aplicação, onde é feita a inserção de dados e a consulta ao banco de dados.
- **MySQL**: Banco de dados relacional para armazenar os nomes.
- **Docker**: Contêineres para isolar cada serviço e facilitar a configuração e execução do projeto.
- **Docker Compose**: Para orquestrar os contêineres, facilitando o gerenciamento de dependências entre os serviços.

## Como Rodar o Projeto

### Pré-requisitos

**Docker**: Certifique-se de ter o Docker instalado na sua máquina. Você pode verificar isso rodando o seguinte
comando:

```bash
docker --version
```

### Clone o repositório

```bash
git@github.com:LuizaAlanis/desafio-nginx-node.git
```

### Construa e execute os containers

```bash
docker-compose up -d --build
```

### Detalhes Técnicos

Para garantir que a aplicação Node.js só inicie após o banco de dados MySQL estar 100% disponível, usamos o [dockerize](https://github.com/jwilder/dockerize)
no container do Node. Isso evita erros de conexão no início, especialmente em ambientes com bancos grandes ou lentos para inicializar.

![NodeJS](https://img.shields.io/badge/node.js-6DA55F?style=for-the-badge&logo=node.js&logoColor=white)
![Nginx](https://img.shields.io/badge/nginx-%23009639.svg?style=for-the-badge&logo=nginx&logoColor=white)
![MySQL](https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white)