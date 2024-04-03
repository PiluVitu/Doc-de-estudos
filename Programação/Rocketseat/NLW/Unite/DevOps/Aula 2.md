## Docker
- Um container docker é efêmero e para persistir os dados de um DB, precisamos de um volume 

#### DockerCompose
- `dependes_on` não verifica a saúde do container, ele só vê se o mesmo subiu e está operante 
- Estudar sobre wait for each para continuar a subida dos containers docker 
##### Docker Network
- serve para principalmente integrar serviços que devem ficar na mesma rede

> OBS: Migrations não devem ser rodadas no docker compose e dockerfile

##### Volumes
- Um local onde os dados não serão perdidos, aqui geralmente salvamos banco de dados 
#### Comandos 
##### Parar um container 
```bash
docker stop <hash do container>
```
##### Remover um container
```bash
docker container rm <hash do container>
```

> OBS: hash do container é encontrado no `docker ps`




## CI
### Github Actions

#### Tags
##### On
- Dizer para o github quando vai acionar a action, seja por push, commit 

#### Dicas
- Quando for gerada uma imagem do docker, devemos seguir algumas boas práticas para nomear a mesma, como inserir o nome do usuário onde essa imagem vai ser deployada no docker hub, nome da aplicação e has do ultimo commit onde a imagem foi feita. Ex: `piluvitu/nlw.services.passin:22f06d2`
