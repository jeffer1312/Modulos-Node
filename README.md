# Modulos-Node

dependecias que uso pra meus projetos e pra que servem Vou tentando colocar modos de usos simples para exemplificar o uso de cada uma delas, caso queria ajudar so contribuir


# Back-End:

## express: Microframework pra criar aplicaçoes (rotas).

#### Modo de uso simples express:

- importa o expres para dentro da variavel express

 ```
const express = require('express'); 
 ```

- criar uma constante com as funçoes do express dentro de uma constante chamada app

 ```
const app = express(); 
 ```

- rota get usando o caminho da rota e uma funcão a ser executada ao acessar aquela rota
 ```
  app.get('/',()=>{})
   ```
  
- usa um metodo do express para ouvir a porta e rodar a aplicação
 ```
app.listen(3333)  
 ```


- bcryptjs: usado pra criptografar senha e outras coisas.


- jsonwebtoken: usado pra criar sessoes e token para essas sessoes.


- multer: usado pra upload de arquivos pro banco de dados

# banco de dados

  - sequelize: ORM pra banco de dados sql
  
  ### knex: ORM para banco de dados sql
  
   ### comando do knex:
   1. 
   ```
   yarn knex init
   ```
   2. configuração dentro do arquivo knexfile.js no objeto development
   ```
  development: {
        client: "sqlite3",
        connection: {
            filename: "./src/database/db.sqlite" //local ond vai ser armazenado o banco de dados
        },
        migrations: {
            directory: "./src/database/migrations" //local ond ficam as migrations do knex
        },
        useNullAsDefault: true
    },
   ```
   3. comando para criar uma migration
   ```
   yarn knex migrate:make nome-da-migration  
   ```
   4. exemplo de uma migration no knex
   ```
   
   exports.up = function(knex) {
    return knex.schema.createTable('ongs', function(table) {
        table.string('id').primary();
        table.string('name').notNullable();
        table.string('email').notNullable();
        table.string('whatsapp').notNullable();
        table.string('city').notNullable();
        table.string('uf', 2).notNullable();

    });


};

exports.down = function(knex) {
    return knex.schema.dropTable('ongs');
};
   ```
   5. comando para rodar as migrations
   ```
    yarn knex migrate:latest      
   ```
    6. comando para desfazer uma migration 
   - para desfazer todas as migrations ja feitas use a flag (--all) ao fim do comando -
   ```
   yarn knex migrate:rollback 
   ```
   
   .7 fazer conexao do knex com o banco
   ```
   const knex = require("knex");
   const configuration = require("../../knexfile");
   
   const config =
       process.env.NODE_ENV === "test" ? configuration.test : configuration.development;   //fazendo uma verificação de qual        o ambiente devera ser configurado, se e o de teste ou de desenvolvimento

   const connection = knex(config);

   module.exports = connection;
   
   ```
  - mongoose: ORM para banco de dados No Sql
  - sqlite3: banco sql lite
  - pg e pg-hstore: plugin do banco de dados postgres
  
# validaçoes e autenticaçoes

  - yup:usado pra validaçao de dados como de email e senha 
  - date-ns@next(o @next e pfra usar a versao mais atual): lidar com datas 
  - celebrate: fazer validaçoes dos dados que estao sendo inseridos no banco de dados
  ## Modo de uso simples do celebrate:
  para validar dados vindo do body
  ```
   celebrate({
         [Segments.BODY]: Joi.object().keys({
              name: Joi.string().required(),
              email: Joi.string().required().email(),
        })
    })
  ```
  
  para validar dados vindo do headers
  
   ```
     celebrate({
        [Segments.HEADERS]: Joi.object({
            authorization: Joi.string().required()
        }).unknown()
    })
  ```
 para validar dados vindo das querys
 
     ```
      celebrate({
        [Segments.QUERY]: Joi.object().keys({
            page: Joi.number()
        })
       ```
  para validar dados vindo das Params
  
   ```
   celebrate({
          [Segments.PARAMS]: Joi.object().keys({
              id: Joi.number().required()
          })
   ```
   
  - cross-env: usar variaveis de ambiente do node



# DEPENDECIAS DE DESENVOLVIMENTO:

 - eslint: usado pra padronização do codigo

 - eslint-config-prettier, eslint-plugin-import ,eslint-plugin-prettier : usado pra padronização do codigo em conjunto com o prettier.

  - nodemon": usado pra ficar sempre escutando as modificaçoes feitas no codigo do back-end

  - prettier": formatar codigo.

  - sequelize-cli": interface de comandos do sequelize no terminal.

  - sucrase": compilador de codigo pra dar algumas funçoes do ES6 ao node

# Front-end(ReactJs)
- Axios: fazer requisiçoes http(conexão com a api)


# Mobile(React Native)

- axios : fazer requisiçoes http(conexão com a api)
- expo: Facilitar uso de recursos nativos do android e ios
- expo-constants: contanstes utilizadas ja configuradas
- expo-mail-composer: cliente para envio de email
- @react-navigation/native: lidar com gestos e navegação
- @react-navigation/stack: lidar com gestos e navegação
    
    
  
  
 
