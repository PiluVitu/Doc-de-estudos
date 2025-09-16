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

## Stateful - Stateless
Stateful é uma aplicação que armazena dados em memoria interna para funcionar, caso o app seja reiniciado ou derrubado, a aplicação não funcionará corretamente ou como o planejado, já Stateless é um app onde os dados ficam salvos em ambientes de terceiros(S3, BD, Redis e etc) e caso seja reiniciada ela funciona normalmente 
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
