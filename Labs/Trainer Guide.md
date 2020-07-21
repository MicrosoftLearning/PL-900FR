---
lab:
    title: 'Guide de l’instructeur'
    module: 'Module XX : Build de Power Apps'
---

# PL-900 : Bases-Microsoft-Power-Platform
## Guide du formateur

# Environnements

Chaque participant aura besoin d’un environnement CDS (Common Data Service) pour effectuer l’exercice pratique. Les environnements peuvent être approvisionnés par les participants pendant le cours ou être approvisionnés avant la prestation avec les informations d’identification remises aux participants avant le premier exercice.

Les environnements ne nécessitent aucune considération de configuration spécifique, un CDS simple *sans aucun échantillon de données* est tout ce dont vous avez besoin.

Nous vous recommandons de réaliser les labos en tant que participant, et ce avant le début de la formation. 

* La familiarité avec les exercices rendra la prestation plus efficace.
* Les composants de la solution créés au cours de cet exercice peuvent être utilisés au besoin pour vos démos. Les démos ne sont pas nécessaires mais certains les trouvent utiles. Faites-en quelques-uns sur des sujets avec lesquels vous vous sentez le plus à l’aise.

# Vue d’ensemble

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visites sur le campus sont actuellement enregistrées dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données sur les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel d’administration et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Certains participants peuvent penser qu’il est excessif d’effectuer toutes les personnalisations dans le cadre de la solution. Cependant, il est essentiel de développer de bonnes habitudes à conserver après le cours.

> [!IMPORTANT]
> Nous construisons des composants propres aux solutions Power Platform. Les dépendances sont minimes mais le **Labo 1** est critique car le reste des exercices utilise un modèle de données construit au cours de ce labo. Les exemples de données importées au cours du labo rendent la création et le test des applications plus faciles, plus réalistes et plus pertinentes.

Hormis le Common Data Model construit dans le labo 1, il n’y a pas de dépendances entre les différents labos. Les instructeurs doivent expliquer clairement l’objectif de chaque labo et décrire les composants et les techniques de la solution de haut niveau. Les participants devraient ensuite être encouragés à concevoir et à créer leurs propres solutions sans suivre les instructions étape par étape pour chaque exercice.

## Composants

Les composants achevés sont disponibles pour *tous* les exercices. Ils comprennent des applications de canevas, des applications basées sur un modèle, des flux d’automation de l’alimentation, un fichier Power BI pbix, des exemples de données et une carte d’importation de données, ainsi qu’une solution complète exportée, gérée ou non gérée. Les composants ne doivent pas être utilisés comme raccourcis pour terminer les exercices plus rapidement. Au lieu de cela, ils sont utiles comme outil de démonstration et comme point de référence général.

Étant donné que tous les labos du cours dépendent du modèle de données, ce modèle est disponible en tant que solution autonome [CampusDataModel_1_0_0_1.zip](..\Allfiles\CampusDataModel_1_0_0_1.zip). Il peut être importé dans un nouvel environnement suivi de l’exercice n°3 du labo 1 (importation de données). Cela créera un point de départ pour les participants qui n’ont pas pu terminer le labo. Le modèle de données prédéfini donne à ces participants la possibilité de rattraper leur retard et de poursuivre le reste des exercices. 

## Défis

Un certain nombre de défis sont fournis à la fin de chaque labo. Les défis incluent généralement des scénarios plus réalistes car les exercices du cours sont simplifiés pour gagner du temps. Les défis couvrent également des sujets plus avancés que certains participants peuvent trouver utiles.

Utilisez les défis pour lancer une discussion sur les scénarios du monde réel et sur la façon dont les techniques apprises au cours des exercices peuvent être appliquées pour résoudre les défis.

Labos
======================

## Labo 01 Modèle de données

Un modèle de données solide est le fondement des applications construites sur la plateforme. Dans ce labo, nous allons mettre en place un environnement et créer des solutions pour suivre les changements. Nous allons également créer un modèle de données pour prendre en charge les exigences et importer des exemples de données.

Sujets à discuter :

* Quels outils utiliseriez-vous ?
* Comment abordez-vous la modélisation ?
* Par où commencer ?
* Relations 
* Bonnes pratiques concernant l’implémentation d’un modèle de données dans CDS
* Apporter des entités de Common Data Model (par exemple des contacts) : ce qu’il faut inclure.
* Jeux d’exemples de données Dev/test : combien suffisent. Bonnes pratiques concernant la création de jeux de données dev/test.

### Défis

* Envisageriez-vous d’utiliser l’activité de *rendez-vous* dans le cadre de la solution ? Qu’est-ce que cela changerait

  > Un rendez-vous ou toute autre entité d’activité nécessite une compréhension plus avancée de concepts tels que les parties d’activité, le champ Concernant, etc. Dans un premier temps, certains outils de création risquent de ne pas pouvoir fonctionner avec eux, nécessitant de faire appel à des solutions de contournement complexes.

* Comment faire en sorte que la fin planifiée soit ultérieure au début planifié ? 

  > Un bon sujet pour discuter des règles métier 

* Ajoutez la prise en charge de plusieurs réunions au cours d’une seule visite.

  > Relations de type plusieurs-à-plusieurs et défis associés

* Sécurisez l’accès au bâtiment non seulement pour les contacts externes mais également pour le personnel interne.

  >  Une bonne introduction à l’accès aux données internes vs externes, utilisateurs vs contacts, authentifiés vs anonymes. Vous pourriez mentionner l’approche par le portal Power Apps pour traiter les utilisateurs comme des contacts également dans ce but

* Les visites de certains bâtiments nécessitent l’approbation de la direction. Qu’est-ce que le processus d’approbation changerait dans le modèle de données ?

  > Discussion des flux de processus métier et des approbations d’automation de l’alimentation en tant que techniques pour introduire le facteur humain dans les processus

## Labo 02 : Application canevas

Ce labo se compose de deux parties ciblant différents types d’utilisateurs.

Dans la première partie de ce labo, vous allez créer une application canevas Power Apps que le personnel de l’université peut utiliser pour gérer les visites de ses invités.

Dans la deuxième partie de ce laboratoire, vous allez créer une application de canevas Power Apps que le personnel de sécurité utilisera aux entrées du bâtiment pour valider et enregistrer rapidement les visiteurs.

Sujets de discussion

- Facteur de forme de téléphone ou tablette Dispositions réactives (bientôt disponibles en canevas).
- Comment le public cible affecte-t-il la conception de l’application.
- Comment la connaissance d’Excel peut apporter un avantage aux créateurs d’applications (programmation procédurale traditionnelle ou propriétés et syntaxe d’expression de Power Apps)

- Quel connecteur utiliser. Comment le connecteur CDS est maintenant intégré au canevas Power Apps.

- Vérificateur d’application : de nouvelles mesures chaque jour. Assurez-vous de tester à nouveau l’application.

- Accessibilité : ce qui rend une application facilement accessible

### Défis

**1ère partie**

* Affichage du calendrier de toutes les visites et filtrage par plage de dates

  > Composants, discussion sur les contrôles tiers, filtrage efficace des données

* Possibilité de créer et de gérer des contacts dans le cadre de l’application

  > Plusieurs écrans, navigation entre eux

* Comment afficher plusieurs réunions lors d’une seule visite

  > Comment parcourir les relations et les propriétés

**Partie 2**

* Comment éviter une saisie manuelle du code de visite ?

  > Utiliser les capacités de numérisation des appareils mobiles si le visiteur peut afficher un code-barres avec le code. Bonne discussion sur comment et quand générer des codes-barres pour les visiteurs.

* Ajoutez la validation du bâtiment de la visite

  > Ajouter des informations de création au code-barres. Utiliser potentiellement les capacités GPS. 

* Ajoutez la validation de l’heure réelle de la visite par rapport à l’heure prévue de la visite (trop tôt, trop tard, etc.)

  > Manipulation de la date/heure dans des formules et une logique plus complexe.

* Ajoutez l’état détaillé de la visite, par exemple l’affichage et la validation des e-mails du visiteur, la raison du refus d’accès au bâtiment, etc.

  > Accès aux propriétés des entités liées, création d’une interface utilisateur attrayante

* Comment géreriez-vous l’exigence de plusieurs bâtiments / réunions / entrées pendant une seule visite du campus ? Par exemple, une personne peut visiter le campus pendant une journée et au cours de cette journée, elle rencontrera des membres du personnel dans plusieurs bâtiments, à différents moments de la journée. Qu’en est-il d’une seule réunion avec plusieurs participants externes ? Envisageriez-vous d’apporter une entité *rendez-vous* dans la solution ? 

  > C’est un bon sujet, mais potentiellement complexe et long à traiter. Pensez à lancer une discussion et à donner aux élèves une forme de « travail à domicile ». Discutez de la façon dont Power Apps permet une approche itérative de la création d’applications, c’est-à-dire commencez simplement et améliorez au fur et à mesure.

## Labo 03 : Power Automate

Au cours de ce labo, vous allez créer des flux Power Automate pour automatiser différents aspects de la gestion du campus. Ce labo nécessite, en plus du labo 1, une application intégrée à la première partie du labo 2. Ceci est nécessaire pour que les tests d’automatisation puissent être effectués (déclenchement des processus en entrant de nouvelles données)

Sujets de discussion

* Flux dans les solutions
* Connecteurs CDS (environnement standard ou actuel)
* Autres moyens d’automatisation dans Power Platform (workflow en temps réel, automatisation de l’IU)
* Interaction humaine avec les flux : processus d’approbation
* Tester les processus pendant la création
* Partager les flux
* Superviser les processus d’exécution

### Défis

* Ajoutez des informations sur le bâtiment et mappez-les au flux de notification.

  > Utilisation potentielle d’images, de cartes, de services externes pour fournir ces informations.

* Pouvez-vous générer un code-barres pour le code de visite ? Quand cela sera-t-il utile ?

  > Les codes-barres peuvent inclure des informations supplémentaires comme le nom du bâtiment et peuvent être scannés par une autre application, éliminant la saisie manuelle des données. Comment générer les codes-barres ? Vous utilisez des polices de codes-barres ? Images ? Services externes ?

* Comment garantir une mise en forme conviviale des dates dans le corps de l’e-mail ?

  > Localisation dans Power Apps, y compris la mise en forme locale, les devises et les fuseaux horaires.

* Est-il possible de générer un tableau avec les informations des visites qui ont duré trop longtemps et d’envoyer un seul e-mail ?

  > Utilisation de variables, création d’expressions plus complexes, modification du format des e-mails.

## Labo 04 Power BI

Dans ce labo, vous allez créer un tableau de bord Power BI qui visualise les données relatives aux visites sur le campus.

Sujets de discussion

-   À quel public ce rapport est-il destiné ?
-   Comment les participants utiliseront-t-il le rapport ? Appareil courant ? Emplacement ?
-   Comment démarrer la conception et remplir le canevas vide
-   Connectez-vous aux sources de données, créez et affinez le modèle de données 
-   Avez-vous suffisamment de données à visualiser ?
-   Quelles sont les caractéristiques qu’il est possible d’utiliser pour analyser les données sur les visites ?
-   Publier et partager les rapports
-   Accessibilité dans Power BI lors de la création de rapports interactifs

### Défis

* Tableaux de bord et rapports pour inclure les plans du campus et de bâtiment.

  > Importer des cartes, des images et des données externes dans les rapports

* Signaler et analyser les modèles et les tendances des visites.

  > Discussion sur les capacités d’analyse et de traitement des données de Power BI.

* Visualisation des visiteurs restés trop longtemps.

  > Comment rendre les rapports plus attrayants. Parlez de l’intégration de Power Apps dans Power BI pour ajouter des capacités de manipulation de données en réponse aux rapports présentés.

* Diffusion en continu Power BI pour un traitement en temps quasi-réel pour un grand campus.

  > Il s’agit d’un sujet complexe et les solutions risquent d’être hors de portée pour la plupart des participants. Il est néanmoins important de discuter du vieillissement ou de la limite d’âge des données, des instantanés par rapport aux flux, de la fréquence des actualisations des données et des données périmées en général.

## Labo 05 : Application basée sur un modèle 

Dans ce labo, vous allez créer une application Power Apps pilotée par modèle pour permettre au personnel de bureau du campus de gérer les enregistrements de visites sur l’ensemble du campus.

Sujets à discuter :

* Applications basées sur un modèle dans le cadre d’une solution
* Power Apps : applications de canevas ou applications basées sur un modèle. Audience cible et objectifs de l’application.
* Qu’est-ce qui révèle la qualité d’un plan de site ?
* Que faut-il inclure dans une application pour une entité donnée ?
* Applications et rôles, sécurité dans CDS, découpage de l’interface utilisateur dans les applications basées sur un modèle
* Ajustement du modèle de données par rapport à l’ajustement de l’application basée sur un modèle

### Défis

* Sélectionner des vues et des formulaires spécifiques pour les visites et les bâtiments

  > Affinage de l’application pour l’audience cible. Création de vues et de formulaires utiles

* Le personnel de sécurité travaille généralement dans un seul bâtiment. Comment leur fourniriez-vous un moyen simple d’afficher les visites uniquement pour un bâtiment sélectionné ?

  > Personnalisation dans les applications basées sur un modèle, par exemple les vues personnelles. Filtrage et grilles. Vues fixes avant création si le nombre de bâtiments est faible. Sous-grilles (sur le Formulaire de bâtiment)

* Comment limiteriez-vous l’accès à des entités spécifiques ? Par exemple, les bâtiments devraient être en lecture seule pour tous les membres du personnel à l’exception des administrateurs.

  > Rôles de sécurité, découpage de l’interface utilisateur. Vous pourriez parler des données de référence (entités appartenant à l’utilisateur ou à l’organisation)

* Quels tableaux de bord envisageriez-vous d’ajouter à l’application ?

  > Tableaux de bord intégrés, canevas intégré, Power BI intégré