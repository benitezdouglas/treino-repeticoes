## Quarta Repetição. 
*Conceitos do NodeJS/Express (Com instruções)*

### Objetivo
Desenvolver uma aplicação simples que será um crud de um cadastro de usuarios com {id, nome, email} (GET/POST/PUT/DELETE)

###Rotas	
```javascript
GET / : Rota principal que exibe a versão da api
GET /users : Rota que exibe a lista de usuarios
POST /users : Rota que insere novo usuario
PUT /users : Rota que atualiza um usuario
DELETE /users : Rota que remove um usuário na lista
````
###Instruções
- Crie um diretório chamado quartaRepeticao para ser o diretório da aplicação, inicie uma aplicação node com yarn init instale o express yarn add express e abra o diretório no vs code.
- Crie um diretório chamado src 
- Crie uma arquivo chamado app.js dentro do diretório src
- Abra o arquivo app.js importe e instancie o express
- Para conseguir pegar o corpo da requisição como JSON é necessário dizer para o express que queremos que nossa api entenda JSON indicando com o metodo .use() do app app.use(express.json());
- Instancie a variável jogos para armazenar a lista let users = [];
- Crie a rota GET / devolva a String 'Crud v0.1.0' usando o metodo .send() da response.
app.get("/", (req, res) => {
 return res.send("Crud OBJ v1.0.0");
});

- Crie a rota GET /users e devolva a lista de usuarios

```javascript
app.get("/users", (req, res) => {
 return res.status(200).json(users);
});
```

- Crie a rota POST /users para inserir um novo jogo na lista

```javascript
app.post("/users", (req, res) => {
 const user = req.body;
 const { id } = req.body;
 const userExiste = users.find(user => user.id === id);
 
 if (!userExiste) {
   users.push(user);
 }
 
 return res.status(201).json(user);
});
 
//Para funcionar esta rota espera receber o seguinte json no corpo da requisição
{
	"id": "1",
	"nome": "Douglas Fazion Benitez",
	"email": "douglasfazion@gmail.com"
}
```

- Crie a roa PUT /users para atualizar um item da lista através do index do array

```javascript
app.put("/users/:id", (req, res) => {
 const { id } = req.params;
 const { nome, email } = req.body;
 
 let user = users.find(user => user.id === id);
 
 if (!user) {
   return res.status(400).json({ message: "Id não encontrado" });
 }
 
 user.nome = nome;
 user.email = email;
 
 return res.status(200).json(user);
});

//Para funcionar esta rota espera receber o seguinte json no corpo da requisição
{
	"nome": "Douglas Fazion Benitez",
	"email": "douglasfazion@gmail.com"
}
```

- Crie a roa DELETE /users para excluir um item da lista através do index do array
```javascript
app.delete("/users/:id", (req, res) => {
 const { id } = req.params;
 
 let userIndex = users.findIndex(user => user.id === id);
 
 users.splice(userIndex, 1);
 
 return res.sendStatus(204);
});
```

Mostre sua API para o mundo usando o metodo .listen() na porta 3000 app.listen(3000);
Execute a aplicação no terminal `node src/app.js`

Para testar utilize um aplicativo chamado insomnia disponível para windows/mac/linux

Você Deve Escrever os comandos e não copiá-los. 
Reescreva este exercicio por 30 minutosno minimo 15 vezes.

###Codigo completo

```javascript
const express = require("express");
 
const app = express();
 
app.use(express.json());
 
let users = [];
 
app.get("/", (req, res) => {
 return res.send("Crud OBJ v1.0.0");
});
 
app.get("/users", (req, res) => {
 return res.status(200).json(users);
});
 
app.post("/users", (req, res) => {
 const user = req.body;
 const { id } = req.body;
 const userExiste = users.find(user => user.id === id);
 
 if (!userExiste) {
   users.push(user);
 }
 
 return res.status(201).json(user);
});
 
app.put("/users/:id", (req, res) => {
 const { id } = req.params;
 const { nome, email } = req.body;
 
 let user = users.find(user => user.id === id);
 
 if (!user) {
   return res.status(400).json({ message: "Id não encontrado" });
 }
 
 user.nome = nome;
 user.email = email;
 
 return res.status(200).json(user);
});
 
app.delete("/users/:id", (req, res) => {
 const { id } = req.params;
 
 let userIndex = users.findIndex(user => user.id === id);
 
 users.splice(userIndex, 1);
 
 return res.sendStatus(204);
});
 
app.listen(3000, () => {
 console.log(`Server started on 3000`);
});
```
 
 

