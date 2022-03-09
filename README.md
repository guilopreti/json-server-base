# json-server-base

Esse é o repositório com a base de JSON-Server + JSON-Server-Auth já configurada, feita para ser usada no desenvolvimento das API's nos Capstones do Q2, e agora sendo utilizada para a atividade 11
JSON-Server: Fake-API do início ao Deploy.

## ENDPOINTS

Assim como a documentação do JSON-Server-Auth traz (https://www.npmjs.com/package/json-server-auth), existem 3 endpoints que podem ser utilizados para cadastro e 2 endpoints que podem ser usados para login de usuarios, e também 1 endpoint para cadastro e busca de animais, e mais um outro para comentários.

### CADASTRO DE USUÁRIO

POST /register <br/>
POST /signup <br/>
POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.
Você pode ficar a vontade para adicionar qualquer outra propriedade no corpo do cadastro dos usuários.

### Formato

{
"email": "exemplo@mail.com",
"password": "exemplo",
"name": "exemplo",
"age": 15
},

### Resposta exemplo 201

{
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6Imd1Z3VAbWFpbC5jb20iLCJpYXQiOjE2NDY3ODE0NjIsImV4cCI6MTY0Njc4NTA2Miwic3ViIjoiMiJ9.ALsEehQDwx0CA03nz1qc_G47S0StiNYp_tbvH1YhC2w",
"user": {
"email": "exemplo@mail.com",
"name": "exemplo",
"age": 15,
"id": 1
}
}

### LOGIN

POST /login <br/>
POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"

### Formato

{
"email": "exemplo@mail.com",
"password": "exemplo",
},

### Resposta exemplo 200

{
"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6Imd1Z3VAbWFpbC5jb20iLCJpYXQiOjE2NDY3ODE0NjIsImV4cCI6MTY0Njc4NTA2Miwic3ViIjoiMiJ9.ALsEehQDwx0CA03nz1qc_G47S0StiNYp_tbvH1YhC2w",
"user": {
"email": "exemplo@mail.com",
"name": "exemplo",
"age": 15,
"id": 1
}
}

### CADASTRO DE ANIMAL

POST /animals

### Formato

Necessita de autentificação com token do usuário logado.

{
"type": "Dog",
"name": "Maru",
"userId": "1"
}

### Resposta exemplo 201

{
"type": "Dog",
"name": "Maru",
"userId": "1",
"id": 1
}

### BUSCAR ANIMAIS

GET /animals

Não precisa de corpo.

### Resposta exemplo 200

[
{
"type": "Dog",
"name": "Chuchu",
"userId": "1",
"id": 1
},
{
"type": "Dog",
"name": "Maru",
"userId": "1",
"id": 2
}
]

### CADASTRO DE COMENTÁRIO

POST /comments

### Formato

Necessita de autentificação com token do usuário logado.

{
"comment": "Exemplo",
"userId": 1
}

### Resposta exemplo 201

{
"comment": "Exemplo",
"userId": 1
"id": 2
}

### VER COMENTÁRIOS

GET /comments

Não precisa de corpo, mas precisa de autentificação de token gerado ao logar.

### Resposta exemplo 200

[
{
"comment": "Exemplo",
"userId": 2,
"id": 1
},
{
"comment": "Exemplo",
"userId": 1,
"id": 2
}
]
