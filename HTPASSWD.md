## INSTALAR HTPASSWD

    yum install httpd-tools

## CRIAR ARQUIVO

    htpasswd -c </path/to/users.htpasswd> <user_name>

## ADICIONAR USUÁRIO

    htpasswd </path/to/users.htpasswd> <user_name>

## REMOVER USUÁRIO

    htpasswd -D </path/to/users.htpasswd> <user_name>

### NA MASTER-CONFIG.YAML DO OPENSHIFT

    oauthConfig:
      ...
      identityProviders:
      - name: my_htpasswd_provider 
        challenge: true 
        login: true 
        mappingMethod: claim 
        provider:
          apiVersion: v1
          kind: HTPasswdPasswordIdentityProvider
          file: /path/to/users.htpasswd
