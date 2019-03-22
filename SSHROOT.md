# LOGIN VIA ROOT SSH 

```
  sudo -s
  passwd root
  $ "Nova senha"
  $ "Confirmar Senha"
```
## Editar arquivo sshd
```
vi /etc/ssh/sshd_config
```
### -Substituir valores pelos abaixo
```
PermitRootLogin yes
PasswordAuthentication yes
```

## Reiniciar serviço sshd
```
service sshd restart
```
