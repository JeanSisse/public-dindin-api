![](https://i.imgur.com/xG74tOh.png)

# Desafio Módulo 3 | API

Essa api servirá para você fazer a integração com o backend, ela foi criada e formatada para funcionar junto ao desafio.

## Passos necessários

1.  Realizar o fork do repositório da api
2.  Clonar para seu computador o fork feito
3.  Executar o `npm install` (para instalar as dependências)
4.  Executar o `npm run dev` (Para "rodar" o projeto! Esse passo deve ser executado todas as vezes que você for desenvolver a aplicação)

**Observação:** A api rodará no endereço http://localhost:3333 .

## Instruções para o CRUD de transações:

Essa `API` possui uma única coleção que já vem com uma transação cadastrada, a coleção chama-se **transactions**, nela todos os verbos do REST estão disponíveis, exemplo:

#### 1. `GET`  http://localhost:3333/transactions
Esse endpoint irá listar todas as transações cadastradas, e o retorno inicial será:

```json=
[
    {
        "date": "2021-09-15T03:00:00.000Z",
        "week_day": "quarta",
        "description": "Venda de carro.",
        "value": 15000,
        "category": "Vendas",
        "type": "credit",
        "id": 1
    }
]
```

#### 2. `GET` http://localhost:3333/transactions/1
Esse endpoint listará apenas uma transação (quando ela existir), o retorno inicial será:

```json=
{
    "date": "2021-09-15T03:00:00.000Z",
    "week_day": "quarta",
    "description": "Venda de carro.",
    "value": 15000,
    "category": "Vendas",
    "type": "credit",
    "id": 1
}
```

#### 3. `POST`  http://localhost:3333/transactions
Nesse endpoint você pode cadastrar outras transações, o `body` para o cadastro precisa seguir o seguinte formato:

Para valores de entrada de dinheiro:
```json=
{
    "date": "2021-09-15T03:00:00.000Z",
    "week_day": "quarta",
    "description": "Venda de carro",
    "value": 15000,
    "category": "Vendas",
    "type": "credit" // ENTRADA DE DINHEIRO
}
```

Para valores de saída de dinheiro:
```json=
{
    "date": "2021-09-15T03:00:00.000Z",
    "week_day": "quarta",
    "description": "Compra de guaraná",
    "value": 5,
    "category": "Compras",
    "type": "debit" //SAÍDA DE DINHEIRO
}
```

Basicamente a única diferença entre entrada e saída é o `type` da transação, sendo:
- **credit** = Entradas de valores
- **debit** = Saída de valores

#### 4. `DELETE` http://localhost:3333/transactions/1

Esse endpoint permite fazer a deleção de uma transação, como bem sabemos, ele não possui `body`, só é necessário passarmos o `id` da transação na rota.


#### 5. `PUT` http://localhost:3333/transactions/1
Esse endpoint permite que você faça a atualização de uma transação, para atualizar basta você passar o `id` da transação na rota e enviar o `body` completo, como no exemplo abaixo:

```json=
{
    "date": "2021-09-15T03:00:00.000Z",
    "week_day": "quarta",
    "description": "Venda de carro.",
    "value": 15000,
    "category": "Vendas",
    "type": "credit"
}
```

#### 5. `PATCH` http://localhost:3333/transactions/1
A `API` conta também com o verbo `patch`, para você poder atualizar apenas um campo de uma transação, para isso você deve passar o `id` da transação na rota e no `body` passar a propriedade que você deseja atualizar, como no exemplo abaixo:

```json=
{    
    "description": "Venda de carro."    
}
```

**Importante:** Você pode passar qualquer propriedade.
