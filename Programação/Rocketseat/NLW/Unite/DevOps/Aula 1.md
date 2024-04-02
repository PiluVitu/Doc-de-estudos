# Estudar sobre: 
- IAC
- Container Registery 
- Cluster Kubernetes
- Mecanismos de observabilidade 
- K3D, Kind ou Minikube


## K3D 
- Criar uma instancia do Kubernets no meu pc
- Alternativas
	- Kind
	- Minikube
## Kubecti 
- Lidar com a instancia do kubernets 
## Lens
- Interface grafica para o kubernets, tipo o docker desktop acredito, não é necessário
## Heml 
- Funciona como um npm do kubernets
## Terraform 
- Conceitos de IAC

## Docker
### Dockerfile
- Separa dockerfile prod e dev
- Dockerfile serve como extensão de arquivo e podemos usar nome `dev` e `prod` para separar os mesmos.  Ex: `dev.Dockerfile`
### DockerCompose
- Serve
### Comandos 

#### Buildar um dockerFile
```bash
docker buil -t <nomeDaImagem> .
```
> OBS: Podemos usar a flag `-f` para informar o path de um dockerfile 

#### Para listar as imagens que fora buildadas 
```bash
docker image ls
```

#### Para rodar alguma imagem que temos no pc, podemos usar: 
```bash
docker run -p 3001:3333 -d passin:v1
```
- A primeira porta é o que vai funcionar na sua maquina e a outra é a porta exposta pelo docker
> A flag -d é para rodarmos o comando sem ele ficar travando o terminal

#### Para ver quais containers estão rodando podemos usar: 
```bash 
docker ps
```

#### Para rodar o docker compose:
```bash
docker-compose up -d
```
> Se adicionarmos um `--build` ele vai buildar novamente a imagem 

#### Para derrubarmos um container: 
```bash 
docker stop <hash do container>
```
