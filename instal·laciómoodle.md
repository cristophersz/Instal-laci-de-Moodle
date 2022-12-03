## INSTAL·LACIÓ DEl LAMP

Abans de instal·lar moodel hem de instal·lar un LAMP.

jo en aquest cas he utilitzat el Apache:

❖ sudo apt-get install apache2

![image](https://user-images.githubusercontent.com/116022089/204258593-caffb899-9b14-4082-aad1-dd7f6b5f8194.png)

Després haurem de instal·lar el MariaDB

❖ sudo apt-get install mariadb-server

![image](https://user-images.githubusercontent.com/116022089/204258978-244f0625-2ed3-4e9c-9cc2-67592d69574c.png)

De seguit executarem la configuració de mariaDB amb la següent comanda: 

❖ sudo mysql_secure_installation

i la configurem de la seguent manera:

![image](https://user-images.githubusercontent.com/116022089/204261543-3f689f6f-1aab-44eb-aa23-513ecd882215.png)

![image](https://user-images.githubusercontent.com/116022089/204261809-14156896-75fa-4fae-b258-bc2eb4c92df9.png)

Una vegada hem configurat el MariaDB afegirem al repositori el php:

![image](https://user-images.githubusercontent.com/116022089/204262361-c8942bb8-5da7-4e31-8004-02981442ecad.png)

i a continuació instal·larem el php que anteriorment hem afegit al repositori:

❖ sudo apt-get install php7.3 -y

![image](https://user-images.githubusercontent.com/116022089/204263350-45c07482-7d90-4338-9a95-288bdca286cd.png)

## INSTAL·LACIÓ DEl MOODLE

1. Primer descarreguem Moodle amb la següent comanda.

❖ wget https://download.moodle.org/download.php/direct/stable400/moodle-latest-400.zip

![image](https://user-images.githubusercontent.com/116022089/203132498-58b1b55f-2553-4a7c-a236-0e00073c4408.png)

2. Després descomprimim l'artxiu.

❖ sudo unzip moodle-latest-400.zip -d /var/www/html/

![image](https://user-images.githubusercontent.com/116022089/204264257-161160c3-70e4-4faf-b7ea-b3329fe351d1.png)

## CREACIÓ DEL DIRECTORI DE FIXERS

Moodle utilitza un directori per desar fitxers dels usuaris, és recomanable que aquest directori no estigui al mateix directori que el servidor web, però ha de ser un directori amb accés per part del navegador.

Nosaltres, per exemple, crearem el directori moodledata en home.

![image](https://user-images.githubusercontent.com/116022089/204264770-fa61c138-5941-4c20-a607-3701cf2d8e2c.png)

## CONFIGURAR LA BASE DE DADES

Accedeix a la base de dades amb:

❖ sudo mysql -u root -p

![image](https://user-images.githubusercontent.com/116022089/204266136-eb94773f-3e30-4706-87bc-32b77090e948.png)

Crearem un usuari per a moodle, per exemple moodlemanager:

❖ CREATE USER 'moodlemanager'@'localhost' IDENTIFIED BY 'managermoodle';

![image](https://user-images.githubusercontent.com/116022089/204266678-2d76ca65-c3a1-4835-9747-4e8c9bb42ddf.png)

I creem la base de dades per a l'ús de moodle:

❖ CREATE DATABASE moodle;

![image](https://user-images.githubusercontent.com/116022089/204274809-8d7bd255-e6f3-451a-8463-4b55c12f78ef.png)

Finalment, concedeix control sobre la base de dades moodle a l'usuari moodlemanager que hem creat abans:

❖ GRANT ALL PRIVILEGES ON moodle.* TO 'moodlemanager'@'localhost';
❖ FLUSH PRIVILEGES;

![image](https://user-images.githubusercontent.com/116022089/204275194-16d1f716-c0a0-44ee-9472-a5219b1b7876.png)

## CONFIGURAR MOODLE 

Ara obrirem el navegador i hem d'anar al directori on hem guardat Moodle, si ha estat a /var/www/html simplement escriurem al navegador http://192.168.xxx.xxx/moodle/install.php (la vostar ip).

![image](https://user-images.githubusercontent.com/116022089/204298571-1c35edfe-28fb-4577-915e-9d7d99ee789d.png)

Just després Moodle farà una comprovació de requisits, en el nostre cas es troba que falten dos mòduls de PHP que necessitarà Moodle: curl i zip

![image](https://user-images.githubusercontent.com/116022089/204299291-820672b1-5a4e-444e-b0ca-ae15940ced55.png)

Com hem instal·lat PHP només hem de buscar en aptitude els paquets indicats, per a curl:

❖ sudo apt install php-curl

![image](https://user-images.githubusercontent.com/116022089/204299723-4a31b06d-a5e9-4506-8173-d746b68fa0cd.png)

I per a zip:

❖ sudo apt install php-zip

![image](https://user-images.githubusercontent.com/116022089/204300482-5260593a-f841-45fc-81cd-85ef8aa6eace.png)

I després recarregar el servidor web, en el nostre cas en ser Apache:

❖ sudo service apache2 reload

![image](https://user-images.githubusercontent.com/116022089/204302412-3c1dfc99-5857-4eb4-809b-acf9b82b978e.png)

# (Error i solució al error)

Al instalar el curl i el zip continua demanant la instal·lació del curl i el zip:

![image](https://user-images.githubusercontent.com/116022089/204332804-f9ca6366-f831-4836-99b0-762833598a19.png)

Per a solucionar el error el que haurem de fer es instal·lar el curl i el zip incloent en la comanda la versió que hem descarregat anteriorment el php, en aquest cas es la 7.3

❖ sudo apt install php7.3-curl

![image](https://user-images.githubusercontent.com/116022089/204333598-918e53a5-8506-41ae-96f2-05b9818e60b9.png)

❖ sudo apt install php7.3-zip

![image](https://user-images.githubusercontent.com/116022089/204333800-c112dd72-9392-4aa6-a7f4-f26e56952174.png)

Resultat de la solució:

![image](https://user-images.githubusercontent.com/116022089/204334658-6060ad5b-f17c-4010-a8d7-a87aca0f52d7.png)

# Continucació de la configuració 

Canviarem la ruta per a després confirmar la ruta del Derectori de Dades:

![image](https://user-images.githubusercontent.com/116022089/204335647-74dca682-3b00-45ea-9bb0-d64df669e1ac.png)

Després seleccionarem el controlador de dades:

![image](https://user-images.githubusercontent.com/116022089/204335917-2e8c7772-b29e-41d0-bea0-265935b740d2.png)

continuarem instal·lant el mbstring:

❖ sudo apt install php7.3-mbstring i després reiniciem el apache2

Abans:

![image](https://user-images.githubusercontent.com/116022089/204357703-8e05bb6a-f7ba-4013-8371-9550687d630d.png)

Després:

![image](https://user-images.githubusercontent.com/116022089/204359810-45f29087-3822-468d-8e78-37e02822e132.png)

## Solució als estats del servidor 

Ens avisen dels següents errors:

![image](https://user-images.githubusercontent.com/116022089/204360300-d30a54ca-1c37-49d3-a378-14f364718016.png)

I per a solucionar els haurem de instal·lar per separat ja que són extensions.

❖ sudo apt install php7.3-gd

![image](https://user-images.githubusercontent.com/116022089/204360538-a7a81f28-1da0-4cc7-aeec-fc68d352f2df.png)

❖ sudo apt install php7.3-intl

![image](https://user-images.githubusercontent.com/116022089/204360756-a7f5d272-57b2-474b-b272-58200abcc826.png)

❖ sudo apt install php7.3-xmlrpc

![image](https://user-images.githubusercontent.com/116022089/204361069-d3ed2619-0590-4b3f-9e4d-9bc4a3f5a065.png)

❖ sudo apt install php7.3-soap

![image](https://user-images.githubusercontent.com/116022089/204361238-fa8220a4-b148-46e2-85de-446f115fda93.png)

Al finalitzar reiniciem el servidor apache

![image](https://user-images.githubusercontent.com/116022089/204361387-1a5d58f5-7d01-4eea-b2bc-f1ca58dd046b.png)

![image](https://user-images.githubusercontent.com/116022089/204361638-de8e0ff5-199f-4922-b918-228ce6cf8ac6.png)

A continuació abans de continuar ens aparexen dos avisos més per últim 

![image](https://user-images.githubusercontent.com/116022089/204362350-20ab9f6b-71c2-479b-8d93-38aa07adb97e.png)

El primer avis és de converitr el http a htpps pero en aquesta vegada no ens interesa canviar aixo, el que si canviarem es el avis del input vars que esn recomana ficar 5000, per a canviar aixo haurem d'accedir al arxiu:

❖ sudo nano /etc/php/7.3/apache2/php.ini

i buscarem la linia del max_input_vars, la descomentarem i li canviem el número:

![image](https://user-images.githubusercontent.com/116022089/204362911-737856e8-73fd-4e2e-a0c6-682af2b197ba.png)

després d'haver fet aixo reiniciem el Apache2.

![image](https://user-images.githubusercontent.com/116022089/204363062-543edb47-1ae8-4a17-89d1-43dbbba66d59.png)

Al clicar continuar començara la instal·lació:

![image](https://user-images.githubusercontent.com/116022089/204363155-92bdfd27-ed5f-4d3c-8e46-2d29e54b74f1.png)


























