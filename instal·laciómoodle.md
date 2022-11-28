#INSTAL·LACIÓ DEl LAMP

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

#INSTAL·LACIÓ DEl MOODLE

1. Primer descarreguem Moodle amb la següent comanda.

wget https://download.moodle.org/download.php/direct/stable400/moodle-latest-400.zip

![image](https://user-images.githubusercontent.com/116022089/203132498-58b1b55f-2553-4a7c-a236-0e00073c4408.png)

2. Després descomprimim l'artxiu.

sudo unzip moodle-latest-400.zip -d /var/www/html/

![image](https://user-images.githubusercontent.com/116022089/204264257-161160c3-70e4-4faf-b7ea-b3329fe351d1.png)

#CREACIÓ DEL DIRECTORI DE FIXERS

Moodle utilitza un directori per desar fitxers dels usuaris, és recomanable que aquest directori no estigui al mateix directori que el servidor web, però ha de ser un directori amb accés per part del navegador.

Nosaltres, per exemple, crearem el directori moodledata en home.

![image](https://user-images.githubusercontent.com/116022089/204264770-fa61c138-5941-4c20-a607-3701cf2d8e2c.png)

#CONFIGURAR LA BASE DE DADES

Accedeix a la base de dades amb:

sudo mysql -u root -p

![image](https://user-images.githubusercontent.com/116022089/204266136-eb94773f-3e30-4706-87bc-32b77090e948.png)

Crearem un usuari per a moodle, per exemple moodlemanager:

CREATE USER 'moodlemanager'@'localhost' IDENTIFIED BY 'managermoodle';

![image](https://user-images.githubusercontent.com/116022089/204266678-2d76ca65-c3a1-4835-9747-4e8c9bb42ddf.png)

I creem la base de dades per a l'ús de moodle:

CREATE DATABASE moodle;

![image](https://user-images.githubusercontent.com/116022089/204274809-8d7bd255-e6f3-451a-8463-4b55c12f78ef.png)

Finalment, concedeix control sobre la base de dades moodle a l'usuari moodlemanager que hem creat abans:

GRANT ALL PRIVILEGES ON moodle.* TO 'moodlemanager'@'localhost';
FLUSH PRIVILEGES;

![image](https://user-images.githubusercontent.com/116022089/204275194-16d1f716-c0a0-44ee-9472-a5219b1b7876.png)

#CONFIGURAR MOODLE 

Ara obrirem el navegador i hem d'anar al directori on hem guardat Moodle, si ha estat a /var/www/html simplement escriurem al navegador http://192.168.xxx.xxx/moodle/install.php (la vostar ip).

![image](https://user-images.githubusercontent.com/116022089/204298571-1c35edfe-28fb-4577-915e-9d7d99ee789d.png)

Just després Moodle farà una comprovació de requisits, en el nostre cas es troba que falten dos mòduls de PHP que necessitarà Moodle: curl i zip

![image](https://user-images.githubusercontent.com/116022089/204299291-820672b1-5a4e-444e-b0ca-ae15940ced55.png)

Com hem instal·lat PHP només hem de buscar en aptitude els paquets indicats, per a curl:

sudo apt install php-curl

![image](https://user-images.githubusercontent.com/116022089/204299723-4a31b06d-a5e9-4506-8173-d746b68fa0cd.png)

I per a zip:

sudo apt install php-zip

![image](https://user-images.githubusercontent.com/116022089/204300482-5260593a-f841-45fc-81cd-85ef8aa6eace.png)

I després recarregar el servidor web, en el nostre cas en ser Apache:

sudo service apache2 reload

![image](https://user-images.githubusercontent.com/116022089/204302412-3c1dfc99-5857-4eb4-809b-acf9b82b978e.png)



