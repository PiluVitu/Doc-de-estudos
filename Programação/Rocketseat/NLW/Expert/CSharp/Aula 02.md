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


## Como tratar strings de maneira facilitada no c#? 
- No c# 8.0 foi inserido um recurso chamado `Range` que basicamente retorna uma substring com base no range especificado: 
```c# 
var autentication = Bearer jkasgyfuasdbnivcikasashffn

var autenticationFormated = autentication["Bearer ".Lenght..]
// Vai retornar: jkasgyfuasdbnivcikasashffn
```
- 
## Como fazer uma atenticação bem simples sem JWT(Será que dá para adaptar com jwt?)

- Crio uma pasta `Filters` adiciono dentro dela uma classe com o nome que representa que tipo de filtro eu irei usar, como aqui no caso é um atenticação de usuário, demos o nome de `AuthenticationUserAttribute` 
- Essa classe vai herdar uma classe do c# chamada `Authorization Attribute` para conseguirmos herdar métodos já instanciados, para completar devemos adicionar uma interface, para conseguirmos definir uma estrutura do que deve conter na nossa classe, o nome da interface é `IAuthorizationFilter`: 
```c# 
public class AuthenticationUserAttribute : AuthorizationAttribute, IAuthorizationFilter{
}
```
- Ao definir uma interface para nossa classe, ela precisa conter um método obrigatório que é um `OnAuthorization`: 
```c# 
public class AuthenticationUserAttribute : AuthorizationAttribute, IAuthorizationFilter{
	public void OnAuthorization(){
	}
}
```
- Dentro dessa função iremos recuperar o token passado no header da rota e iremos tratar esse valor, extraindo apenas o código de auth: 
```c# 
// Para fazer isso criamos um método separado

private string TokenOnRequest(HttpContext context){
	var authentication = context.Request.Headers.Authorization.ToString();
	return athentication["Bearer ".Length..]
}
```
- Agora dentro da função `onAuthorization` usamos o método previamente feito e inserimos o `context.HttpContext` :
```c# 
public void OnAuthorization(AuthorizationFilterContext context){
	var token = TokenOnRequest(context.HttpContext);
}
```
- Preciso informar no código de execução do c# que é para executar primeiramente o autheticador
- Vou criar um entidade que vai refletir a minha tabela de usuários do BD, para conseguir pegar o email e comparar com o que está no token. 
- Para tratar o token base64 que estamos recebendo é preciso converter ele para string: 
```c# 
private string FromBase64String(string base64){
	var data = Convert.FromBase64String(base64);
	//O que vai ser retornado aqui é os bytes de string
	var dataString = System.Text.Encoding.UTF8.GetString(data);
	return dataString 
}
```
- Agora é só comparar o email recebido no token com o que temos no banco de dados:
```c# 
// dentro de OnAuthorization vamos converter o token com o método criado
	var responseEmail = FromBase64String(token);
	
	var emailExist = repository.Users.Any(user => user.Email.Equals(responseEmail))
```
- Precisamos definir um tratamento de erro caso o email n exista: 
```c#
if(!emailExist){ 
	context.Result = new UnauthorizedObjectResult("E-mail not valid")
}
```