# Charlie — suivi bébé, simplement

> Propulsé par Bear80140, un papa fatigué, avec l’aide de l’IA.

Charlie est une petite application web installable (PWA) pensée à la naissance de mon fils. Au début, il s’agissait simplement de noter les tétées sans se demander à quelle heure était la précédente. Puis se sont ajoutés les couches, les siestes, le poids, les soins, les températures, les petits bilans… bref, tout ce qui aide à garder un peu de mémoire quand les nuits sont courtes.

Ce projet est partagé tel quel, sans publicité et sans prétention. J’aimerais surtout voir ce que d’autres parents, développeurs ou curieux pourraient en faire : simplifier des écrans, corriger des bugs, ajouter des idées utiles, améliorer la confidentialité ou créer une version qui leur ressemble.

## Ce que l’application permet de suivre

- Tétées
- Couches et selles
- Sommeil et siestes
- Soins
- Poids
- Température, vomissements et petits bilans
- Routine quotidienne
- Synchronisation en temps réel avec Firebase, si elle est configurée

L’application est une PWA : elle peut s’installer sur un téléphone depuis le navigateur et continuer à fonctionner avec son cache local.

## Important : pas un outil médical

Charlie est un carnet de suivi personnel. Il ne remplace ni un professionnel de santé, ni un avis médical, ni les carnets de santé officiels.

En cas de doute concernant la santé d’un enfant, contactez un professionnel de santé.

## Utiliser le projet

Le projet est volontairement simple : pas de dépendance à installer, pas de compilation, pas de compte imposé.

1. Téléchargez ou clonez le dépôt.
2. Créez votre fichier de configuration Firebase, comme expliqué ci-dessous.
3. Servez les fichiers depuis un petit serveur web local ou un hébergement HTTPS.
4. Ouvrez l’application dans votre navigateur.

> Évitez d’ouvrir directement `index.html` en double-cliquant dessus : certaines fonctions de navigateur, notamment l’installation PWA et le service worker, fonctionnent mieux via un serveur web.

## Configurer Firebase

La synchronisation est optionnelle dans l’idée, mais la version actuelle de l’application attend un fichier `config.js`.

### 1. Créer un projet Firebase

Rendez-vous sur la [console Firebase](https://console.firebase.google.com/) et créez votre propre projet.

Dans ce projet :

1. Ajoutez une application **Web**.
2. Activez **Cloud Firestore**.
3. Récupérez la configuration proposée pour votre application web.

Elle ressemble à ceci :

```js
const firebaseConfig = {
  apiKey: "…",
  authDomain: "…",
  projectId: "…",
  storageBucket: "…",
  messagingSenderId: "…",
  appId: "…"
};
```

### 2. Créer `config.js`

Copiez le fichier `config.js.example` et renommez la copie en `config.js`.

Remplacez ensuite les valeurs fictives par celles de votre projet Firebase :

```js
window.firebaseConfig = {
  apiKey: "VOTRE_API_KEY",
  authDomain: "VOTRE_PROJET.firebaseapp.com",
  projectId: "VOTRE_PROJET_ID",
  storageBucket: "VOTRE_PROJET.firebasestorage.app",
  messagingSenderId: "VOTRE_SENDER_ID",
  appId: "VOTRE_APP_ID"
};
```

Ne publiez pas votre `config.js` personnel dans ce dépôt. Ajoutez bien cette ligne à votre `.gitignore` :

```gitignore
config.js
```

### À propos de la sécurité Firebase

La configuration Firebase visible dans une application web n’est pas, à elle seule, un mot de passe. La protection réelle des données repose sur les règles Firestore et sur l’authentification.

À ce stade, Charlie ne propose pas encore de connexion utilisateur ni de séparation des données par foyer. Il ne faut donc pas déployer une copie publique avec des règles Firestore ouvertes, surtout pour des données concernant un enfant.

C’est une priorité d’évolution du projet : ajouter une authentification simple, des règles Firestore solides et une séparation claire des foyers.

## Contribuer

Vous n’avez pas besoin d’être développeur professionnel pour aider.

- Une idée ou un écran peu pratique ? Ouvrez une discussion ou une issue.
- Un bug ? Décrivez ce que vous avez fait, ce que vous attendiez et ce qui s’est passé.
- Une amélioration de code, de design, d’accessibilité ou de sécurité ? Les propositions sont les bienvenues.
- Une correction dans ce README ? C’est déjà une contribution utile.

L’objectif n’est pas de créer l’application parfaite, mais un outil simple, respectueux et réellement pratique pour les familles.

## Licence

Ce projet est distribué sous licence MIT. Vous pouvez l’utiliser, le modifier, le partager et l’adapter à vos besoins. Voir le fichier [LICENSE](LICENSE).

## Remerciements

Cette application est née d’un besoin très concret, de beaucoup de fatigue, et de conversations avec une IA pour transformer des idées en code.

Si Charlie vous aide, ou si vous lui donnez une nouvelle direction, ce sera déjà une belle suite à l’histoire.

Une question, une idée ou un retour ?  
Vous pouvez ouvrir une issue sur GitHub ou écrire à : **bear80140@proton.me**
