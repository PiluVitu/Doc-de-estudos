## Como resolver a presença de números mágicos em uma aplicação ? 
- Para resolvermos esse problema, podemos utilizar `enum` que é uma classe especial onde podemos armazenas valores estáticos que pertencem à algum contexto. 
```c#
public enum Condition {
	NEW = 0, 
	GREAT = 1, 
	GOOD = 2,
}
```

- No `enum` acima estamos definido a condição dos itens de um leilão, como no banco de dados a condição de um item varia de 0 a 2, criamos variáveis que representem essas condições, deixando o nosso código bem mais semântico..