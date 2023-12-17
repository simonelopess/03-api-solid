# App 

Gympass style app

## RFs (Requisitos Funcionais)

- [ ] Dever ser possível se cadastrar;
- [ ] Deve ser possível se autenticar;
- [ ] Deve ser possível obter o perfil de um usuário logado;
- [ ] Deve ser possível obter o número de check-ins realizados pelo usuário logado;
- [ ] Deve ser possível o usuário obter seu histórico de check-ins;
- [ ] Deve ser possível o usuário buscar academias próximas;
- [ ] Deve ser possível o usuário buscar academias pelo nome;
- [ ] Deve ser possível o usuário realizar check-in em uma academia;
- [ ] Deve ser possível validar o check-in de um usuário;
- [ ] Deve ser possível cadastrar uma academia;

## RNs (Regras de Negócio)

- [ ] O usuário não deve poder se cadastrar com um e-mail duplicado;
- [ ] O usuário não pode fazer check-in no mesmo dia;
- [ ] O usuário não pode fazer check-in se não estiver perto (100m) da academia;
- [ ] O check-in só pode ser validado até 20 minutos após criado;
- [ ] O check-in só pode ser validado por administradores;
- [ ] A academia só pode ser cadastrada por administradores;


## RNFs (Requisitos não-funcionais)

- [ ] A senha do usuário precisa estar criptografada;
- [ ] Os dados da aplicação precisam estar persistidos em um banco PostgresSQL;
- [ ] Todas as listas de dados precisam estar paginadas por 20 itens por página;
- [ ] O usuário deve ser identificado por um JWT (token);



### Libs usadas

- tsup -> fazer build para produção

`npx i prisma -D` -> trabalhar com prisma em ambiente de desenvolvimento
`npx prisma generate` -> cria de forma automatica a tipagem do schema
`npm i @prisma/client ` -> dependencia para trabalhar em producao


### Configuração do docker

`docker run --name api-solid-pg bitnami/postgresql:latest`

Criando a configuração com variáveis de ambiente


`docker run --name api-solid-pg -e POSTGRESQL_USERNAME=docker -e POSTGRESQL_PASSWORD=docker -e POSTGRESQL_DATABASE=apisolid -p 5432:5432 bitnami/postgresql:latest`

`docker ps -a` -> list containers

`docker start [namedocontainer]` -> inicia

`docker stop [namedocontainer]` -> para

`docker rm [namedocontainer]` -> remove 

`docker logs [nomedocontainer]` -> logs

`docker logs -f [nomedocontainer]` -> watch logs

### Conexão prisma com BD

- No env modificar o nome, senha e user da configuração
Ex: DATABASE_URL="postgresql://teste:teste@localhost:5432/teste?schema=public"

`npx prisma migrate dev` -> Cria a entity no banco de dados no docker criando uma migration
`npx prisma studio` -> visualiza as tabelas criadas

### Docker Compose 

```docker compose up -d``` -> starta
```docker compose stop``` -> para
```docker compose down ``` -> deleta