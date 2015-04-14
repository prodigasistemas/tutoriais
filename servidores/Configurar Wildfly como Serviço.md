Para configurar o Wildfly como serviço, usam-se os próprios scripts disponibilizados pelo servidor.

OBS: Este tutorial é dedicado aos usuários Linux.

No linux, os scripts de configuração estão localizados na pasta JBOSS_HOME/bin/init.d.

Esta pasta contem os seguintes arquivos:
- wildfly-init-redhat.sh: para ser usado com distribuições baseadas no Red Hat (RHEL, CentOS)
- wildfly-init-debian.sh: para ser usado com distribuições baseadas no Debian (Debian, Ubuntu)
- wildfly.conf: arquivo que contem as configurações usadas pelos arquivos acima

O primeiro passo é copiar o shell script equivalente a sua distribuição do Linux para dentro da pasta /ect/init.d.

```
cp wildfly-init-redhat.sh /etc/init.d/wildfly
ou 
cp wildfly-init-debian.sh /etc/init.d/wildfly
```

Copie também o arquivo wildfly.conf para um local específico esperado pelos scripts:
```
mkdir –p /etc/default
cp wildfly.conf /etc/default
```

Neste arquivo, ajuste os parâmetros de configuração do servidor:
```
JAVA_HOME=/opt/java/
 
# Location of WildFly
JBOSS_HOME=/opt/wildfly
 
# The username who should own the process.
JBOSS_USER=wildfly
 
# The mode WildFly should start, standalone or domain
JBOSS_MODE=standalone
 
# Configuration for standalone mode
JBOSS_CONFIG=standalone.xml
```

Por fim, usamos o comando chkconfig para efetivamente instalar o serviço.

Primeiramente, adicionamos o shell script do wildfly para a listagem do chkconfig:
```
chkconfig --add wildfly
```
Depois, definimos os níveis da inicialização do serviço:
```
chkconfig --level 2345 wildfly  on
```

Pronto! Para iniciar, use os comandos:
```
/etc/init.d/wildfly start
ou
service wildfly  start
```

e para interromper, use os comandos: 
```
service wildfly  stop
ou
/etc/init.d/wildfly stop
```







