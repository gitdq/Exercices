# Exercices-exo1 sous Centos

1) Installer Nodejs dans l'environnement de Docker:
  ==> sudo yum install nodejs
2) Positionner le PATH=$PATH:$HOME/bin:/usr/bin dans le .bash_profile car le binaire node se trouve sous /usr/bin
3) Vérifier que nodejs est bien installé:
  ==> node -v
4) Installer npm dans l'environnement de Docker:
  ==> sudo yum install npm (npm est embarqué dans l'install de nodejs)
5) Vérifier que npm est bien installé:
  ==> npm -v
6) Comment tester le fonctionnement après l'installation:
  ==> vi hello_world.js
7) Ajouter le code dans le fichier:
   const http = require('http');
   const port = 3000;
   const ip = '0.0.0.0';

   http.createServer(function (req, res) {
     res.writeHead(200, {'Content-Type': 'text/plain'});
     res.end('Hello World');
   }).listen(port, ip);

   console.log(`server is running on ${ip}:${port}`);
  
 8) lancer ==> node hello_world.js
    Résultat: 
    server is running on 0.0.0.0:3000
 9) Tester via le navigateur: http://192.168.0.11:3000 (192.168.0.11 = IP du host)
    ==> resultat : Hello World
    
    
 **************************************************************************************************************************

exo2: L'objectif est de démarrer une application via Dockerfile from Scratch
      Constuire ne image à partir en allant récupérer le Centos en .zip

- Récupérer le fichier : CentOS-7-20140625-x86_64-docker_01.img.tar.xz
   - wget https://buildlogs.centos.org/centos/7/docker/CentOS-7-20140625-x86_64-docker_01.img.tar.xz

- Créer une fichier Dockerfile 
   - vi Dockerfile
- Ajouter dans le fichier Dockerfile les lignes ci-dessous :
   - FROM scratch
   
- Prends le fichier "CentOS-7-20140625-x86_64-docker_01.img.tar.xz", et extrait le à la racine "/"
   - ADD CentOS-7-20140625-x86_64-docker_01.img.tar.xz /
   (Docker construira votre image en s'appuyant sur le fichier zip Centos récupéré avec wget)
   
- Lancer un Build pour construire i'image
   - docker build .
   
- Donner un nom à votre build, de manière à ne pas avoir à mémoriser par coeur les id   
   - docker tag 0f64c7ae0987 localhost:5000/imcentos
   
- Pusher dans le registry
   - docker push localhost:5000/imcentos
   
- Demarrer le conteneur avec l'image
   -  docker run -it localhost:5000/imcentos:latest bash
     
 **************************************************************************************************************************
 
 exo3:l'objectif est de démarrer une application Node (en utilisant un Dockerfile)
 
 1) Créer un dossier my-projet-node
    - mkdir my-projet-node
 2) créer un fichier Dockerfile dans ce répertoire
    - vi my-projet-node/Dockerfile
 3) Utiliser l'image "my-node" du reigstry local :localhost:5000/my-node
 4) Installer npm
 5) Importer le code source dans l'image (ex sous /app/
 6) Sepossitionner sous /app
 7) lancer npm install
 8) Exposer le port 
 
 
 
