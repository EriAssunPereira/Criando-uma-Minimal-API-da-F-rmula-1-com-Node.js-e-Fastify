# Criando uma Minimal API da Fórmula 1 com Node.js e Fastify

Neste artigo, vamos explorar como criar uma API minimalista para fornecer informações sobre equipes e pilotos de Fórmula 1. Utilizaremos **Node.js** e **Fastify**, uma estrutura web compacta e eficiente. A API resultante será ideal para projetos que exigem respostas rápidas e um ambiente leve.

## Pré-requisitos
Antes de começarmos, certifique-se de ter o **Node.js** instalado em seu sistema.

## Passo 1: Configuração do Projeto
1. Crie um novo diretório para o projeto.
2. Navegue até o diretório do projeto no terminal.
3. Execute o seguinte comando para inicializar um novo projeto Node.js:
   ```bash
   npm init -y
   ```
4. Instale o **Fastify**:
   ```bash
   npm install fastify
   ```

## Passo 2: Estrutura do Projeto
Organize o projeto em módulos para facilitar a manutenção e escalabilidade. Vamos criar os seguintes arquivos:

- `index.js`: Ponto de entrada da aplicação.
- `routes/teams.js`: Rota para informações sobre equipes.
- `routes/drivers.js`: Rota para informações sobre pilotos.

## Passo 3: Implementação das Rotas
### Rota de Equipes
1. No arquivo `routes/teams.js`, crie uma rota para retornar informações sobre todas as equipes de Fórmula 1:
   ```javascript
   // routes/teams.js
   const fastify = require('fastify')();

   fastify.get('/teams', async (request, reply) => {
     // Lógica para buscar informações das equipes
     return { teams: [] }; // Exemplo vazio
   });

   module.exports = fastify;
   ```

### Rota de Pilotos
1. No arquivo `routes/drivers.js`, crie uma rota para retornar informações sobre todos os pilotos de Fórmula 1:
   ```javascript
   // routes/drivers.js
   const fastify = require('fastify')();

   fastify.get('/drivers', async (request, reply) => {
     // Lógica para buscar informações dos pilotos
     return { drivers: [] }; // Exemplo vazio
   });

   module.exports = fastify;
   ```

## Passo 4: Inicialização do Servidor
No arquivo `index.js`, configure o servidor para usar as rotas criadas:
```javascript
// index.js
const fastify = require('fastify')();
const teamsRoute = require('./routes/teams');
const driversRoute = require('./routes/drivers');

fastify.register(teamsRoute);
fastify.register(driversRoute);

const PORT = process.env.PORT || 3000;
fastify.listen(PORT, (err) => {
  if (err) {
    console.error('Erro ao iniciar o servidor:', err);
    process.exit(1);
  }
  console.log(`Servidor rodando na porta ${PORT}`);
});
```

## Executando o Projeto
1. Execute o servidor localmente:
   ```bash
   node index.js
   ```
2. Acesse as rotas através de um cliente HTTP, como o **Postman** ou um navegador web:
   - `/teams`: Retorna informações sobre todas as equipes.
   - `/drivers`: Retorna informações sobre todos os pilotos.
   - `/drivers/:id`: Retorna informações sobre um piloto específico com base no ID fornecido.
   - `/teams/:id`: Retorna informações sobre uma equipe específica com base no ID fornecido.

## Conclusão
Parabéns! Agora você tem uma API minimalista da Fórmula 1 construída com **Node.js** e **Fastify**. Explore mais recursos e aprimore sua API conforme necessário. Lembre-se de adaptar a lógica de busca de dados nas rotas para obter informações reais sobre equipes e pilotos.
