## ArgoCD
### Senha de ADMIN
Pode ser encontrada dentro de secrets na parte de initial admin secret, ele vem por padrão no BASE64, mas vc consegue decodificar automaticamente pelo lens. 
Se você deseja fazer por linha de comando é o seguinte comando:
```bash
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```
