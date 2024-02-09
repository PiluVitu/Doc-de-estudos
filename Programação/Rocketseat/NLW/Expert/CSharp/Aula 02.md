## Como resolver a presença de números mágicos em uma aplicação ? 
- Para resolvermos esse problema, podemos utilizar `enum` que é uma classe especial onde podemos armazenas valores estáticos que pertencem à algum contexto. 
```c#
public enum Condition {
	NEW = 0, 
	GREAT = 1, 
	GOOD = 2,
}
```

- No `enum` acima estamos definido a condição dos itens de um leilão, como no banco de dados a condição de um item varia de 0 a 2, criamos variáveis que representem essas condições, deixando o nosso código bem mais semântico.

## Como deixar o caminho dos endpoints dinâmicos ? 
- Para fazer isso, podemos criar um controller base para todo os endpoints, onde herdamos a classe `ControllerBase` e nos controllers padrões podemos herdar esse controller base e alterar o caminho do endpoint por ele.
> Uma boa maneira de nomear esse controller é colocar o nome do projeto + Base Controller(`RocketseatAuctionBaseController`)
- Dessa maneira se no meio do projeto ou por decisão de negocio as rotas dos endpoint tiverem q mudar, podemos alterar em um caminho só: 
```c#
//Controller Base
public class RocketseatAuctionBaseController : ControllerBase {
}

//Controller do Endpoint
public class AuctionController : RocketseatAuctionBaseController{
[HttpGet]

}
```
- Outra vantagem é conseguirmos compartilhar métodos que estão no controller base com todos que herdarem o mesmo. 

## Como fazer uma atenticação bem simples sem JWT(Será que dá para adaptar com jwt?)

- Crio uma pasta `Filters` adiciono dentro dela uma classe com o nome que representa que tipo de filtro eu irei usar, como aqui no caso é um atenticação de usuário, demos o nome de `AuthenticationUserAttribute` 
- Essa classe vai herdar uma classe do c# chamada `Authorization Attribute` para conseguirmos herdar métodos já instanciados, para completar devemos adicionar uma interface, para conseguirmos definir uma estrutura do que deve conter na nossa classe, o nome da interface é `IAuthorizationFilter` 