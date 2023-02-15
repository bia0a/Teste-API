
# API Teste de Empréstimos Bancários

Este é um projeto que foi desenvolvido como parte do desafio técnico proposto pelo Serasa.

## Clone
Para clonar o repositório em sua máquina local, execute o seguinte comando:
```bash
  $ git clone https://github.com/bia0a/Teste-API.git
```
## Executando o Projeto Localmente
Para a execução do ambiente, é necessário que você possua instalado o Postman em sua máquina.
```bash
Download Postman via https://www.getpostman.com/apps
```
 ### Importação do arquivo `.postman_collection.json`
 Para importar seus dados para o Postman, selecione Importar no canto superior esquerdo e selecione o arquivo `API Teste de Empréstimos Bancários.postman_collection.json`

 ### Configurando a execução da `collection`
1. Escolha a collection `API Teste de Empréstimos Bancários` na barra lateral.
 2. Na guia visão geral, selecione Executar.
 3. Selecione Executar manualmente e selecione Executar `API Teste de Empréstimos Bancários`.

## Documentação da API

#### Link da API

```http
  https://8dac9f4e-fcb2-4e8f-857a-e4ed3497a0d8.mock.pstmn.io
```

#### Token da API

Deve utilizar o token sem as aspas como Bearer Token

|    Path     |  Tipo      | Descrição                           |
| :---------- | :--------- | :---------------------------------- |
|   `auth`    |  `string`  | "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyLCJkZXNhZmlvIjoic2VyYXNhIn0.oOMv4kf9hKMtuatZEZJyESVu9Z7h6hGBwrZRJ-9HkCU"
 

## Busca na API
```http
  GET /bank
```

```bash
[
    {
        "id": 1,
        "banco": "Banco do Brasil",
        "estadoAtuacao": "SC",
        "juros": "11,25%"
    },
    {
        "id": 2,
        "banco": "Caixa Econômica Federal",
        "estadoAtuacao": "SP",
        "juros": "10,75%"
    },
    {
        "id": 3,
        "banco": "Banco Santander",
        "estadoAtuacao": "PR",
        "juros": "13,00%"
    },
    {
        "id": 4,
        "banco": "Banco Itaú",
        "estadoAtuacao": "SC",
        "juros": "12,50%"
    },
    {
        "id": 5,
        "banco": "Banco Mercantil do Brasil",
        "estadoAtuacao": "SC",
        "juros": "11,50%"
    },
    {
        "id": 6,
        "banco": "Banco Safra",
        "estadoAtuacao": "SP",
        "juros": "12,50%"
    },
    {
        "id": 7,
        "banco": "Banco Bradesco",
        "estadoAtuacao": "SC",
        "juros": "12,50%"
    },
    {
        "id": 8,
        "banco": "Banco Inter",
        "estadoAtuacao": "SP",
        "juros": "10,50%"
    },
    {
        "id": 9,
        "banco": "Nubank",
        "estadoAtuacao": "SC",
        "juros": "10,75%"
    },
    {
        "id": 10,
        "banco": "Banco Original",
        "estadoAtuacao": "SP",
        "juros": "12,50%"
    }
]
```
## Observação 1.1
#### Criticidade; Nível Alto
Ao realizar a busca da API sem o Bearer Token, a mesma informação é mostrada.

# Busca usando query parameters
Busca filtrando por estado de atuação de Santa Catarina
```http
GET https://8dac9f4e-fcb2-4e8f-857a-e4ed3497a0d8.mock.pstmn.io/bank?estadoAtuacao=SC
```
```bash
[
    {
        "id": 1,
        "banco": "Banco do Brasil",
        "estadoAtuacao": "SC",
        "juros": "11,25%"
    },
    {
        "id": 4,
        "banco": "Banco Itaú",
        "estadoAtuacao": "SC",
        "juros": "12,50%"
    },
    {
        "id": 5,
        "banco": "Banco Mercantil do Brasil",
        "estadoAtuacao": "SC",
        "juros": "11,50%"
    },
    {
        "id": 7,
        "banco": "Banco Bradesco",
        "estadoAtuacao": "SC",
        "juros": "12,50%"
    },
    {
        "id": 9,
        "banco": "Nubank",
        "estadoAtuacao": "SC",
        "juros": "10,75%"
    }
]
```
## Observação 1.2
#### Criticidade; Nível Alto
Ao realizar a busca da API sem o Bearer Token, a mesma informação é mostrada.
#### Criticidade; Nível médio
O mesmo acontece caso o value da key estadoAtuacao esteja vazio ou com outra infomação diferente de SC
 
## Alterações de Informação
 ### Alteração das informações do Banco do Brasil na API para: ‘estadoAtuacao’: ‘SP’ e valor de ‘juros’: 15,00 usando o campo ‘ID’:
```http
  PUT /bank/?id=1
```
#### body:
```bash
{
        "estadoAtuacao": "SP",
        "juros": "15,00%"
}
```
### Messagem de sucesso
```bash
[
    {
        "mensagem": "Registro alterado com sucesso!"
    },
    {
        "id": 1,
        "banco": "Banco do Brasil",
        "estadoAtuacao": "SP",
        "juros": "15,00%"
    }
]

```
## Observação 1.3
#### Criticidade; Nível Alto
Ao realizar a alteração na infomação da API sem o Bearer Token, a mesma mensagem de confirmação é mostrada.
#### Criticidade; Nível Médio
O mesmo acontece caso o value da key id esteja vazio ou com outra infomação diferente de 1
## Inserção de dado
#### Adição de um novo banco
```http
  POST /bank
```
#### body:
```bash
{
        "banco":"Banco Teste",
        "estadoAtuacao": "SC",
        "juros": "10,00%"
}
```
### Messagem de sucesso
```bash
[
    {
        "id": 463,
        "banco": "Banco Teste",
        "estadoAtuacao": "SC",
        "juros": "10,00%"
    },
    {
        "mensagem": "Banco adicionado com sucesso!"
    }
]

```
## Observação 1.4
#### Criticidade; Nível Alto
Ao realizar a adição na infomação da API sem o Bearer Token, a mesma mensagem de confirmação é mostrada.
#### Criticidade; Nível Médio
O mesmo acontece caso seja inserido key e value, e com informações nulas ou divergentes no body.
## Cenário de testes

|   Cenário   |  Tipo      | Descrição                           |
| :---------- | :--------- | :---------------------------------- |
|`Teste de segurança`|` Não-funcional`|Verifica se os dados podem ser acessados sem Token de segurança|
|   `Teste de unidade`    |  `funcional`  |Verifica se há dados buscados pelo `GET` |
|   `Teste de unidade`    |  `funcional`  |Verifica se há dados buscados pelo `GET` filtrados com o *Query Params*|
|   `Teste de unidade`    |  `funcional`  |Verifica se a alteração pelo `PUT` foi validada |
|   `Teste de unidade`    |  `funcional`  |Verifica se a inserção de dado pelo `POST` foi validada |
