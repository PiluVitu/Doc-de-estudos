## Arquitetura Base do kubernets
Kube funciona em uma arquitetura de Klusters, onde eu tenho um conjunto de maquinas que vão fazer 1 de dois papeis possiveis, control plane(orquestra o kluster) e worker nodes(executa os containers)
![](assets/Pasted%20image%2020240822113413.png)
### Control Plane
#### API Server
- Ponto central de comunicação com o kubernets 