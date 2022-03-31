# comandos linux
```
ln -s /usr/local/bin/python2.7 /usr/bin/python2
ln -s /usr/lib64/python2.7 python2
```

- verificar python
    > whereis python2

    > ls -l /usr/bin/python*
- deletar link
    > unlink /usr/bin/python
- criar link
    > ln -s /usr/lib64/python2.7 /usr/bin/python2.7

    > cd /usr/bin/

    > ln -s python2.7 python

## install rpm

- instalar rpm
    > rpm -Uvh yum-3.4.3-168.el7.centos.src.rpm

- verificar 
    > rpm -qR yum

## coletando info do systema

> rpm -qa --queryformat "%{NAME}-%{VERSION}-%{RELEASE}-%{ARCH}\n" | sort > /tmp/rpm-list

> ldd /usr/bin/python

- Strace command output

> strace -fxvto /tmp/strace.out yum update 

> which python
> env > /tmp/env.out
> rpm -qf `which yum`
> rpm -Va > /tmp/rpm_va

## copiando um arquivo entre servidores
> scp <user_01>@<ip_01>:/usr/bin/python2.7 <user_02>@<ip_02>:/usr/bin/python2.7

> scp jupyter@<user_02>:/home/jupyter/data 

- processo em htop
> htop -p $(pgrep -d',' -f "jupyter")

## comandos firewalld

listar as portas abertas
> firewall-cmd --list-all

listar servicos
> firewall-cmd --get-services

listar zonas
> firewall-cmd --get-zones

abrir portas o servico
> firewall-cmd --zone=public --permanent --add-service=http

> firewall-cmd --zone=public --permanent --add-port 8080/tcp

reiniciar firewall
> firewall-cmd --reload

## links
* [link red-hat](https://access.redhat.com/solutions/21199)

## Encontre os maiores diretórios no Linux

> du -a | sort -n -r | head -n 5

    du comando: Estimar o uso do espaço no arquivo.
    a : Exibe todos os arquivos e pastas.
    sort comando: Classifica linhas de arquivos de texto.
    -n : Compare de acordo com o valor numérico da string.
    -r : Inverta o resultado das comparações.
    head : Produz a primeira parte dos arquivos.
    -n: Imprime as primeiras 'n' linhas. (Em nosso caso, exibimos as primeiras 5 linhas).

> du -hs * | sort -rh | head -5

## list port and kill

> lsof -i TCP:<port>

## convert executable sh

```
#!/bin/bash

# Verificar o acesso à internet:
net(){
   clear
      ping -w1 www.google.com.br >/dev/null 2>&1
         while [ $? != 0 ]; do
            clear
               echo " __________________________________________"
               echo "|Sem acesso à internet; Verifique a conexão|"
               echo "|__________________________________________|"
                  sleep 2s
                     ping -w1 www.google.com.br >/dev/null 2>&1
         done
   clear
      echo "[Ok] internet conectada..."
}
net
```
> chmod +x internet.sh

## remove logs in shell

> rm -rf *log.{1..36}
