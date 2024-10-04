# DIO - Trilha .NET - API e Entity Framework
www.dio.me

## Desafio de projeto
Para este desafio, você precisará usar seus conhecimentos adquiridos no módulo de API e Entity Framework, da trilha .NET da DIO.

## Contexto
Você precisa construir um sistema gerenciador de tarefas, onde você poderá cadastrar uma lista de tarefas que permitirá organizar melhor a sua rotina.

Essa lista de tarefas precisa ter um CRUD, ou seja, deverá permitir a você obter os registros, criar, salvar e deletar esses registros.

A sua aplicação deverá ser do tipo Web API ou MVC, fique a vontade para implementar a solução que achar mais adequado.

A sua classe principal, a classe de tarefa, deve ser a seguinte:

![Diagrama da classe Tarefa](diagrama.png)

Não se esqueça de gerar a sua migration para atualização no banco de dados.

## Métodos esperados
É esperado que você crie o seus métodos conforme a seguir:


**Swagger**


![Métodos Swagger](swagger.png)


**Endpoints**


| Verbo  | Endpoint                | Parâmetro | Body          |
|--------|-------------------------|-----------|---------------|
| GET    | /Tarefa/{id}            | id        | N/A           |
| PUT    | /Tarefa/{id}            | id        | Schema Tarefa |
| DELETE | /Tarefa/{id}            | id        | N/A           |
| GET    | /Tarefa/ObterTodos      | N/A       | N/A           |
| GET    | /Tarefa/ObterPorTitulo  | titulo    | N/A           |
| GET    | /Tarefa/ObterPorData    | data      | N/A           |
| GET    | /Tarefa/ObterPorStatus  | status    | N/A           |
| POST   | /Tarefa                 | N/A       | Schema Tarefa |

Esse é o schema (model) de Tarefa, utilizado para passar para os métodos que exigirem

```json
{
  "id": 0,
  "titulo": "string",
  "descricao": "string",
  "data": "2022-06-08T01:31:07.056Z",
  "status": "Pendente"
}
```


## Solução
O código está pela metade, e você deverá dar continuidade obedecendo as regras descritas acima, para que no final, tenhamos um programa funcional. Procure pela palavra comentada "TODO" no código, em seguida, implemente conforme as regras acima.


## Desafio Concluido: Implementações

Este projeto é um sistema gerenciador de tarefas desenvolvido como uma API Web utilizando .NET e Entity Framework. Ele permite criar, listar, atualizar e excluir tarefas, organizando-as de maneira eficiente. As tarefas possuem campos como título, descrição, data de execução e status (Pendente ou Concluído).

O campo *Status* utiliza um enum chamado *EnumStatusTarefa* para definir se a tarefa está "Pendente" ou "Concluída".

**Endpoints Implementados**
*GET /Tarefa/{id}*
Busca uma tarefa pelo seu ID. Se a tarefa não for encontrada, retorna 404 Not Found.

*GET /Tarefa/ObterTodos*
Retorna todas as tarefas cadastradas.

*GET /Tarefa/ObterPorTitulo?titulo={titulo}*
Busca tarefas cujo título contenha a string informada.

*GET /Tarefa/ObterPorData?data={data}*
Retorna as tarefas agendadas para uma data específica.

*GET /Tarefa/ObterPorStatus?status={status}*
Retorna as tarefas de acordo com o status informado (Pendente ou Concluído).

*POST /Tarefa*
Cria uma nova tarefa. Caso a data da tarefa seja inválida (vazia), retorna 400 Bad Request. Após a criação, retorna o ID da tarefa criada.

*PUT /Tarefa/{id}*
Atualiza uma tarefa existente. Caso a tarefa não seja encontrada ou a data seja inválida, retorna 404 Not Found ou 400 Bad Request, respectivamente.

*DELETE /Tarefa/{id}*
Remove uma tarefa do sistema. Se a tarefa não for encontrada, retorna 404 Not Found.

**Migrações e Banco de Dados**
O sistema utiliza o *Entity Framework* para gerenciar a persistência das tarefas em um banco de dados. As migrações foram configuradas e aplicadas corretamente, garantindo a criação das tabelas necessárias.

**Configurações Adicionais**
O projeto foi configurado para utilizar o *Swagger* para documentação e teste dos endpoints.
Foi configurado para rodar sob HTTPS, necessitando a aceitação do certificado SSL ao acessar via navegador.
