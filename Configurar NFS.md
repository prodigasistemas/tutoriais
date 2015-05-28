NFS (Network File System) é um serviço de compartilhamento de diretórios usado nas distribuições Unix.

#Configuração na máquina servidora

Para configurar o serviço, siga os seguintes passos:

1. Download do software 
```
sudo yum install nfs-utils nfs-utils-lib
```

2. Configure o NFS para subir como serviço habilitado
```
chkconfig nfs on 
service rpcbind start
service nfs start
```

3. Configuracao das pastas compartilhadas

Edite o arquivo seguinte arquivo

```
vi /etc/exports
```

Adicionando a linha ao final do arquivo

```
/shared_folder           ip_da_maquina_cliente(rw,sync,no_root_squash,no_subtree_check)
```

Execute o comando para exportar as configurações:
```
exportfs -a
```


