## Arquitetura Base do kubernets
Kube funciona em uma arquitetura de Klusters, onde eu tenho um conjunto de maquinas que vão fazer 1 de dois papeis possiveis, control plane(orquestra o kluster) e worker nodes(executa os containers)
![](assets/Pasted%20image%2020240822113413.png)
### Control Plane
#### API Server
- Ponto central de comunicação com o kubernets 
#### ETCD 
- Banco chave e valor que armazena as informações do meu cluster 
#### Scheduler
- Responsavel por definir em qual node os containers serão executados 
#### Controller Manager
- Gerencia os controladores que mantem o estado desejado do cluster
### Worker Nodes
#### Kublet 
- Ele quem garante a execução dos containers se comunicando com o container runtime 
#### KubeProxy
- Gerencia a comunicação de rede no cluster  

### OBS:
Algumas pessoas dizem que aprender docker pode ser inutil com o kubernets, pois ele não suporta mais a execução de containers com o docker. 
Isso é uma meia verdade, kubernets realmente não suporta mais docker, e utiliza o containerD ou Crio para gerenciar os containers, mas essas 2 tecnologias tem algo em comum com o docker, a padronização na criação de container e imagens.
O que nos permite usar o docker para criar as imagens e aproveitar a mesma imagem na hora de instanciar o meu kluster

### Deploy 
#### Nodes
- Menor objeto do cluster kube é aqui onde são executados os meus containers.
#### ReplicaSet
- Responsavel por gerenciar os pods, garantindo a quantidade certa de pods e mantendo o bom funcionamentos dos mesmos, fazendo com que quando a imagem base para o pod seja mudada ele mate e suba novos pods de maneira cadenciada e intervalada, tendo assim 0 downtime 
#### Deployment
- Gerencia o replicaset, fazendo com que quando tenha uma nova atualização da imagem que uso no meu pod, ele cria um novo replicaset, deixando assim uma copia de segurança facilitando um futuro rollback. 
## Como criar um kluster kubernets

### on Premise 
Vc gerencia o ambiente, tem mais controle, mas aumenta a complexidade 

### Kurbenetes as a services
Serviço gerenciado pelos clouds providers

### Ambiente local
minikube, kind, k3d, onde essas ferramentas criam clusters kubernets com base em containers docker  

## Criando cluster com k3d 

### Requisitos 
- Docker
- k3d
- kubectl

### Comandos

#### `k3d cluster create <nome>`
- --servers 3 (control planes)
- --agents(worker nodes) 


#### `k3d cluster list`

#### `k3d cluster delete <nome>`

#### `kubectl get nodes`

#### `kubectl api-resources`

#### `kubectl apply`
- Serve para aplicar as configurações definidas no arquivo manifesto, passamos a flag `-f` para poder especificar onde o arquivo se encontra.