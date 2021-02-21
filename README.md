# TO DO API (versão 1.0)
Projeto elaborado no bootcamp de back-end da reprograma com a finalidade de praticar os métodos HTTP, MongoDB e autenticação JWT.

## Objetivo
O objetivo do projeto é possibilitar a visualização de todas as tarefas, por status de concluída e não concluída, por seu ID, registrar, atualizar, conluir uma tarefa, atualizar colaborador e deletar uma tarefa. Todo o desenvolvimento da API foi pensado na utilização de boas práticas e estrutura de pastas, seguindo o design MVC. Além disso, a utilização dos métodos relacionados ao banco de dados MongoDB, suas consultas avançadas e autenticação JWT.

## Rotas
### Apresentação da API

**GET:** /

Apresenta o título da API e sua versão.

Resposta [200]:

~~~Javascript
{
    "titulo": "Projeto To-Do Turma On9",
    "versao": "1.0.0"
}
~~~

### Login

**POST:** /sessions

Para gerar o JSON Web Token que será enviado em todas as requisições protegidas.

Body necessário:

~~~Javascript
{
    "name": "string",
    "password": "string"
}
~~~

Resposta [200]:

~~~Javascript
{
    "user": {
        "id": "object ID",
        "nomeColaborador": "string"
    },
    "token": "string"
}
~~~

Resposta [401]:

~~~Javascript
{
    "error": "Collaborator not found."
}
~~~

### Tarefas
**GET:** /tarefas

Lista todas as tarefas.

Resposta [200]:

~~~Javascript
[
    {
      "descricao": "array",
      "_id": "object ID",
      "concluido": "boolean",
      "nomeColaborador": "string",
      "hashPass": "string"
    }
]
~~~

**GET:** /tarefas/concluidas

Retorna todas as tarefas concluídas.

Resposta [200]:

~~~Javascript
[
    {
      "descricao": "array",
      "_id": "object ID",
      "concluido": "boolean",
      "nomeColaborador": "string",
      "hashPass": "string"
    }
]
~~~

**GET:** /tarefas/naoconcluidas

Retorna todas as tarefas não concluídas.

Resposta [200]:

~~~Javascript
[
    {
      "descricao": "array",
      "_id": "object ID",
      "concluido": "boolean",
      "nomeColaborador": "string",
      "hashPass": "string"
    }
]
~~~

**GET:** /tarefas/{id}

Visualizar a tarefa a partir do seu ID.

Resposta [200]:

~~~Javascript
{
    "descricao": "Array",
    "_id": "object ID",
    "concluido": "boolean",
    "nomeColaborador": "string",
    "hashPass": "string"
}
~~~

**POST:** /tarefas/cadastro

Registrar uma tarefa

Body necessário:

~~~Javascript
{
    "descricao": "string",
    "concluido": "boolean",
    "nomeColaborador": "string",
    "password": "string"
}
~~~

Resposta [200]:

~~~Javascript
{
    "descricao": "Array",
    "_id": "object ID",
    "concluido": "boolean",
    "nomeColaborador": "string",
    "hashPass": "string"
}
~~~

**PUT:** /tarefas/editar/{id}

Editar tarefa. É necessário autorização com token no padrão: Bearer Token.

Body necessário:

~~~Javascript
{
    "concluido": "boolean",
    "descricao": "string",
    "nomeColaborador": "string"
}
~~~

Resposta [200]:

Se a tarefa já está concluída.

~~~Javascript
{
    "message": "Unable to update completed tasks."
}
~~~

Resposta [200]:

Se a tarefa já está concluída.

~~~Javascript
{
    "message": "{id} is updated successfully."
}
~~~

Resposta [401]:

Quando o token não é inserido.

~~~Javascript
{
    "error": "Token not provided."
}
~~~

**PATCH:** /tarefas/naoconcluidas/{id}

Concluir uma tarefa. É necessário autorização com token no padrão: Bearer Token.

Body necessário:

~~~Javascript
{
    "concluido": "boolean"
}
~~~

Resposta [200]:

Se a tarefa já está concluída.

~~~Javascript
{
    "message": "The task cannot be completed."
}
~~~

Resposta [200]:

~~~Javascript
{
    "message": "{id} task is finished."
}
~~~

Resposta [401]:

Quando o token não é inserido.

~~~Javascript
{
    "error": "Token not provided."
}
~~~

**PATCH:** /tarefas/naoconcluidas/colaborador/{id}

Atualizar nome do colaborador. É necessário autorização com token no padrão: Bearer Token.

Body necessário:

~~~Javascript
{
    "nomeColaborador": "string"
}
~~~

Resposta [200]:

Se a tarefa já está concluída.

~~~Javascript
{
    "message": "It is not possible to update the responsible, as this task has already been completed."
}
~~~

Resposta [200]:

Se a tarefa já está concluída.

~~~Javascript
{
    "message": "{id} is updated successfully."
}
~~~

Resposta [401]:

Quando o token não é inserido.

~~~Javascript
{
    "error": "Token not provided."
}
~~~

**DELETE:** /tarefas/{id}

Deletar uma tarefa. É necessário autorização com token no padrão: Bearer Token.

Resposta [200]:

Se a tarefa não estiver concluída ela poderá ser deletada.

~~~Javascript
{
    "message": "Task deleted."
}
~~~

Resposta [200]:

Se a tarefa estiver concluída.

~~~Javascript
{
    "message": "Unable to delete completed tasks."
}
~~~

Resposta [401]:

~~~Javascript
{
    "error": "Token not provided."
}
~~~

## Para rodar o projeto
- Clone esse repositório
- Faça **npm install** em seu terminal para instalar as dependências.

    ~~~Shell
        npm install
    ~~~

- Para rodar o servidor digite **npm start** no terminal:

    ~~~Shell
        npm start
    ~~~

## Tecnologias

Foram utilizadas no desenvolvimento do projeto as seguintes tecnologias:

- Git e Github;
- Visual Studio Code;
- Node.js;
- Express.js;
- Nodemon;
- MongoDB;
- Mongoose;
- Cors;
- Bcrypt;
- Jsonwebtoken.

Feito com ❤️ por Irla Andrade 👋🏽 Entre em contato:

[![Linkedin Badge](https://img.shields.io/badge/-irlaandrade-blue?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/irlaandrade/)](https://www.linkedin.com/in/irlaandrade/)

[![Gmail Badge](https://img.shields.io/badge/gmail-c14438?style=flat-square&logo=Gmail&logoColor=white&link=mailto:paula.irla@gmail.com)](mailto:paula.irla@gmail.com)
