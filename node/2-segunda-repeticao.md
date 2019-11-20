## Segunda Repetição. 
*Conceitos do NodeJS/Express (Com instruções)*

Objetivo
Desenvolver uma aplicação simples que será o inicio do crud de uma lista de Jogos (GET/POST)

Rotas	
```javascript
GET / : Rota principal que exibe a versão da api
GET /jogos : Rota que exibe a lista de jogos
POST /jogos : Rota que insere novo jogo na lista
```

### Instruções
- Crie um diretório chamado segundaRepeticao para ser o diretório da aplicação, inicie uma aplicação node com yarn init instale o express yarn add express e abra o diretório no vs code.
- Crie um diretório chamado *src* 
- Crie uma arquivo chamado *app.js* dentro do diretório *src*
- Abra o arquivo app.js e importe o express: `const express = require("express");`
- Defina o express como a constante app: `const app = express();`
- Para conseguir pegar o corpo da requisição como JSON é necessário dizer para o express que queremos que nossa api entenda JSON indicando com o metodo .use() do app. `app.use(express.json());`
- Como estamos iniciando um crud precisamos que nossa aplicação armazene os dados em algum lugar, 
e para essa série de repetições vamos utilizar um array, e como o crud se trata de uma lista de jogos vamos instanciar a variável jogos. `let jogos = [];`
- Crie a rota GET / devolva a String 'Crud v0.1.0' usando o metodo .send() da response.

```javascript
app.get("/", (req, res) => {
  return res.send("Crud v0.1.0");
});
```

- Crie a rota GET /jogos e devolva a lista de jogos
```javascript
app.get("/jogos", (req, res) => {
  return res.json(jogos);
});
```

- Crie a rota POST /jogos para inserir um novo jogo na lista
```javascript
app.post("/jogos", (req, res) => {
  const { jogo } = req.body;
  jogos.push(jogo);
  return res.json(jogos);
});

//Para funcionar esta rota espera receber o seguinte json no corpo da requisição
{
  "jogo": "Nome do jogo que deseja adicionar na lista"
}
```

Mostre sua API para o mundo usando o metodo .listen() na porta 3000 app.listen(3000);
Execute a aplicação no terminal `node src/app.js`

Para testar utilize um aplicativo chamado insomnia disponível para windows/mac/linux

Você Deve Escrever os comandos e não copiá-los. As explicações virão nas repetições futuras. 
Reescreva este exercicio no mínimo 10 vezes.


### Codigo completo
```javascript
const express = require("express");
 
const app = express();
 
app.use(express.json());
 
let jogos = [];
 
app.get("/", (req, res) => {
  return res.send("Crud v0.0.1");
});
 
app.get("/jogos", (req, res) => {
  return res.json(jogos);
});
 
app.post("/jogos", (req, res) => {
  const { jogo } = req.body;
  jogos.push(jogo);
  return res.json(jogos);
});
 
app.listen(3000);
