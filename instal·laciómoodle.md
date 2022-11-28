#INSTAL·LACIÓ DE MOODLE

Abans de instal·lar moodel hem de instal·lar un LAMP.

jo en aquest cas he utilitzat el Apache:

sudo apt-get install apache2


![image](https://user-images.githubusercontent.com/116022089/204258593-caffb899-9b14-4082-aad1-dd7f6b5f8194.png)

Després haurem de instal·lar el MariaDB

sudo apt-get install mariadb-server

![image](https://user-images.githubusercontent.com/116022089/204258978-244f0625-2ed3-4e9c-9cc2-67592d69574c.png)

De seguit executarem la configuració de mariaDB amb la següent comanda: 

sudo mysql_secure_installation

i la cponfigurem de la seguent manera:

![image](https://user-images.githubusercontent.com/116022089/204261543-3f689f6f-1aab-44eb-aa23-513ecd882215.png)

![image](https://user-images.githubusercontent.com/116022089/204261809-14156896-75fa-4fae-b258-bc2eb4c92df9.png)

Una vegada hem configurat el MariaDB afegirem al repositori el php:

![image](https://user-images.githubusercontent.com/116022089/204262361-c8942bb8-5da7-4e31-8004-02981442ecad.png)

i a continuació instal·larem el php que anteriorment hem afegit al repositori:

sudo apt-get install php7.3 -y

![image](https://user-images.githubusercontent.com/116022089/204263350-45c07482-7d90-4338-9a95-288bdca286cd.png)


1. Primer descarreguem Moodle amb la següent comanda.

wget https://download.moodle.org/download.php/direct/stable400/moodle-latest-400.zip

![image](https://user-images.githubusercontent.com/116022089/203132498-58b1b55f-2553-4a7c-a236-0e00073c4408.png)

2. Després descomprimim l'artxiu.

sudo unzip moodle-latest-400.zip -d /var/www/html/
