# suap-web-api

Ferramentas de acesso não oficial ao SUAP

# Instalação

```sh

  npm install suap-web-api
  yarn add suap-web-api


```

# Uso

```js
import SUAP from "suap-web-api";

const SUAP = require("suap-web-api");
```

# Métodos

## `string getCookie( string matricula, string password )`

Realiza login no SUAP e retorna um cookie que pode ser usado para fazer as próximas requisições

### Exemplo

```js
const cookie = await SUAP.getCookie("1234567", "senha");
// ->
```

## ` setCookie( string | string[] cookie )`

`setCookie` é usada sempre que for necessário fazer uma requisição que deve ser autenticada.

### Exemplo

```js
const cookies = "__Host_.....";

const cookie = await SUAP.setCookie(cookies).get("/rh/servidor/1234567");
// ->
```

## `string get( string path [, object params = {} ] )`

`get()` realiza uma requisição do tipo GET ao SUAP e recebe o seu resultado como string.

| Parâmetro | Tipo     | Valor Padrão | Obrigatório |
| --------- | -------- | ------------ | ----------- |
| path      | `string` | `/`          | `true`      |
| params    | `object` | `{}`         | `false`     |

### Exemplo

```js
// Requisição não autenticada à url /acesso
const content = await SUAP.get("/acesso");
// -> Retorna o HTML da página

// Requisição autenticada à url /rh/servidor/1234567
const content = await SUAP.setCookie("__Httt....").get("/rh/servidor/1234567");
// -> Retorna o HTML da página

// Requisição à url /rh/servidor/1234567
const content = await SUAP.get("/acesso/login", { next: "/" });
// -> Retorna o HTML da página /acesso/login?next=/
```

## `string post( string path [, object data = {} ] )`

`post()` realiza uma requisição do tipo POST ao SUAP e recebe o seu resultado como string.

| Parâmetro | Tipo     | Valor Padrão | Obrigatório |
| --------- | -------- | ------------ | ----------- |
| path      | `string` | `/`          | `true`      |
| data      | `object` | `{}`         | `false`     |

### Exemplo

```js
// Requisição não autenticada à url /acesso
const content = await SUAP.post("/acesso");
// -> Retorna o HTML da página

// Requisição autenticada à url /rh/servidor/1234567
const content = await SUAP.setCookie("__Httt....").post("/rh/servidor/1234567");
// -> Retorna o HTML da página

// Requisição à url /rh/servidor/1234567
const content = await SUAP.post("/acesso/login", {
  username: "1234567",
  password: "senha",
});
// -> Retorna o HTML da página /acesso/login?next=/ após o envio do formulário
```
