## Primeira Repetição. 
Conceitos do NodeJS (Com instruções)		
Criar uma Aplicação (API) com Node.js usando express.

Objetivo
Desenvolver uma aplicação simples que exibe o texto Hello World na rota (/).
Primeiro passo para atingir proficiência na configuração e início de uma aplicação Backend.

Rotas:
```javascript
GET /
```
 > Rota principal que exibe a String ('Hello World');


### Instruções
- Criar um diretório chamado primeiraRepeticao dentro de um diretório de sua escolha. Usando o Terminal/Powershell `mkdir primeiraRepeticao`;
- Acessar o diretório criado `cd primeiraRepeticao`
- Iniciar uma aplicação node utilizando o yarn `yarn init -y`
- Adicione o express como dependencia `yarn add express`
- Acesse o diretório criado pelo vs code `code .`
- Crie um diretório chamado *src* 
- Crie uma arquivo chamado *app.js* dentro do diretório *src*
- Abra o arquivo *app.js* e importe o express: `const express = require("express");`
- Defina o express como a constante app: `const app = express();`
- Crie a rota (/) através do verbo http get e devolva a String 'Hello World' usando o metodo .send() da response.

```javascript
app.get("/", (req, res) => {
  res.send("Hello World");
});
```
Mostre sua API para o mundo usando o metodo .listen() na porta 3000 app.listen(3000);
Execute a aplicação no terminal `node src/app.js`
Você Deve Escrever os comandos e não copiá-los. As explicações virão nas repetições futuras. 
Reescreva esta repetição no minimo 10 vezes
