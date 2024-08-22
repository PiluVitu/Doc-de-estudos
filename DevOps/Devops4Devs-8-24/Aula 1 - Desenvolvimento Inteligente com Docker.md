## Comandos básicos 

### `docker container ls`
- Comando responsavel por listar os containers ativos, caso queiramos que sejam listados todos os containers devemos passar a flag `-a`.
- É possivel ter o mesmo resultado com o comando `docker ps`, mas essa maneira é uma forma antiga. 
### `docker container run <image>`
- Usamos esse comando para instanciar containers com imagens especificas. 
- Podemos definir um nome para o container com a flag `-name`
- Para poder evitarmos do comando travar o terminal no momento de instanciar o container podemos passar a flag `-d` fazendo com que ele rode em modo detach
- Podemos fazer o publish de portas com a flag `-p` para conseguirmos acessar o conteudo de um container pelas portas da nossa maquina, logo após a flag passamos as portas seguindo a ordem `<porta da minha maquina>:<porta do meu container>`
### `docker container rm <hash>`
- Usamos esse comando para poder deletar containers, para isso passamos o id ou o nome do container logo apos o comando. 
- Podemos passar a flag `-f` para poder excluir a imagem
### `docker container exec <hash>`
- Comando usado para executar comando para o container docker 
- Podemos passar a flag `-it` para poder entrar em modo interativo e logo após especificar o container, temos que passar o caminho do shell que iremos usar, é bem comum usarmos a `/bin/bash`
### `docker container stop <hash>`
- Comando necessario para parar a execução de um container sem precisar excluir o mesmo. 
### `docker image ls`
- Usado para listar todas as imagens que temos no nosso sistema e informar a sua tag, seu ID, quando foi criada e seu Tamanho
### `docker build <path da imagem>`
- Comando que usamos para poder buildar uma imagem docker, podemos passar o nome para essa imagem com a flag `-t` 
- É importante seguirmos um padrão de nomeclatura para imagens da nossa aplicação, principalmente se as mesmas forem postadas no docker hub. 
- Esse é o padrão ![](assets/Pasted%20image%2020240822104919.png)
## Dockerfile

### Estrutura base 
![](assets/Pasted%20image%2020240822102537.png)
### FROM 
- É onde declaramos a nossa imagem base onde iremos colocar o nosso projeto, é importante esperficicarmos a tag que rodamos nossa aplicação, podemos encontrar as imagens e suas tags no [docker hub](https://hub.docker.com/) 
### WORKDIR 
- É onde definimos o caminho padrão que iremos inserir nossa aplicação no container, é importante definir uma, quando acessamos o container em modo interativo, sempre vamos para a pasta q definimos como workdir na imagem. 

### COPY 
- É o comando que sempre iremos utilizar para copiar algo do nosso diretorio para a imagem do container, assim como para copiar coisas entre imagens(muito usado na estratégia de multi stage building)
- A ordem que deve ser respeitada é o primeiro argumento é oque vc quer copiar do seu diretorio atual e o segundo é para onde deseja mandar no container, quando definimos `.` estamos nos referindo a raiz da nossa imagem que é o workdir.
- É importante lembrar que [glob patterns](https://www.malikbrowne.com/blog/a-beginners-guide-glob-patterns/)  como `*` funcionam como no exemplo da imagem. 
### RUN 
- É onde passamos comandos que queremos que sejam executados dentro do container na hora da criação da nossa imagem
### EXPOSE
- Tag puramente para doc, serve para informamos onde a aplicação irá rodar, é importante principalmente para 3os que irão baixar essa imagem futuramente
### CMD 
- Comando onde irmemos listar o comando que queremos executar no momento que o container for criado. 
- Passamos os argumentos no comando dentro do array