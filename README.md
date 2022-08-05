# suap-tools
Ferramentas de acesso não oficial ao SUAP 

# Instalação

```sh

  npm install suap-tools
  yarn add suap-tools
  
  
```

# Uso

```js

import SUAP from 'suap-tools'

const SUAP = require('suap-tools')
```

# Métodos

## getCookie( string matricula, string password )

Realiza login no SUAP e retorna um cookie que pode ser usado para fazer as próximas requisições

### Exemplo
```js
  const cookie = await SUAP.getCookie('1234567', 'senha')
  // 
```
