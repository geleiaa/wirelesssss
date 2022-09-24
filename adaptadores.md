## ***Aqui vai algumas informações sobre adaptadores que já usei e como resolver problemas com alguns deles*** ...


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
