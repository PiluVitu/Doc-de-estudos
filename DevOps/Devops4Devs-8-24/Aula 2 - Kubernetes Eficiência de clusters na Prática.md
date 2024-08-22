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
