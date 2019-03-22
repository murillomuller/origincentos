
**################################################**

## INSTALAÇÃO OPENSHIFT CLUSTER UP

**################################################**

### MUDAR SENHA DO ROOT

    sudo -s  passwd root  "Nova senha"  "Confirmar Senha"

### LOGIN SERVIDOR CENTOS DESEJADO

    ssh root@ipdamaquina


>  LIBERE A PORTA 8443 NO FIREWALL


### UPDATE NOS PACOTES EXISTENTES DO SERVIDOR

    yum update -y

### INSTALAR DOCKER

    yum install docker -y

### INICIAR DOCKER

    systemctl start docker

### EDITAR ARQUIVO DAEMON.JSON

    vi /etc/docker/daemon.json

### SUBSTITUIR CONTEUDO DO DAEMON.JSON

    {  
    "insecure-registries": ["172.30.0.0/16"]
    }

### INSTALAR WGET (SE NÃO EXISTIR)

    yum install wget -y

### BAIXAR OKD.IO
#### URL DE PACOTES ORIGIN: [https://github.com/openshift/origin/releases](https://github.com/openshift/origin/releases)

    wget https://github.com/openshift/origin/releases/download/v3.11.0/openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz
    tar -xvf openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit.tar.gz
    mv openshift-origin-client-tools-v3.11.0-0cbc58b-linux-64bit oc

### COLOCAR PASTA DO OC NO PATH

    cd oc
    export PATH="$(pwd)":$PATH
    oc cluster up --public-hostname ipdamaquina.nip.io
