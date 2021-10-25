<h1 align="center">
  <img alt="KenzieAcademy" title="KenzieAcademy" src="https://kenzie.com.br/images/logoblue.svg" width="100px" />
</h1>

<h1 align="center">
  Aplicação Base com JSON-server por Emanuel Martins
</h1>

<p align = "center">
Este é o servidor da tarefa 5A04 - Uma aplicação para cadastrar e salvar Comics(Quadrinhos)/HQ's!
</p>

<p align="center">
  <a href="#endpoints">Endpoints</a>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</p>

## **Endpoints**

A API tem um total de 6 endpoints, sendo feito pelo acesso de um usuário - podendo criar e ler os quadrinhos feitas pelos usuários, criar e ler os quadrinhos salvas pelo usuários. <br/>

URL base: https://json-server-emanuelz-martins.herokuapp.com

## Rotas que não necessitam de autorização

<h2 align ='center'> Cadastrar novo usuário </h2>

`POST /register - FORMATO DA REQUISIÇÃO`

```json
{
	"id": 2,
	"email": "mail@mail.com",
	"password": "123456",
	"name": "Usuário",
	"age": 18
}
```

<h2 align ='center'> Fazer Login no sistema </h2>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
	"email": "testman@thisapp.com",
	"password": "123456"
}
```

```reposta
{
    "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RtYW5AdGhpc2FwcC5jb20iLCJpYXQiOjE2MzUxOTc1NzEsImV4cCI6MTYzNTIwMTE3MSwic3ViIjoiMiJ9.rPfV7YxM2chJba74QkQLOWgsHTJxFWt5YHMJcCf4tiw",
    "user": {
        "email": "testman@thisapp.com",
        "name": "Emanuel",
        "age": 20,
        "id": 2
    }
}
```

## Rotas que necessitam de autorização

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

<h2 align ='center'> Listando comics </h2>

`GET /comics - FORMATO DA RESPOSTA - STATUS 200`

```json
[
	{
		"id": 1,
		"owner_user": 2,
		"type": "super_heroes",
		"title": "A Piada Mortal"
	}
]
```

Podemos utilizar os query params para mudar a lista

`GET /comics?id=2 - FORMATO DA RESPOSTA - STATUS 200`

```json
[
	{
		"id": 2,
		"userId": 2,
		"type": "super_heroes",
		"title": "KINGDOM COME"
	}
]
```

<h2 align ='center'> Listando comics salvas </h2>

`GET /saved_comics - FORMATO DA RESPOSTA - STATUS 200`

```json
[
	{
		"id": 1,
		"userId": 3,
		"type": "super_heroes",
		"title": "A Piada Mortal",
		"comment": "Lorem Ipsum"
	}
]
```

<h2 align ='center'> Criar comics gerais para o sistema </h2>

`POST /comics - FORMATO DA REQUISIÇÃO`

```json
{
	"id": 1,
	"userId": 2,
	"type": "category",
	"title": "comic name"
}
```

<h2 align ='center'> Salvando comics  </h2>

`POST /saved_comics - FORMATO DA REQUISIÇÃO`

```json
{
	"id": 2,
	"userId": 3,
	"type": "super_heroes",
	"title": "KINGDOM COME",
	"comment": "LIPSUM"
}
```

Feito por emanuelz-martins!
