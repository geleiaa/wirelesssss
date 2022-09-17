# Wirelesssss 
***repo p/ links de conteúdos com foco em wifi hacking***
- Atualizações semanais(talvez)



##### Wki de uns caras muito bons em wireless hacking. Nessa wki tem uma introdução/links de várias coisas tipo
o padrão wifi [IEEE 802.11](https://en.wikipedia.org/wiki/IEEE_802.11), link para uma introdução do aircrack-ng,
algumas ferramentas && +++

^
|
\_(https://github.com/rfhs/rfhs-wiki/wiki/WiFi#80211-wireless-standard)

^
|
\_site da comunidade desse pessoal ^^^ (https://www.wirelessvillage.ninja/)

 
 
##### Resumo de vários ataques como DoS, Cracking WEP && WPA, Brute-force WPS, Evil-Twin && 
ataques de "sondagem". E algumas ferramentas que automatizam vários tipos de ataques. 

^
|
\_ (https://book.hacktricks.xyz/pentesting/pentesting-wifi)



##### Blog com vários artigos sobre ataques contra WPA2-Enterprise, ataques KARMA, MANA && mais. É o blog
do desenvolvedor da ferramenta EAPHammer (ou um dos devs). 

^
|
\_ (https://solstice.sh/) 



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



# Ataques

## Handshake capture

|_ Esse ataque é o mais básico entre todos que existem, dependendo do cenário talvez seja o mais fácil.
   Mais no arquivo crackwpa.txt ^^^  
   
|_ (https://beta.ivc.no/wiki/index.php/WPA_Attack) aqui tem uma explicação detalhada sobre como o handshake e feito e outras formas de ataque.

|_ (https://openwall.info/wiki/john/WPA-PSK) resumo da quebra do wpa-psk com JTR e exemplo de captura do handshake.

## Brute-Force do WPS

|_ Uma grande falha de segurança foi revelada em dezembro de 2011 que afeta roteadores sem fio com o recurso WPS PIN, que os modelos mais recentes habilitam por padrão. A falha permite que um invasor remoto recupere o PIN WPS em poucas horas com um ataque de força bruta e, com o PIN WPS, a chave pré-compartilhada WPA/WPA2 da rede (PSK). Isso talvez não é possível em alguns modelos de roteador. Após encontrar as redes com WPS é hora de conhecer o Reaver. Este é um software muito interessante que realiza um ataque de força bruta (brute force) contra o número pin de um Access Point com WPS (WiFi Protected Setup) habilitado. 

|_ (https://en.wikipedia.org/wiki/Wi-Fi_Protected_Setup)

|_ (https://en.wikipedia.org/wiki/Wi-Fi_Protected_Access#WPS_PIN_recovery)

|_ (https://github.com/t6x/reaver-wps-fork-t6x)


## PMKID Attack

|_ (https://hashcat.net/forum/thread-7717.html) 

|_ (https://www.evilsocket.net/2019/02/13/Pwning-WiFi-networks-with-bettercap-and-the-PMKID-client-less-attack/) pmkid attack com bettercap

|_ (https://hashcat.net/wiki/doku.php?id=cracking_wpawpa2) "passo a passo" para o pmkid attack


...

# Ferramentas 

* [aircrack-ng](https://www.aircrack-ng.org/) [github](https://github.com/aircrack-ng)
* [hcxdumptool](https://github.com/ZerBea/hcxdumptool) (https://github.com/ZerBea/hcxdumptool/blob/master/docs/first_steps.txt)
* [Wifite2](https://github.com/derv82/wifite2)  &&  [kali tools](https://www.kali.org/tools/wifite/)
* [wifiphisher](https://github.com/wifiphisher/wifiphisher) && [site wifiphisher](https://wifiphisher.org/)
* [pyrit](https://github.com/JPaulMora/Pyrit)
* [eaphammer](https://github.com/s0lst1c3/eaphammer)  &&  [wiki](https://github.com/s0lst1c3/eaphammer/wiki)
* [bettercap](https://github.com/bettercap/bettercap)  &&  [site](https://www.bettercap.org/)



# Adaptadores && chipsets && drivers

|_ https://deviwiki.com/wiki/List_of_Wireless_Adapters_That_Support_Monitor_Mode_and_Packet_Injection

|_ https://wikidevi.wi-cat.ru/


## Tp-link Archer T4U AC1300 (v3)
![adapt](https://github.com/geleiaa/wirelesssss/blob/main/images/20220820_120235.jpg)

* https://wikidevi.wi-cat.ru/TP-LINK_Archer_T4U_v3
* Driver https://github.com/RinCat/RTL88x2BU-Linux-Driver
* Driver https://github.com/cilynx/rtl88x2bu
* Driver https://github.com/morrownr/88x2bu-20210702

**Caso tenha problemas em usar esse adaptador no VirtualBox você pode tentar 
  alterar essa configuração com a vm desligada e depois inicie >>>**
  
  
**(talvez precise instalar um driver além de fazer essas configs)**  
  
![vm](https://github.com/geleiaa/wirelesssss/blob/main/images/Configuracao_VM_-_Criar_novo_filtro_USB.png)  


**o comando `lsusb` mostrara o Vendor ID e Product ID do adaptador para a config. Exemplo da saida:**  
![id](https://github.com/geleiaa/wirelesssss/blob/main/images/vendorid.png)


* fonte: https://www.systranbox.com/how-to-setup-usb-wifi-adapter-in-virtualbox-kali-linux/
* outra alternativa caso a primeira não der certo: https://null-byte.wonderhowto.com/forum/wifi-hacking-attach-usb-wireless-adapter-with-virtual-box-0324433/
