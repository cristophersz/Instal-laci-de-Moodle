#INSTAL·LACIÓ DE MOODLE

Abans de instal·lar moodel hem de instal·lar un LAMP.

jo en aquest cas he utilitzat el Apache:

sudo apt-get install apache2


![image](https://user-images.githubusercontent.com/116022089/204258593-caffb899-9b14-4082-aad1-dd7f6b5f8194.png)

Després haurem de instal·lar el MariaDB

sudo apt-get install mariadb-server

![image](https://user-images.githubusercontent.com/116022089/204258978-244f0625-2ed3-4e9c-9cc2-67592d69574c.png)




1. Primer descarreguem Moodle amb la següent comanda.

wget https://download.moodle.org/download.php/direct/stable400/moodle-latest-400.zip

![image](https://user-images.githubusercontent.com/116022089/203132498-58b1b55f-2553-4a7c-a236-0e00073c4408.png)

2. Després descomprimim l'artxiu.

sudo unzip moodle-latest-400.zip -d /var/www/html/
