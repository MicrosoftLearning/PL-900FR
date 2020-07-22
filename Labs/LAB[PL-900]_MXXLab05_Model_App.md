---
lab:
    title: 'Labo 5 : Application basée sur un modèle'
    module: 'Module XX : Build de Power Apps'
---

# PL-900 : Bases-Microsoft-Power-Platform
## Module X, Labo 5 - Application basée sur un modèle

Scénario
========

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visiteurs du campus sont actuellement enregistrés dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données sur les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel d’administration et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Dans ce labo, vous allez créer une application Power Apps pilotée par modèle pour permettre au personnel de bureau du campus de gérer les enregistrements de visites sur l’ensemble du campus.

Étapes de labo de haut niveau
======================

Dans le cadre de la création de l’application basée sur un modèle, vous effectuerez les opérations suivantes :

-   Créer une nouvelle application pilotée par modèle nommée Gestion du campus

-   Modifier la navigation de l’application pour référencer les entités requises

-   Personnaliser les formulaires et les vues des entités requises pour l’application

Nous travaillerons avec les composants suivants :

- **Vues** : Les vues permettent à l’utilisateur d’afficher les données existantes dans le formulaire
d’un tableau.

- **Formulaires** : C’est là que l’utilisateur crée ou met à jour de nouveaux enregistrements dans les entités.

Les deux seront intégrés à l’application basée sur un modèle pour une meilleure expérience utilisateur.

## Conditions préalables

* Achèvement du labo 1 - Modélisation de données

Éléments à considérer avant de commencer
-----------------------------------

-   Quels changements devons-nous apporter pour améliorer l’expérience utilisateur ?

-   Que devrions-nous inclure dans une application pilotée par modèle basée sur le modèle de données que nous avons créé ?
    
-   Quelles personnalisations peuvent être effectuées sur le plan du site d’une application pilotée par modèle ?


Exercice \#1 : Personnaliser les vues et les formulaires
=======================================

**Objectif :** Dans cet exercice, vous allez personnaliser les vues et les formulaires des entités personnalisées qui seront utilisées dans l’application pilotée par modèle.

Tâche \#1 : Modifier le formulaire de visite
-----------------------------------

1.  Connectez-vous à <https://make.powerapps.com> si ce n’est pas encore fait.
2.  Sélectionnez votre **environnement**.
3.  Sélectionnez **Solutions**.
4.  Cliquez pour ouvrir la solution de **Gestion du campus**.
5.  Cliquez pour ouvrir l’entité **Visite**.
7.  Cliquez sur l’onglet **Formulaires** et sélectionnez le type de formulaire **Principal**. Par défaut,
    le formulaire comporte deux champs, Nom (Champ principal) et Propriétaire.
7.  Ajoutez les champs suivants sous le champ **Propriétaire** en faisant glisser les champs vers le formulaire ou en double-cliquant simplement sur les noms de champ :
    * **Bâtiment**
    * **Visiteur**
    * **Début prévu**
    * **Fin prévue**
    * **Début réel**
    * **Fin réelle** 
8.  Faites glisser le champ **Code** et déposez-le dans l’en-tête du formulaire. (Vous devrez peut-être réduire le panneau Propriétés sur le côté droit de l’écran pour voir le champ sur le formulaire.)
9.  Dans le panneau Propriétés, activez l’option du champ **Lecture seule**
10.  Sélectionnez le champ **Propriétaire** puis, dans le panneau Propriétés remplacez la valeur du champ **Étiquette de champ** par **Hôte**
11.  Cliquez sur **Enregistrer** et attendez la fin de l’enregistrement.
12.  Cliquez sur **Publier** et attendez la fin de la publication.
13.  Cliquez sur le bouton Précédent du navigateur. Vous devriez maintenant revenir au niveau
     de l’onglet Formulaires de l’entité Visite.

## Tâche \#2 : Modifier les vues de visite

Dans cette tâche, nous allons modifier la vue des visites actives par défaut et créer une nouvelle vue pour les visites d’aujourd’hui.

1.  Sélectionnez l’onglet **Vues** et cliquez pour ouvrir la vue **Visites actives**.
2.  Ajoutez les champs suivants à la vue en cliquant sur ou en faisant glisser-déposer les champs :
    1.  **Code**
    2.  **Visiteur**
    3.  **Bâtiment**
    4.  **Début prévu** 
    5.  **Fin prévue**
3.  Cliquez sur l’icône en chevron de la colonne **Créé sur** et sélectionnez **Supprimer**. Le champ **Créé sur** sera maintenant supprimé de la vue.
4.  Cliquez sur l’icône en chevron de la colonne **Nom** et sélectionnez **Supprimer**. Le champ **Nom** sera maintenant supprimé de la vue.
5.  Dans le panneau Propriétés, affichée dans le volet droit, cliquez sur **Trier par** et sélectionnez **Début programmé**. Cliquez à nouveau sur **Début programmé** pour changer l’ordre en descendant (nouvelles visites en haut).
6.  Redimensionnez les colonnes individuelles pour qu’elles correspondent aux informations présentées.
7.  Cliquez sur **Enregistrer** et attendez la fin de l’enregistrement.
8.  Cliquez sur **Publier** et attendez la fin de la publication.
9.  Nous allons maintenant cloner la vue afin de créer une nouvelle vue pour les visites d’aujourd’hui. Cliquez sur « x » à côté du filtre existant dans le panneau Propriétés pour supprimer le filtre.
10.  Appuyez sur le chevron à côté du bouton **Enregistrer** (attention à ne pas appuyer sur le bouton lui-même) et sélectionnez **Enregistrer sous**.
11.  Changez le nom en **Visites du jour** et appuyez sur **Enregistrer**.
12.  Appuyez sur le lien **Modifier les filtres** dans le panneau Propriétés.
13.  Cliquez sur **Ajouter**, puis sélectionnez **Ajouter une ligne**.
14.  Sélectionnez le champ **Début programmé**, puis sélectionnez  la condition **Aujourd’hui**. Appuyez sur **OK** pour enregistrer la condition.
15.  Ajoutez les champs **Début réel** et **Fin réelle** à la vue. Étant donné que nous ne filtrons plus l’état de la vue, nous verrons toutes les visites d’aujourd’hui, y compris les visites terminées. Ces champs permettront de différencier les visites terminées et les visites en cours.
16.  Cliquez sur **Enregistrer** et attendez la fin de l’enregistrement.
17.  Cliquez sur **Publier** et attendez la fin de la publication.
18.  Cliquez sur le bouton Précédent du navigateur.

Exercice \#2 : Créer une application pilotée par modèle
=============================================

**Objectif :** Au cours de cet exercice, vous allez créer l’application pilotée par modèle, personnaliser le plan du site et tester l’application.

**Remarque :** Vous verrez plusieurs champs non traités lors de la création de votre application, en particulier sur les étapes du plan du site. Nous avons pris quelques raccourcis dans le cadre de la réalisation des labos. Dans un projet réel, vous donneriez à ces éléments des noms logiques.

Tâche \#1 : Création d’une application 
----------------------------

1.  Ouvrez la solution Gestion du campus si vous n’y êtes pas déjà.

    -   Connectez-vous à <https://make.powerapps.com>

    -   Dans votre environnement, cliquez pour ouvrir la solution **Gestion du campus**
        .
2.  Créer une application pilotée par modèle

    -   Cliquez sur **Nouveau** et sélectionnez **App**,puis **Model-Drive App**. Cela va ouvrir un nouvel onglet.
    -   Activez la case à cocher **Utiliser la solution existante pour créer l’application**
    -   Saisissez **Gestion du campus** dans le champ Nom et cliquez sur **Suivant**.
    -   Sélectionnez la solution **Gestion du campus** dans la liste déroulante, puis cliquez sur **Terminé**.
3.  Cliquez sur l’icône en forme de crayon affichée en regard du champ **Plan du site.**
4.  Modifiez les titres par défaut

    -   Sélectionnez **Nouvelle zone**.

    -   Accédez au volet des propriétés et saisissez **Campus** pour **Titre**.

    -   Sélectionnez **Nouveau groupe**.

    -   Allez dans le volet **Propriétés** et saisissez **Sécurité** pour **Titre**.
5.  Ajoutez l’entité Contact au plan du site

    -   Sélectionnez **Nouvelle sous-zone**.

    -   Accédez au volet **Propriétés** et sélectionnez **Entité** dans la liste déroulante
        comme **Type**.

    -   Recherchez l’entité **Contact** dans la liste déroulante pour **Entité**.
6.  Ajoutez l’entité Visite au plan du site

    -   Sélectionnez le groupe **Sécurité** et cliquez sur **Ajouter**.

    -   Sélectionnez **Sous-zone**.

    -   Allez dans le volet **Propriétés**.

    -   Sélectionnez **Entité** dans la liste déroulante pour **Type** et recherchez
        l’entité **Visite** dans la liste déroulante pour **Entité**.
7.  Ajoutez l’entité Bâtiment au plan du site

    -   Sélectionnez la zone **Campus** et cliquez sur **Ajouter**.
-   Sélectionnez **Nouveau groupe**.
    -   Saisissez **Réglages** pour **Titre** dans le volet **Propriétés**.
-   Cliquez sur **Ajouter**.
    -   Sélectionnez **Sous-zone**.
-   Allez dans le volet **Propriétés**.
    -   Sélectionnez **Entité** dans la liste déroulante pour **Type** et recherchez l’entité **Bâtiment** dans la liste déroulante **Entité**.

8.  Cliquez sur **Enregistrer**. Cela affichera l’écran de chargement pendant l’enregistrement des modifications.

9.  Cliquez sur **Publier** pour publier le plan du site et attendez la fin de la publication.
10.  Cliquez sur **Enregistrer et fermer** pour fermer l’éditeur du plan du site.
11.  Vous verrez que les éléments des entités qui ont été ajoutés au plan du site sont
     maintenant tous dans l’application.
12.  Cliquez sur **Enregistrer** pour enregistrer l’application.
13.  Cliquez sur **Valider** pour valider les modifications effectuées dans l’application. Quelques avertissements s’afficheront, mais nous pouvons les ignorer, car nous n’avons pas référencé une vue et un formulaire spécifiques pour les entités. Les utilisateurs auront accès à toutes les vues et formulaires pour les entités **Visite** et **Bâtiment**.
14.  Cliquez sur **Publier** pour publier l’application et attendre la fin de la
     publication.
15.  Cliquez sur **Enregistrer et fermer** pour fermer le concepteur d’application.
16.  Cliquez sur **Terminé**.
17.  Sélectionnez **Solutions**, puis cliquez sur **Publier toutes les personnalisations**.
18.  Sélectionnez **Applications**. Votre application devrait maintenant être répertoriée.

Tâche \#2 : Application de test
--------------------------

1.  Démarrer l’application

    -   Sélectionnez **Applications** et cliquez pour ouvrir l’application **Gestion du campus** dans une nouvelle fenêtre. (Si vous ne voyez pas votre application au début, vous devrez peut-être actualiser votre navigateur.)

    -   L’application doit démarrer.
2.  Créer un enregistrement de contact

    -   Sélectionnez **Contacts**.

    -   Cliquez sur **Nouveau** dans le menu supérieur.

    -   Dans **Prénom**, indiquez **John** puis, dans le champ **Nom de famille**, indiquez **Doe**.

    -   Cliquez sur **Enregistrer et fermer**.

    -   Vous devriez maintenant voir le contact créé dans la vue **Contacts actifs**.
3.  Créer un enregistrement de bâtiment

    -   Sélectionnez **Bâtiment** dans le plan du site.

    -   Cliquez sur **Nouveau**.

    -   Entrez Microsoft Building dans le champ **Nom**.
        
-   Cliquez sur **Enregistrer et fermer**. Le nouvel enregistrement s’affiche dans
        la vue Bâtiments actifs.
4.  Créer un enregistrement de visite

    -   Sélectionnez **Visites** dans le plan du site.
    -   Cliquez sur **Nouveau**.
    -   Si nécessaire, remplissez les champs. 
        -   **Nom** : Nouvelle visite test
        -   **Bâtiment** : sélectionnez Microsoft Building
        -   **Visiteur** : sélectionnez John Doe
        -   **Début planifié** : sélectionnez la date du jour et 14h00 comme heure de début.
        -   **Fin planifiée** : sélectionnez la date du jour et 15h30 comme heure de fin.
    -   Cliquez sur **Enregistrer et fermer**. L’enregistrement est ainsi créé. Vous devriez pouvoir le voir dans la
        Vue Visites actives.
    -   Changez la vue en **Visites du jour**. Vous devriez voir la visite entrée dans la vue.
5.  Vous pouvez ajouter d’autres enregistrements test.

# Défis

* Sélectionner des vues et des formulaires spécifiques pour les visites et les bâtiments
* Le personnel de sécurité travaille généralement dans un seul bâtiment. Comment leur fourniriez-vous un moyen simple d’afficher les visites uniquement pour un bâtiment sélectionné ?
* Comment limiteriez-vous l’accès à des entités spécifiques ? Par exemple, les bâtiments devraient être en lecture seule pour tous les membres du personnel à l’exception des administrateurs.
* Quels tableaux de bord envisageriez-vous d’ajouter à l’application ?