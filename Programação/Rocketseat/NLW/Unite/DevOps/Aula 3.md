## Kubernets

> Imagem representando o funcionamento do kubernets
![](Pasted%20image%2020240405223152.png)
- Gerenciador de containers, não precisa ser necessáriamente em docker  
- Concorrentes 
	- DockerSwarm(docker)
	- Nomad(hasicorp mesma do terraform)
	
![](Pasted%20image%2020240405224045.png)

- Docker vai rodar dentro de um pod
- Um pod pode executar vários containers   
### Comandos 
- Para iniciar um cluster kubernets
```bash
k3d cluster create nlw-unite --servers 2
```
> Acho interessante ter um docker instalado no ambiente de desenvolvimento para evitar conflitos, tipo docker desktop q integra com wsl

