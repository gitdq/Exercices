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
