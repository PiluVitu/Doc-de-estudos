### Considerações e primeiras impressões da IDE
- Até agora está se mostrando bem fácil de configurar 
- Criação de APIs é bem facilitada, tendo template para quase tudo no C# 
- Achei estranho essa parte das `solutions` não aparecerem no explorador de arquivos por padrão, necessitando que criemos uma pasta no folder do projeto
- Conclusão é que o setup de projetos é bem fácil, seja para *Iniciar* um projeto ou *criar componentes* da sua aplicação
## Conceitos básicos de C# 

### namespace 
- É o nome da pasta do arquivo em questão, onde o nome dos arquivos são separados por `.`  a medida que se vai tendo mais pastas.
```c#
namespace RocketseatAuction.API.Controllers
```
### using 
- Consigo pensar o using como um [[`import`]] no JavaScript, mas não sei se seria algo mais parecido com [[herança]] de classes.
```c#
using Microsoft.AspNetCore.Mvc
```

> Acredito que a formatação padrão para escrita de arquivos, funções e variáveis seja [[Pascal Case]] 

### funções 
- Precisam de `public` acredito que seja porque tem tipagem forte
- Tem [[interfaces]](pelo menos acredito que sejam [[interfaces]]), consegui identificar pelo [[prefixo]] `I` 
```c#
[HttpGet]
public IActionResult GetCurrentAuction() {
	return Created()
}
```

>Com base no exemplo dado acima é possível ver que um [[status code]] é retornado na função com seu nome e não pelo seu código, me lembro de ter visto algo assim usando [[SpringBoot]] 

### var 
- Diferente do JavaScript, `var` não nescessariamente sinaliza a criação de variável padrão no js.
- Quando se coloca var antes de uma variável vc sinaliza para o c# que ele vai inferir o tipo de dado contido ali
```c#
var i = 10; // tipo inferido como int
int j = 10; // tipo especificado explicitamente como int
```
- Quando se usar var em uma nova instância de objeto, busca-se reduzir a quantidade de código na tela, pois esse `var` infere o nome da classe 
```c#
[HttpGet]
public IActionResult GetCurrentAuction() {
	var useCase = new GetCurrentAuctionUseCase()
	
	return Created()
}
```

> Em vez de repetir o nome da classe duas vezes, uso o `var` para poder inferir a classe

### classes
- Creio que tem algumas semelhanças com o que já se faz no ts.
- Como a tipagem de retorno de um método e informar se o mesmo é public : 
```c#
public class GetCurrentAuctionUseCase {
	public void Execute(){
		//Não retorna nada
	}
}
```
 - Já havia visto sobre get e set em spring, revi quando estudava ts e a aqui parece ter sua própria maneira, achei diferente de inicio, mas achei bem coeso
```c#
public class Auction {
	//Aqui definimos o nome da variável, o nivel de escopo e se a mesma pode ser usada e editada  
	public int Id {get; set;}
	public string Name {get; set;}
	public DateTime Starts {get; set;}
	public DateTime Ends {get; set;}
}
```

> Aqui você não necessariamente precisa de uma interface ou type para tipar o retorno de um método, apenas precisa atribuir a entidade que ele representa

> Quando estamos trabalhando com banco de dados é importante criar uma entidade que reflete nossa tabela no banco.

- Podemos fazer heranças de classes apenas inserindo `:` e o nome da classe de onde vamos herdar
```c#
public class AuctionController : ControllerBase{

}
```

---
## Como especificar uma rota da API ? 

- Acima da função que vai executar a lógica eu posso inserir um `[Http<metodo>]` para especificar qual será a rota com base no métodos http. 
### E se eu tiver mais de uma rota com o mesmo método http ? 
- Nesse caso você pode definir um nome especifico para a rota: 
```c#
[HttpGet]
public IActionResult GetCurrentAuction() {
	return Created()
}

[HttpGet("Test")]
public IActionResult Test() {
	return NotFound("Não encontrei meu chapaaa")
}
```

> Uma maneira de ver como isso está funcionando é usar o swagger para documentar o back-end e assim conseguir visualizar os path das rotas

## Como tratar erro de string vir como null e não como "" ? 
- Dentro da nossa entidade, onde temos campos de string, podemos definir um valor padrão para o mesmo, e esse valor padrão é `sring.Empty` ficando mais ou menos assim: 
```c#
public string Name {get; set} = string.Empty;
```
- Assim não irá dar erro caso eu tente usar algum método especifico de `string` 

## Como fazer conexão da minha aplicação com meu banco de dados ?
- Aqui no c# as bibliotecas são chamadas de NuGet Packages
- Na parte de bibliotecas procuramos pelo seguintes pacotes: 
![](Pasted%20image%2020240207205812.png)

![](Pasted%20image%2020240207205824.png)

- Quando formos criar uma classe na pasta da nossa escolha é interessante seguirmos um padrão, que no caso é `NomeDoSeuProjetoDbContext`
- Essa nossa classe vai herdar a classe `DbContext
- Dentro da classe vamos criar um método `override OnConfiguring` onde ele já vai puxar uma função só no ponto pra editar.
- Vamos definir o `optionsBuilder.UseSqlite()` e dentro do método do `UseSqlite`  vamos inserir uma string `Data Source= <Caminho do sqlite no sistema>`
> Para informar ao c# que não é para considerar caracteres de scape como `/n` e afins, devo inserir um `@` antes da string no `UseSqlite()` , ficando assim: `optionsBuilder.UseSqlite(@"Data Source= <Caminho do sqlite no sistema>")`
- Por final precisamos definir qual a entidade que vai se conectar com aquele banco de dados, dentro da classe e acima de `OnConfiguring` é so inserir um: 
```c#
public DbSet<Auction>
```
