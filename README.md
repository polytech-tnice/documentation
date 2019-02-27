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

## Descriptioon

Description du projet

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
