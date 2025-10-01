## Comandos Base em go 

`go mod init <nomeDaPastaDoProjeto`
`go run <arquivoGo>`
### `go build`
-o => Passa o nome do arquivo compilado
#### Cross-Compilation
Ao setar as envs inline ou no `go env -w` eu compilo o go build na linguagem que eu definir
GOOS - Nome do os em que quer compilar 
GOARCH - Nome da arquitetura que quer compilar 
Essas são exemplos de combinações: 
- `linux/amd64` (servidores Linux)
- `windows/amd64` (Windows 64-bit)
- `darwin/amd64` (macOS Intel)
- `darwin/arm64` (macOS Apple Silicon)
- `linux/arm64` (Raspberry Pi 4, servidores ARM)
Se está em duvida se alguma plataforma suporta rode o comando `go tool dist list`
## Package 
Pacotes no go é a forma base de declarar tudo, seja para pacotes padrões da linguagem ou para pacotes internos do seu programa, gosto de pensar que é tipo uma forma de declarar o nome de uma factory da vida 

O go obriga vc definir um pacote na 1 linha do arquivo, salvo apenas por comentarios que podem vir antes do package. 
Packages main são sempre compilados pelo go, então a ideia é que vc tenha um package main na sua aplicação que será compilado e chamará todos os outros pacotes, assim como import modules no JS
## Import 
É onde ficam a declaração dos pacotes que importamos sejam eles padrões do go, internos ou de terceiros

- Podemos renomear pacotes inserindo um nome na frente dos mesmos, isso é muito util quando o nome do pacote é muito grande
```go 
import (
	xlx "aleatory/xilendoto-lescical-xexuxuxu"
)
```
> NÃO USAMOS ISSO PARA PACOTES PADRÕES DO GO

- Podemos definir um pacote como `.` fazendo ele ser automaticamente importado no projeto 
```go 
import (
	. "fmt"
)

func main() {
	Println("HelloMyRiPA")
}
```
> Por mais que pareça super interessante não é recomendado e sempre o linter corrigirá esse estilo de import, NÃO USE ELE

- Modo escondido, eu ainda não entendi muito bem isso, mas tem como fazer com que pacotes não sejam listados por padrão dentro do nosso arquivo golang possibilitando que ele seja meio que escondido enquanto esse modo tiver ativo, o modo em questão é colocar o `_` na frente de um pacote golang. 
```go 
impot(
	_ "fmt"
)
```
> Aparentemente isso é necessário para banco de dados 
## Nomes 
Dentro do go podemos definir um nome como publico e privado, em outras linguagens fazemos isso definindo ele na hora da declaração com algo como `Private` ou `Public`, mas no GO isso é muito mais facil. 
Se a variavel tem a primeira letra maiuscula é PUBLICA, se tem a primeira letra minuscula é PRIVADA
```go 
var Bar string = "OI KRL" //Publica
var mesa string = "Publica é o krl" //Privada
```

Quando juntamos essa funcionalidade com a questão dos packages, descobrimos que quando importamos um package, os metodos ou var que estão disponiveis para ser usados são justamente os que estão publicos, o que estão privado só conseguem ser usados dentro do escopo de cada ARQUIVO, caso meu package tenha dois arquivos A.go e B.go e eu declarar uma privada em B, o A não poderá usar. 

Essa condição pode ser quebrada quando usamos a pasta `internal` em um package, ela é responsavel por abriar os arquivos que serão somente usados dentro do package, ou seja por mais que eles estejam publicos eles somente serão acessados dentro do package. 


> É possivel exibir variaveis interna por meio de prints em funções publicas
## Variaveis 

- Podemos definir var em dois contextos, dentro de funções ou em packages.
- Temos que tipar as variaveis e nessa linha variaveis que tem tipos diferentes só podem  ser declarada em linhas separadas.
- Variaveis iguais podem ser declaradas em conjuntos, assim como no C
- As variaveis podem ser inferidas com base no valor padrão das mesmas
### Packages 
Dentro de packages podemos declarar elas assim: 
```go 
var idade = 30 
var idadeInt8 int8 = 10
var Nome, Sobrenome, Apelido string
```
- Elas não tem restrições se não forem usadas, elas continuam podendo ser somente declaradas ali
### Functions 
Dentro de funções podemos declarar as variaveis de um jeito mais simplificado, atribuindo valor e declarando ao mesmo tempo, mas precisamos usar todas que declaramos ou recebemos um erro de compilação

```go
func main() {
	nome := "Pilu"
	jsobrenome := "Vitu"
	var x int8 = 20

	fmt.Println(nome, sobrenome,x)
}
```

