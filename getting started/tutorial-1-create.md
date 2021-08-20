# Introduction

Le but de ce tutoriel est de montrer comment construire un terrain de jeu basique sur Tech.io.

## Conditions préalables

Tu a juste besoins :
- Git installé sur votre ordinateur.
- Connaissances de base sur Git (clone, push)

Le code source de cette documentation est sur GitHub  ([Documentation GitHub repository](https://github.com/TechDotIO/techio-documentation), n'hésitez pas à faire des propositions pour l'améliorer !)

##Qu'est-ce qu'une aire de jeux - What's a Playground?

Une aire de jeux peut prendre plusieurs formes:

- Article général expliquant un concept (ex: [Genetic Algorithms](https://tech.io/playgrounds/334/genetic-algorithms), [Graph Theory Basics](https://tech.io/playgrounds/5470/graph-theory-basics-engesp))
- Liste des fonctionnalités avancées d'un langage (ex: [Advanced Python Features](https://tech.io/playgrounds/500/advanced-python-features), [7 Features of C++ 17 that will Simplify your Code](https://tech.io/playgrounds/2205/7-features-of-c17-that-will-simplify-your-code))
- Mise en avant d'une technologie (ex: [Reactive Programming with Reactor 3](https://tech.io/playgrounds/929/reactive-programming-with-reactor-3))
- Cours approfondi sur un sujet spécifique ([Using C# LINQ - A Practical Overview](https://tech.io/playgrounds/213/using-c-linq---a-practical-overview))
- De mode d'emploi ([How to iterate (loop) over the elements in a map in Java 8](https://tech.io/playgrounds/5048/how-to-iterate-loop-over-the-elements-in-a-map-in-java-8))
...

La plupart des terrains de jeux contiennent des exemples de code exécutables, mais ce n'est pas obligatoire. 

# Créer votre propre *Playground*

 Vous devez d'abord choisir un modèle pour créer un nouveau terrain de jeu[Create a playground](/new-playground). 

## Modèles *Templates*

Là, vous pouvez choisir un modèle parmi une large sélection de technologies. Il existe deux types de modèles :
- Un modèle "simple" avec des options d'exemple de code limitées mais qui permet de se lancer rapidement *(recommandé pour un premier terrain de jeu)*.
- Un modèle plus avancé avec de nombreuses options -dépendances, tests unitaires, rendu visuel...- comme un vrai projet.

Tous les modèles contiennent un exemple de code fonctionnel et quelques conseils pour vous aider à démarrer.

Vous pouvez également choisir de créer un terrain de jeu vide à partir de zéro.

## Dépôt *Repository*

Un squelette de terrain de jeu basé sur le modèle sélectionné est créé dans un nouveau référentiel git.

Il existe deux options pour choisir le référentiel :
- Sur votre propre référentiel Github. Pour cela, nous avons besoin de votre autorisation *(Nous n'effectuerons aucune action sans votre approbation. Vous pouvez révoquer l'accès depuis vos paramètres GitHub à tout moment)*. Cela permettra une meilleure collaboration avec la communauté car elle pourra creuser votre terrain de jeu et proposer des améliorations et des traductions. *(conseillé)*
- Sur notre référentiel privé Tech.io. Pour cela, vous devez être authentifié sur la plateforme Git de Tech.io. 

::: Authentification sur la plateforme Git de Tech.io

To do so, you need to add a SSH key to your profile.

Si vous n'avez pas encore de clé SSH, exécutez-la `ssh-keygen` dans ton terminal. Cette commande crée une clé publique et une clé privée utilisées pour accéder à votre référentiel. (Consultez l'[aide de GitHub](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent) pour plus d'informations).

Par défaut, la clé publique se trouve dans  `~/.ssh/id_rsa.pub`. Copiez votre clé publique dans votre [page de paramètres](/settings/ssh).

Maintenant que votre clé a été ajoutée, vous pouvez cloner votre référentiel en utilisant l'URL d'origine fournie sur la page du terrain de jeu :

```bash
  git clone git@ssh.git.tech.io:cg123456/playground-hash.git
```

:::

# Structure de votre terrain de jeu
Maintenant que vous avez créé le référentiel, examinons la structure des dossiers :
- `techio.yml`: Ce fichier obligatoire décrit la structure de votre aire de jeux. Il doit être présent à la racine du dépôt git du terrain de jeu. Il contient : la table des matières du terrain de jeu, les références aux fichiers de cours, et quelques autres détails techniques pour une utilisation avancée (voir l'exemple [techio.yml](/reference/reference-techioyml.md)).
- `cover.png`: Cette petite image (140x76) le long de votre terrain de jeu dans la [page d'exploitatoin](https://tech.io/explore). Par défaut, c'est le logo de la technologie que vous avez choisie.
- Le dossier `markdowns` ou le fichier `statement.md`: Chaque fichier de démarque correspond à une page. Un terrain de jeu d'une page ne contiendra que le fichier `statement.md`à la racine. Sinon, tous les fichiers seront contenus dans le dossier`markdowns` .
*Markdown est une syntaxe simple pour le formatage de base (liens, images, texte de citation, extraits de texte au format de code, etc.). Vous pouvez trouver une aide-mémoire pour la démarque [ici](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).*
- Le dossier `project` ou rien: ce dossier contient les fichiers utilisés dans vos exercices de codage. Nous le décrirons plus tard dans la section [Ajouter un exercice de codage](/getting%20started/tutorial-3-coding-exercise.md) de la documentation.  Dans un modèle simple, ce dossier est absent, car des échantillons de codes sont ajoutés directement dans le démarque à l'aide d'[extraits de code](/markdown/markdown-snippet.md).

# Mettre à jour votre terrain de jeu *Playground*

## Changer le titre et rédiger une introduction

Dans le fichier `tech.io.yml`, mettre à jour le titre:

```yml
title: Mettez votre titre de terrain de jeu ici
plan:
  - title: Bienvenue
    statement: markdowns/welcome.md
```
Ensuite, soit dans votre fichier markdown `statement.md` ou votre répertoire `markdowns/welcome.md`, écrivez une introduction:

```markdown
# Hello world,

Bienvenue sur ce terrain de jeu sur cette technologie étonnante. je vais te montrer comment utiliser le langage de balisage Markdown ...
```

## Ajout d'une nouvelle page
Si vous souhaitez ajouter une nouvelle leçon, procédez comme suit ::

- Créer un fichier markdown : `markdowns/part2.md`
- Modifiez votre fichier markdown et ajouter du contenu
- Référencez ce nouveau fichier dans `techio.yml`:

```yml
title: Mettez votre titre de terrain de jeu ici
plan:
  - title: Part 1
    statement: markdowns/welcome.md
  - title: Part 2
    statement: markdowns/part2.md
```

## Déploiement des modifications sur Tech.io

Valider et pousser un changement dans votre branche `master` déclenchera automatiquement une construction du terrain de jeu et le mettra à jour sur Tech.io. Utilisez les commandes git suivantes :

```bash
git commit -a -m "Titre et introduction"
git push origin master
```

Revenez à votre page de jeux sur Tech.io. Il aurait dû se rafraîchir. Cliquez sur "Aperçu" pour jouer avec votre terrain de jeu.


# Partager votre terrain de jeu

## Partage d'un lien d'aperçu

Même si votre terrain de jeu n'est pas publié, vous pouvez partager son lien d'aperçu qui ressemble à ceci :

https://tech.io/playgrounds/super_long_id/title_of_the_playground

Chaque fois que vous envoyez des modifications à votre terrain de jeu, la référence *super_long_id* est mis à jour.
## Publication de votre terrain de jeu

Un terrain de jeu publié est visible dans la [page ](https://tech.io/explore/latest) qui référence les derniers ajouts . *Pour maintenir la qualité des aires de jeux affichées, nous vous recommandons de ne pas publier votre aire de jeux de test.*

Une fois qu'un terrain de jeu est publié, la référence *super_long_id* devient *short_id* qui rend l'url beaucoup plus conviviale.

## Mises à jour

Une fois qu'un terrain de jeu est publié et disponible pour la communauté, vous pouvez le mettre à jour librement avec des améliorations et utiliser l'aperçu pour voir les résultats impactant les lecteurs. Une fois que vous en êtes satisfait, vous pouvez publier la nouvelle version et les utilisateurs verront les changements.
