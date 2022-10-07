# Wirelesssss 
***repo p/ links de conteúdos com foco em wifi hacking***
- Atualizações semanais(talvez)



##### Wiki de uns caras muito bons em wireless hacking. Nessa wiki tem uma introdução de várias coisas tipo padrão wifi [IEEE 802.11](https://en.wikipedia.org/wiki/IEEE_802.11), link para uma introdução do aircrack-ng, algumas ferramentas && +++

^
|
\_(https://github.com/rfhs/rfhs-wiki/wiki/WiFi#80211-wireless-standard)

^
|
\_site da comunidade desse pessoal ^^^ (https://www.wirelessvillage.ninja/)

 
 
##### Resumo de vários ataques como DoS, Cracking WEP && WPA, Brute-force WPS, Evil-Twin && ataques de "sondagem". E algumas ferramentas que automatizam esses tipos ataques. 

^
|
\_ (https://book.hacktricks.xyz/pentesting/pentesting-wifi)



##### Blog com vários artigos sobre ataques contra WPA2-Enterprise, ataques KARMA, MANA && mais. Blog de um dos desenvolvedores da ferramenta EAPHammer. 

^
|
\_ (https://solstice.sh/) (site off até o momento, artigos também no medium) 

^
|
\_ (https://medium.com/@s0lst1c3)



##### Blog de um dos desenvolvedores do bettercap. Tem umas coisas interessantes.

^
|
\_ (https://www.evilsocket.net/)



##### Vários artigos sobre wifi hacking.

^
|
\_ (https://null-byte.wonderhowto.com/how-to/wi-fi-hacking/)



##### Livro sobre pentest wifi do Daniel Moreno. No livro tem várias referências dos conteúdos abordados.

^
|
\_ (https://novatec.com.br/livros/pentest-redes-sem-fio/)



##### Syllabus da certificação Offensive Security Wireless Professional (OSWP). Com certeza vai ajudar na pesquisa.

^
|
\_ (https://www.offensive-security.com/documentation/PEN210_syllabus.pdf)



##### Blog com vários artigos sobre wireless e redes no geral (tem muita coisa útil)

^
|
\_ (https://mrncciew.com/)



# Ataques

## Handshake capture

|_ Esse ataque é o mais básico entre todos que existem, dependendo do cenário talvez seja o mais fácil (***mais informações no arquivo crackwpa.md la em cima***).  
   
|_ (https://beta.ivc.no/wiki/index.php/WPA_Attack) aqui tem uma explicação detalhada sobre como o handshake e feito e outras formas de ataque.

|_ (https://openwall.info/wiki/john/WPA-PSK) resumo da quebra do wpa-psk com JTR e exemplo de captura do handshake.

## Brute-Force do WPS

|_ Uma grande falha de segurança foi revelada em dezembro de 2011 que afeta roteadores sem fio com o recurso WPS PIN, que os modelos mais recentes habilitam por padrão. A falha permite que um invasor remoto recupere o PIN WPS em poucas horas com um ataque de força bruta e, com o PIN WPS, a chave pré-compartilhada WPA/WPA2 da rede (PSK). Isso talvez não é possível em alguns modelos de roteador. Outra coisa que vale a pena ressaltar é que existe duas formas de brute-force no WPS. Uma é a **online** que consiste em testar pin a pin até achar o correto. E a outra forma é o brute-force **offline** que é conhecido como pixie-dust attack(***mais informações sobre pixie-dust no arquivo wps_pixiedust.md la pra cima***)

|_ (https://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)

|_ (https://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup#Vulnerabilities)

|_ (https://en.wikipedia.org/wiki/Wi-Fi_Protected_Access#WPS_PIN_recovery)

|_ (https://www.wonderhowto.com/search/wps/)

|_ ferramenta para brute-force on e offline (https://github.com/t6x/reaver-wps-fork-t6x)

|_ ferramenta para brute-force online (https://github.com/kimocoder/bully)


## PMKID Attack

|_ (https://hashcat.net/forum/thread-7717.html) 

|_ (https://www.evilsocket.net/2019/02/13/Pwning-WiFi-networks-with-bettercap-and-the-PMKID-client-less-attack/) pmkid attack com bettercap

|_ (https://hashcat.net/wiki/doku.php?id=cracking_wpawpa2) "passo a passo" para o pmkid attack


...

# Ferramentas 

* [aircrack-ng](https://www.aircrack-ng.org/) - [github](https://github.com/aircrack-ng)
* [reaver](https://github.com/t6x/reaver-wps-fork-t6x) - [kali tools](https://www.kali.org/tools/reaver/)
* [bully](https://github.com/kimocoder/bully) - [kali tools](https://www.kali.org/tools/bully/)
* [pixiewps](https://github.com/wiire-a/pixiewps) 
* [hcxdumptool](https://github.com/ZerBea/hcxdumptool) - (https://github.com/ZerBea/hcxdumptool/blob/master/docs/first_steps.txt)
* [Wifite2](https://github.com/derv82/wifite2) - [kali tools](https://www.kali.org/tools/wifite/)
* [wifiphisher](https://github.com/wifiphisher/wifiphisher) - [site wifiphisher](https://wifiphisher.org/)
* [pyrit (não oficial)](https://github.com/JPaulMora/Pyrit) - [google code](https://code.google.com/archive/p/pyrit/) - [site](https://pyrit.wordpress.com/)
* [eaphammer](https://github.com/s0lst1c3/eaphammer) - [wiki](https://github.com/s0lst1c3/eaphammer/wiki)
* [bettercap](https://github.com/bettercap/bettercap) - [site](https://www.bettercap.org/)



# Adaptadores && chipsets && drivers

|_ https://deviwiki.com/wiki/List_of_Wireless_Adapters_That_Support_Monitor_Mode_and_Packet_Injection

|_ https://wikidevi.wi-cat.ru/


