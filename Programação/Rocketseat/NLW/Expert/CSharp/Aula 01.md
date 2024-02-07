### Considerações e primeiras impressões da IDE
- Até agora está se mostrando bem fácil de configurar 
- Criação de APIs é bem facilitada, tendo template para quase tudo no C# 
- Achei estranho essa parte das `solutions` não aparecerem no explorador de arquivos por padrão, necessitando que criemos uma pasta no folder do projeto
- Conclusão é que o setup de projetos é bem fácil, seja para *Iniciar* um projeto ou *criar componentes* da sua aplicação
# Conceitos básicos de C# 

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

# Como especificar uma rota na API ? 

- Acima da função que vai executar a lógica eu posso inserir um `[Http<metodo>]` para especificar qual será a rota com base no métodos http. 
## E se eu tiver mais de uma rota com o mesmo método http ? 
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
> Uma maneira de ver como isso está funcionando é usar o swagger para documentar o back-end e assim conseguir visualizar funcionando
