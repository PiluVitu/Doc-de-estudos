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

## Dockerfile
- Separa dockerfile prod e dev
- Dockerfile serve como extensão de arquivo e podemos usar nome `dev` e `prod` para separar os mesmos.  Ex: `dev.Dockerfile`
### Comandos 

- Buildar um dockerFile
```bash
docker buil -t <nomeDaImagem> .
```
> OBS: Podemos usar a flag `-f` para informar o path de um dockerfile 

- Para listar as imagens que fora buildadas 
```bash
docker image ls
```

- Para rodar alguma imagem que temos no pc, podemos usar 
```
```