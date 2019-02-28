# T-Nice Documentation

Documentation du projet T-Nice

## Composantes du projet

- [Serveur Node](https://github.com/polytech-tnice/tnice-backend)
- [Jeu Unity](https://github.com/polytech-tnice/unity-client)
- [Application Mobile](https://github.com/polytech-tnice/mobile-app)

Non utilisé dans l'état actuel du projet :

- [Application Web](https://github.com/polytech-tnice/web-app)

## Membres du groupe

- Quentin Duret
- Julien Lemaire
- Loïc Rose
- Antoine Steyer

## Description

T-Nice est une application ludique permettant d’importer dans un cadre culturel les nouvelles technologies du moment. Nous proposons une expérience unique aux visiteurs du musée du Sport en créant une application multi-supports permettant de jouer au tennis avec un partenaire en utilisant la réalité virtuelle. De plus, les spectateurs du match pourront influencer sur le vent directement dans le match grâce à des smartphones. Nous offrons aussi la possibilité à une personne de prendre le contrôle des caméras durant le match.

## Déploiement

### Prérequis

Pour les joueurs :

- 2 Casques Samsung Gear VR
- 2 Smartphones Samsung Galaxy compatibles avec la VR
- 2 Samsung Gear controller

Pour le serveur de gestion de parties et le serveur unity :

- 1 Ordinateur

Pour les spectateurs-perturbateurs

- 1 smartphone tactile pour chaque personne

Pour controller les caméras en jeu :

- 1 manette XBox (testé avec une One S)
- 1 Ordinateur (qui peut être le même que celui utilisé pour lancer les serveurs nodejs et unity)

### Configuration

Tous les dispositifs doivent être connectés au même Wi-Fi. Certains dispositifs ont besoin d'une configuration manuelle afin de pouvoir communiquer entre eux sur le réseaux.

**Serveur unity** :

Ouvrir le projet unity-client sur Unity, aller dans la partie "Project" de l'IDE, puis dans les Prefabs ouvrir celui qui se nomme `SocketIO TNice`. A droite de l'IDE vous devriez avoir une fenêtre avec une partie "SocketIO Component (Script)" avec un paramètre `url`.

- Si lancé sur le même ordinateur que le serveur nodejs, il faut mettre le paramètre `url` à la valeur : `ws://localhost:3000/socket.io/?EIO=4&transport=websocket`
- Sinon il faut préciser l'IP de l'ordinateur où se trouve le serveur nodejs à la place de `localhost`

Vous pouvez maintenant lancer le serveur unity en appuyant sur le bouton "Play" en haut de l'IDE ou en faisant un "Build & Run" depuis le menu "File" de Unity. Une fois dans le lobby il faut appuyer sur le bouton `Run Server`.

**Casque VR** :

Pour pouvoir installer l'application VR sur un téléphone, il faut récupérer la signature du téléphone sur le site suivant : https://dashboard.oculus.com/tools/osig-generator/ . Il faut ensuite déposer le fichier obtenu dans le dossier `Assets/Plugins/android/assets/`.
Vous pouvez ensuite connecter la manette du Samsung Gear VR au smartphone.

Pour les joueurs, il faut lancer l'applications lorsque le serveur unity est lancé, les joueurs seront automatiquement connectés à la partie.

**Caméras** :

Une fois que le serveur de jeu Unity est lancé on peut se connecter dessus afin de controller les caméras pendant le match en lançant un client Unity depuis l'IDE avec le button "Play" ou en le générant avec "Build & Run" dans le menu "File" de Unity. Une fois sur le lobby il faut renseigner l'ip de l'ordinateur où se trouve le serveur Unity et appuyer sur le bouton "Run Camera".

**Mobile app** :

Pour le deploiement de l'application mobile, il faut tout d'abord cloner le repo sur github ([ici](https://github.com/polytech-tnice/mobile-app)) puis il faut faire la commande: `npm install` pour installer les paquets. 
Ensuite, pour configurer l'IP sur laquelle l'application va taper pour les appels au serveur node, il faut aller dans *src/app/environment.ts* et modifier l'ip dans baseUrl. Pour savoir l'IP qu'il faut, faire la commande: `ipconfig` sur la machine qui a le serveur node (pour windows). 
Puis, pour lancer l'application 2 choix possibles:

- Lancer la commande: `ionic serve` et l'application va se lancer sur le navigateur. Pour installer ionic si vous ne l'avez pas il faut faire la commande: `npm install -g ionic`.
- Pour simuler l'application sur mobile, vous pouvez utiliser soit un emulateur (pour Android il faut Android Studio) soit un telephone android. D'abord il faut faire un build: `ionic cordova build android` puis soit vous emulez sur android en faisant: `ionic cordova emulate android` et pour installer l'APK sur android, faites: `ionic cordova run android` en ayant au prealable branche votre smartphone android et active le debug USB en mode developpeur. 

Voila, vous pouvez normalement tester l'application.
