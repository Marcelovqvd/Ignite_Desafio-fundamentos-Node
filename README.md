# Ignite: Desafio Fundamentos Node
2023 Rocketseat - Desafio: Fundamentos do Node.js
Desafio referente ao módulo: Fundamentos do Node.js
Nesse desafio você reforçará de forma prática os conceitos que aprendemos nesse módulo.

## Sobre o desafio

Nesse desafio você desenvolverá uma API para realizar o CRUD de suas *tasks* (tarefas).

A API deve conter as seguintes funcionalidades:

- Criação de uma task
- Listagem de todas as tasks
- Atualização de uma task pelo `id`
- Remover uma task pelo `id`
- Marcar pelo `id` uma task como completa
- E o verdadeiro desafio: Importação de tasks em massa por um arquivo CSV

- ### Rotas e regras de negócio

Antes das rotas, vamos entender qual a estrutura (propriedades) que uma task deve ter:

- `id` - Identificador único de cada task
- `title` - Título da task
- `description` - Descrição detalhada da task
- `completed_at` - Data de quando a task foi concluída. O valor inicial deve ser `null`
- `created_at` - Data de quando a task foi criada.
- `updated_at` - Deve ser sempre alterado para a data de quando a task foi atualizada.

  

Rotas:

- `POST - /tasks`
    
    Deve ser possível criar uma task no banco de dados, enviando os campos `title` e `description` por meio do `body` da requisição.
    
    Ao criar uma task, os campos: `id`, `created_at`, `updated_at` e `completed_at` devem ser preenchidos automaticamente, conforme a orientação das propriedades acima.
    
- `GET - /tasks`
    
    Deve ser possível listar todas as tasks salvas no banco de dados.
    
    Também deve ser possível realizar uma busca, filtrando as tasks pelo `title` e `description`
    
- `PUT - /tasks/:id`
    
    Deve ser possível atualizar uma task pelo `id`.
    
    No `body` da requisição, deve receber somente o `title` e/ou `description` para serem atualizados.
    
    Se for enviado somente o `title`, significa que o `description` não pode ser atualizado e vice-versa.
    
    Antes de realizar a atualização, deve ser feito uma validação se o `id` pertence a uma task salva no banco de dados.
    
- `DELETE - /tasks/:id`
    
    Deve ser possível remover uma task pelo `id`.
    
    Antes de realizar a remoção, deve ser feito uma validação se o `id` pertence a uma task salva no banco de dados.
    
- `PATCH - /tasks/:id/complete`


### E a importação do CSV?

Normalmente em uma API, a importação de um CSV acontece enviando o arquivo pela rota, por meio de outro formato, chamado `multipart/form-data`.

Como ainda não vimos isso em aula, a importação será feita de outra forma. Acesse a página abaixo para a explicação:
Criação via CSV com Stream
Para realizar isso, vamos utilizar a lib [csv-parse](https://csv.js.org/), utilizando o exemplo de [iterador async](https://csv.js.org/parse/api/async_iterator/).

Com a lib instalada utilizando o gerenciador de pacotes de sua preferência, crie um arquivo a parte para realizar a leitura do arquivo CSV.

Nesse arquivo, deve ser feito a leitura do CSV e para cada linha, realize uma requisição para a rota `POST - /tasks`, passando os campos necessários.

Recomendação do formato do CSV:
title,description
Task 01,Descrição da Task 01
Task 02,Descrição da Task 02
Task 03,Descrição da Task 03
Task 04,Descrição da Task 04
Task 05,Descrição da Task 05

Recomendação de implementação:

Semelhante ao que fizemos no [stream-http-server.js](https://github.com/rocketseat-education/ignite-nodejs-01-fundamentos-nodejs/blob/main/streams/stream-http-server.js) utilizando o `for await`, também é possível fazer com o `parse` da lib informada acima. (Lembre-se de pular a primeira linha do CSV)



## Indo além

Algumas sugestões do que pode ser implementado:

- Validar se as propriedades `title` e `description` das rotas `POST` e `PUT` estão presentes no `body` da requisição.
- Nas rotas que recebem o `/:id`, além de validar se o `id` existe no banco de dados, retornar a requisição com uma mensagem informando que o registro não existe.

  

## Repositório para consultaalém
https://github.com/rocketseat-education/ignite-nodejs-01-fundamentos-nodejs-challenge
