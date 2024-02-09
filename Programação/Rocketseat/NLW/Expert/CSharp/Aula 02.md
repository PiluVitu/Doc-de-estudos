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
public class RocketseatAuctionBaseCOntroller : ControllerBase {
}


```