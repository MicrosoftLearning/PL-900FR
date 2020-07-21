---
lab:
    title: 'Labo 02 : Application de canevas, Partie 1'
    module: 'Module 03 : Introduction au Common Data Service'
---

# PL-900 : Bases-Microsoft-Power-Platform
## Module 3, Labo 2 : Application de canevas, première partie

Scénario
========

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visites sur le campus sont actuellement enregistrées dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données sur les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel d’administration et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus.  

Dans la partie 1 de ce labo, vous allez concevoir une application de canevas PowerApps qui permettra au personnel de l’université de gérer les visites de ses invités.

Étapes de labo de haut niveau
======================

Nous allons suivre le plan ci-dessous pour concevoir l’application canevas :

-   Créer l’application depuis des données à l’aide du modèle de facteur de forme du téléphone
-   Une page de détail avec des informations sur les visites
-   Une page d’édition à créer pour les visites
-   Un contrôle de galerie pour afficher les visites
-   Ajouter un filtrage sur la source de données de la galerie pour n’afficher que les futures visites

## Conditions préalables

* Achèvement du labo 1 - Modélisation de données

Éléments à considérer avant de commencer
-----------------------------------

-   Quel est le facteur de forme le plus répandu pour le public cible ?
-   Estimer le nombre d’enregistrements dans le système 
-   Comment réduire les enregistrements sélectionnés pour améliorer les niveaux de performance de l’application et l’adoption par les utilisateurs


Exercice \#1 : Créer une application de canevas du personnel 
===============================

**Objectif :** Dans cet exercice, vous allez créer une application canevas depuis un modèle, puis la modifier pour y inclure les données requises

Tâche \#1 : Créer une application de canevas
---------------------------

Dans cette tâche, vous allez créer une application de canevas à l’aide du modèle de disposition du téléphone basé sur Common Data Service. En utilisant Visites comme entité sélectionnée depuis CDS, le modèle génère l’application Galerie - Afficher - Éditer pour gérer les visites sur le campus.

1.  Ouvrez la solution Gestion du campus.

    -   Connectez-vous à <https://make.powerapps.com>

    -   Sélectionnez votre **environnement**.

    -   Sélectionnez **Applications**.

2.  Créer une nouvelle application canevas

    -   Cliquez sur **Nouvelle application | Application canevas**.
    -   Sélectionnez **Mode téléphone** sous **Common Data Service** 
-   Sélectionnez la connexion **Common Data Service**, puis cliquez sur **Créer**
    -   Sélectionnez la table **Visites**
    -   Cliquez sur **Se connecter**
3.  Enregistrer l’application
    1.  Cliquez sur **Fichier > Enregistrer**
    2.  Tapez le nom de l’application comme **Personnel du campus**
    3.  Appuyez sur **Enregistrer**

Tâche \#2 : Configurer le formulaire de détails des visites
--------------------------------

Dans cette tâche, vous allez configurer le formulaire de détails pour afficher les informations sur l’enregistrement de visite individuelle

1.  Développez **DetailScreen1** sous **Arborescence**
2.  Sélectionnez **DetailForm1**
3.  Sélectionnez **Éditer** en regard de la zone **Champs** dans le panneau des propriétés
4.  Cliquez sur **Ajouter un champ**
5.  Sélectionnez les champs suivants :
    * Fin réelle
    * Début réel
    * Bâtiment 
    * Code
    * Fin prévue
    * Début prévu
    * Visiteur
6.  Cliquez sur **Ajouter**
7.  Réorganisez les champs en glissant et déposant les noms de champs vers le haut ou vers le bas. L’ordre recommandé est le suivant :
    * Code, nom, bâtiment, visiteur, début planifié, fin planifiée, début réel, fin réelle
8.  Pour conserver le travail en cours, cliquez sur **Fichier | Enregistrez** puis appuyez sur **Enregistrer** 

## Tâche n°3 : Configurer le formulaire de modification des visites 

Dans cette tâche, vous allez configurer un formulaire pour modifier les informations sur l’enregistrement de visite individuelle

1.  Développez **EditScreen1** sous **Arborescence**
2.  Sélectionnez **EditForm1**
3.  Sélectionnez le champ **Créé sur**, puis appuyez sur la touche **Suppr** pour supprimer le champ
4.  Sélectionnez **Modifier les champs** dans le panneau des propriétés
5.  Cliquez sur **Ajouter un champ**
6.  Sélectionnez les champs suivants :
    * Bâtiment 
    * Fin prévue
    * Début prévu
    * Visiteur
7.  Cliquez sur **Ajouter**
8.  Réorganisez les champs en glissant et déposant les noms de champs vers le haut ou vers le bas. L’ordre recommandé est le suivant :
    * Nom, bâtiment, visiteur, début planifié, fin planifiée
9.  Pour conserver le travail en cours, cliquez sur **Fichier | Enregistrez** puis appuyez sur **Enregistrer** 

Tâche \#4 : Configurer la galerie de visites
---------------------------------------

Dans cette tâche, vous allez configurer la galerie prégénérée pour afficher le titre, les dates de début et de fin de la visite. 

1.  Développez **BrowseScreen1** sous **Arborescence**
2.  Sélectionnez **BrowseGallery1**
3.  Sélectionnez la propriété **TemplateSize** depuis la liste déroulante des propriétés
4.  Remplacez l’expression par la suivante « Min(150, BrowseGallery1.Height - 60) ». Cette action garantit un espace suffisant pour des informations supplémentaires.
5.  Modifiez la galerie en appuyant sur l’icône en forme de crayon dans le coin supérieur gauche de la galerie
6.  Sélectionnez le champ avec la date et l’heure 
7.  Modifiez la propriété **Texte** depuis « ThisItem.'Created On' » vers « ThisItem.'Scheduled Start' »
8.  Sélectionnez à nouveau le champ
9.  Appuyez sur « CTRL-C », puis sur « CTRL-V » pour créer une copie du champ.
10.  À l’aide de la souris ou du clavier, déplacez le contrôle copié vers le bas et alignez-le avec les autres contrôles dans la galerie
11.  Modifiez la propriété **Texte** en « ThisItem.'Scheduled End' »
12.  Pour conserver le travail en cours, cliquez sur **Fichier | Enregistrez** puis appuyez sur **Enregistrer** 

## Tâche n°6 : Ajouter un filtre de date

Étant donné que le nombre de visites augmente continuellement, les utilisateurs ont besoin d’une fonctionnalité pour filtrer la galerie de visites. Par exemple, l’utilisateur peut souhaiter voir uniquement les futures visites. Dans cette tâche, vous ajoutez la possibilité d’afficher les visites uniquement après une date sélectionnée par l’utilisateur.

1. Sélectionnez le menu **Insérer**

2. Cliquez sur **Entrée | Sélecteur de date** 

3. À l’aide du clavier ou de la souris, contrôlez la position sous le champ de recherche.

4. Sélectionnez **BrowseGallery1** 

5. Redimensionnez et déplacez le contrôle de la galerie pour qu’il se trouve sous le sélecteur de date et couvre l’écran.

6. Sélectionnez la propriété **Items**

7. Dans l’expression, recherchez « [@Visits] » et remplacez-le par « Filter(Visits, 'Scheduled End'>= DatePicker1.SelectedDate) ». L’expression complète devrait ressembler à ce qui suit :

   ```
   SortByColumns(
   	Search(
        Filter(
        	Visits,
            'Scheduled End' >= DatePicker1.SelectedDate
           ),
           TextSearchBox1.Text,
       	"bc_code","bc_name"
       ),
     "bc_code",
     If(SortDescending1, Descending, Ascending)
   )
   ```
   
8. Pour conserver le travail en cours, cliquez sur **Fichier | Enregistrez** puis appuyez sur **Enregistrer**

# Exercice n°2 : Finaliser l’application

Au cours de cet exercice, vous testerez l’application. Si elle fonctionne comme prévu, vous l’ajoutez ensuite à votre solution.

Tâche \#1 : Tester l’application
--------------------------

1.  Démarrer l’application

    -   Sélectionnez **BrowseScreen1**, puis appuyez sur **F5** ou cliquez sur **Aperçu de l’application**.
    -   L’application doit se charger et afficher la liste des visites. 
    -   Testez le filtre en sélectionnant différentes dates dans le contrôle du sélecteur de dates
    -   Sélectionnez une visite et vérifiez que le formulaire d’affichage fonctionne correctement
    -   Retournez dans la galerie et appuyez sur + pour créer une nouvelle visite. Vérifiez que le formulaire de modification contient les champs obligatoires, y compris le visiteur, le bâtiment et les dates de début et de fin planifiées.
    -   Renseignez les informations avant l’envoi. Vérifiez que le nouvel enregistrement apparaît dans la galerie.
    -   Appuyez sur le bouton **Échap** pour fermer l’application

2.  Enregistrer et publier l’application

    -   Cliquez sur **Fichier**, puis sur **Enregistrer**.

    -   Cliquez sur Publier.

    -   Cliquez sur **Publiez cette version**.

    -   Cliquez sur **Fermer**.

    -   Fermez l’onglet ou la fenêtre du navigateur du **Concepteur**.

    -   Cliquez sur **Quitter** si vous y êtes invité lorsque vous essayez de fermer la fenêtre du navigateur.

    -   Revenez à la fenêtre précédente et cliquez sur **Terminé**.

## Tâche n°2 : Ajouter une application à la solution et publier 

1. Ouvrez la solution Gestion du campus.
   * Connectez-vous à <https://make.powerapps.com>
   * Sélectionnez votre **environnement**.
   * Sélectionnez **Solutions**.
   * Cliquez pour ouvrir la solution de **Gestion du campus**.
2. Sélectionnez **Ajouter existant | Application | Application de canevas**
3. Sélectionnez l’onglet **Solutions extérieures**
4. Sélectionnez l’application **Personnel du campus**, puis cliquez sur **Ajouter**
5. Sélectionnez l’application **Personnel du campus**, puis cliquez sur **Éditer**
6. Sélectionnez **Fichier | Publier** 

# Défis

* Affichage du calendrier de toutes les visites et filtrage par plage de dates
* Possibilité de créer et de gérer des contacts dans le cadre de l’application
* Comment afficher plusieurs réunions lors d’une seule visite

