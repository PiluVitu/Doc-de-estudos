## Tipos de blocos 

![](assets/Pasted%20image%2020240825220635.png)
![](assets/Pasted%20image%2020240825220657.png)![](assets/Pasted%20image%2020240825220705.png)
![](assets/Pasted%20image%2020240825220716.png)
![](assets/Pasted%20image%2020240825220744.png)
![](assets/Pasted%20image%2020240825220748.png)
## OBS: 
- Uma boa pratica é usar as configurações do terraform em outro repo, já que ele é algo voltado para a infraestrutura em geral. 
- O ideal é que os secrest fiquem em outro lugar e nao no repo, podemos usar os vaults dos proprios providers se pah.

## Como executar 
- Entramos dentro de onde o arquivo terraform está  
- Rodamos um `terraform init` 

### `terraform plan`
- Ele le o aqrquivo terraform e vê se o mesmo é compativel, e da um planejamento de quais e o que os serviços terão.

### Terraform state
- Estado atual da sua aplicação no provider 
- Não é uma boa prática armazenar eles em um postgress ou nos cloud providers
- **POR DEUS NÃO PERCA ESSE ARQUIVO**

### Variables
![](assets/Pasted%20image%2020240825232623.png)
- Devemos criar um arquivo terraform.tfvars que serve como um env.file 

### `terraform destroy`
- Dessa forma eu deleto todo serviço que tenho declarado no meu arquivo tf