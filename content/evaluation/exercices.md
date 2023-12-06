# Évaluation

## Projet : système de gestion de bibliothèque simplifié

**Lisez-bien les instructions avant de commencer à travailler sur le projet !**


### Objectif
Créer un système de gestion de bibliothèque simple qui permette de gérer les livres et les utilisateurs de la bibliothèque.
Le système doit permettre aux utilisateurs d'ajouter et de retirer des livres de la bibliothèque,
de rechercher des livres par titre, par auteur ou catégorie,
d'enregistrer de nouveaux utilisateurs de la bibliothèque,
d'emprunter et de retourner des livres,
et de savoir qui détient un livre.


### Fonctionnalités

1. Ajout et retrait de livres : Permettre à l'utilisateur d'ajouter ou de retirer des livres de la bibliothèque.
2. Recherche de livres : Rechercher des livres par titre, par auteur ou par catégorie.
3. Enregistrement des utilisateurs : Enregistrer de nouveaux utilisateurs de la bibliothèque.
4. Emprunt et retour de livres : Permettre aux utilisateurs d'emprunter et de retourner des livres (si un livre est pris, il n'est plus disponible).
5. Sauvegarde de l'état : Sauvegarder l'état de la bibliothèque dans un fichier au format JSON.


### Design patterns à utiliser

Vous devez idéalement implémenter ces 4 design patterns (et/ou d'autres) et les utiliser dans votre code,
là où vous pensez que cela a du sens,
les utilisations décrites ici sont de simples suggestions.

1. Singleton : Pour gérer une instance unique de la base de données de la bibliothèque.
2. Factory : Pour créer des objets Livre ou Utilisateur.
3. Observer : Pour notifier les utilisateurs lorsqu'un livre recherché devient disponible.
4. Strategy : Pour différentes stratégies de recherche de livres.


### Évaluation

1. Implémentation des patterns : Évaluer comment les étudiants implémentent et utilisent les design patterns mentionnés.
2. Cohérence du code : Vérifier la clarté et la logique du code, ainsi que son organisation, son découpage en classes.
3. Fonctionnalité : Tester si les fonctionnalités clés sont implémentées correctement et fonctionnent comme prévu.
4. Commentaires : Si vous voulez me partager une information, ajoutez des commentaires dans votre code pour m'expliquer ce que vous avez fait et pourquoi.

### Bonus

_Attention:_
_Les bonus ne sont pas obligatoires, mais ils peuvent vous aider à améliorer votre note finale._
_Les bonus ne sont pas évalués si les fonctionnalités principales ne sont pas couvertes._

1. Utiliser SQLite pour stocker les données de la bibliothèque.
2. Exposer l'API de la bibliothèque via une API REST avec le framework Bottle.


### Ressources fournies

1. Vous avez le droit d'utiliser le code fourni dans les exemples de ce cours et les exercices que nous avons fait ensemble.
2. Vous pouvez utiliser internet pour rechercher des informations sur les design patterns et les implémentations en Python.
3. Vous pouvez utiliser ChatGPT _raisonnablement_ pour obtenir de l'aide sur les design patterns et les implémentations en Python.

**Attention**:
Si vous vous inspirez de code trouvé sur internet ou généré par ChatGPT,
faites bien attention parce que je vais évaluer votre code et votre compréhension du code,
et je reconnais assez facilement le code généré par ChatGPT parce qu'il est presque systématiquement incorrect ou de mauvaise qualité.
Inspirez-vous,
mais ne copiez-collez pas sans comprendre ce que vous faites.


### Modalité de rendu

1. Vous devez créer une archive (.zip, .tar ou .tgz) contenant votre code et un fichier README.md de quelques lignes qui explique comment utiliser votre projet.
2. Vous devez envoyer votre archive par email à l'adresse `gilles.chehade@mail-formateur.net` avant la fin de la session.
3. Assurez-vous que j'ai bien reçu votre e-mail (demandez-moi !) et que j'ai pu télécharger votre archive.

Je ferais l'évaluation des différents rendus assez rapidement,
et je vous enverrai un e-mail avec mes commentaires.

