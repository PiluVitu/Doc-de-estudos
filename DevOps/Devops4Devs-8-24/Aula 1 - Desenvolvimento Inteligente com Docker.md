## Comandos básicos

### `docker container ls`
- Comando responsavel por listar os containers ativos, caso queiramos que sejam listados todos os containers devemos passar a flag `-a`.
- É possivel ter o mesmo resultado com o comando `docker ps`, mas essa maneira é uma forma antiga. 
## `docker container run`
- Usamos esse comando para instanciar containers com imagens especificas. 
- Podemos definir um nome para o container com a flag `-name`
- Para poder evitarmos do comando travar o terminal no momento de instanciar o container podemos passar a flag `-d` fazendo com que ele rode em modo detach
## `docker container rm`
- Usamos esse comando para poder deletar containers, para isso passamos o id ou o nome do container logo apos o comando. 
- Podemos passar a flag `-f` para poder excluir a imagem
## 