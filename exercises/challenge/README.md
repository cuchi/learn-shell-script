# Operador de pipe - `|`

Neste exercício temos um arquivo `auth.log`, nele estão registradas as
tentativas de acesso à um servidor.

Para cada tentativa com senha do usuário root inválida, o registro fica no
seguinte formato:
```
Aug 27 07:08:45 ubuntu69 sshd[32447]: Failed password for root from 59.45.175.98 port 54966 ssh2
```

E para cada tentativa de entrar com um usuário inexistente, o registro fica
assim:
```
Aug 27 07:08:54 ubuntu69 sshd[32453]: Failed password for invalid user support from 112.238.72.189 port 34999 ssh2
```

Tendo isso em mente, seu objetivo é extrair os seguintes dados:
* Lista de ips que tentaram (sem sucesso) acessar o servidor
* Lista de nomes inválidos que foram utilizados como tentativa
* Número total de tentativas de acesso
