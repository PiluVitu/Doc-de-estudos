- Como node roda no server ele não tem acesso a apis do browser como documents e etc
## Padrão de Importação
Precisa ser definido no package jsona
### CommonJs
Usa o require para importar os modulos
```js
const http = require('http')
```
### Module
Usa import/export para se usar os modulos
```js
import http from 'http'
```

- Para importar módulo do node geralmente usamos o prefixo `node:` 

## Rotas http

C reate
R ead
U pdate
D elete
### Metodos
#### GET => Listagem de dado(s)
#### POST => Criação de dado(s)
#### PUT => Edição de dados em lote
#### PATCH => Atualizar dado especifico
#### DELETE => Exclusão de dados
