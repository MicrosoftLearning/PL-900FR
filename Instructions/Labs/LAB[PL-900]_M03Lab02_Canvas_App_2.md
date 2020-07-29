---
lab:
    title: 'Labo : Application de canevas, Deuxième partie'
    module: 'Module 3 : Premiers pas avec Power Apps'
---

# Module 3 : Premiers pas avec Power Apps
## Labo : Application de canevas, Deuxième partie

Scénario
========

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visites sur le campus sont actuellement enregistrées dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données concernant les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel administratif et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Dans la deuxième partie de ce labo, vous allez concevoir et créer une application de canevas Power Apps que le personnel de sécurité utilisera aux entrées du bâtiment pour confirmer et enregistrer rapidement les visiteurs.

Étapes de labo de haut niveau
======================

Vous suivrez le schéma ci-dessous pour concevoir l’application canevas :

-   Créez l’application en utilisant le facteur de formulaire de téléphone
-   Se connecter à Common Data Service en tant que source de données
-   Capturez l’entrée (code visiteur) et localisez l’enregistrement visiteur
-   Configurez un contrôle de visualiseur de formulaire pour afficher les informations sur le visiteur
-   Utilisez une vue CDS pour remplir la galerie
-   Gérez le processus d’arrivée et de départ d’un visiteur


## Conditions préalables

* Achèvement du labo 1 - Modélisation de données

Éléments à considérer avant de commencer
-----------------------------------

-   À quelles informations un agent de sécurité a-t-il besoin d’accéder rapidement ?
-   Que doit-il se passer si le code visiteur n’est pas valide ?
-   Que se passera-t-il si le visiteur arrive en dehors des heures prévues ? 

Exercice \#1 : Créer une application de canevas de sécurité
===============================

**Objectif :** Dans cet exercice, vous allez créer une application de canevas.

Tâche \#1 : Créer une application de canevas
---------------------------

1.  Ouvrez la solution Gestion du campus.

    -   Connectez-vous à <https://make.powerapps.com>

    -   Si l’environnement affiché en haut à droite n’est pas votre environnement de Bellows College, sélectionnez votre **Environnement**. 

    -   Sélectionnez **Solutions**.

    -   Cliquez pour ouvrir la solution de **Gestion du campus**.
2.  Créer une nouvelle application canevas

    -   Cliquez sur **Nouveau** et sélectionnez **Application \| Application canevas \| Facteur de formulaire de téléphone**.
        Cela ouvrira l’éditeur d’application dans une nouvelle fenêtre.
    -   Si c’est votre première application, il vous demandera de définir
        Le pays ou la région de l’application. Cliquez sur **Démarrer.**
    -   Cliquez sur Fichier et sélectionnez Enregistrer sous.
    -   Vérifiez si **le cloud** est sélectionné. Entrez **Sécurité du campus** dans le champ Nom et
        cliquez sur **Enregistrer**. Cela garantit que les modifications ne seront pas supprimées si l’application se ferme subitement.
    -   Cliquez sur la flèche de retour en haut à droite (sous « Power Apps ») pour revenir à l’application.

3.  Se connecter à la source de données (visites)
    1.  Cliquez sur **Afficher \| Des sources de données**
    2.  Cliquez sur **Ajouter des données**
    3.  Cliquez sur **Voir toutes les entités**
    4.  Sélectionnez **Visites** et attendez que l’entité Visite s’affiche sous le champ Sources de données.
4.  Pour conserver le travail en cours, cliquez sur **Fichier \| Enregistrez** puis appuyez sur **Enregistrer**

Tâche \#2 : Affichez les informations sur les visiteurs
--------------------------------

1.  Ajoutez une zone de recherche

    -   Sélectionnez l’onglet **Arborescence** dans le volet gauche.
    -   Sélectionnez **Screen1**.
    -   Accédez à l’onglet **Insérer**.
    -   Cliquez sur **Texte** et sélectionnez **Saisie de texte**.
    -   Sélectionnez le texte dans la propriété **Default** et effacez la valeur.
    -   Sélectionnez la propriété **HintText** et entrez la valeur **"Entrez le code visiteur"** (avec les guillemets)
    -   Cliquez sur ... à côté du nom du contrôle dans une arborescence, sélectionnez **Renommer**, changez le nom par **textCode**
2. Ajouter un mode formulaire

   -   Sur l’onglet **Insérer**, cliquez sur **Formulaires** puis sélectionnez **Afficher**
   -   À l’aide des poignées de taille, placez le formulaire sous la zone de texte de recherche
   -   Sélectionnez la propriété **DataSource** et entrez **Visites**
   -   Dans le volet des propriétés, sélectionnez **Horizontale** comme **Disposition**
   -   Cliquez sur **Modifier les champs**
   -   Cliquez sur **Ajouter un champ** et sélectionnez les champs suivants : Fin effective, Début effectif, Bâtiment, Fin planifiée, Début planifié, Visiteur
   -   Appuyez sur **Ajouter**.
   -   Modifiez l’ordre des champs sélectionnés en faisant glisser les cartes de champ dans la liste. L’ordre recommandé est Visiteur, Bâtiment, Début planifié, Fin planifiée, Début réel, Fin réelle
   -   Sous l’onglet Avancé, sélectionnez Propriété de l’**article** et entrez `LookUp(Visits, Code = textCode.Text)`

3.  Pour conserver le travail en cours, cliquez sur **Fichier \| Enregistrez** puis appuyez sur **Enregistrer**. Cliquez sur la flèche de retour en haut à droite (sous « Power Apps ») pour revenir à l’application.

4. Testez l’application

   -   Passez à l’onglet du navigateur contenant la solution
   -   Sélectionnez l’entité **Visite**
   -   Sélectionnez l’onglet **Données**
   -   Ouvrez le sélecteur de vue en haut à droite en cliquant sur le nom de la vue actuelle (visites actives)
   -   Remplacez le nom de la vue par **Tous les champs**
   -   Recherchez un enregistrement de visite qui n’a pas de valeur de début réel ou de fin réelle. Sélectionnez et copiez le **code** de cette visite.
   -   Basculez vers l’onglet du navigateur avec l’application, puis appuyez sur F5 pour exécuter l’application
   -   Collez la valeur copiée dans la zone de texte de recherche et vérifiez que l’enregistrement est affiché dans le formulaire
   -   Effacez le contenu de la zone de texte de recherche.
5.  Appuyez sur **ÉCHAP** pour quitter l’application en cours d’exécution.


Tâche 3 : Ajouter des boutons d’entrée et de sortie
---------------------------------------

1. Enregistrez les résultats de la recherche dans une variable à réutiliser dans la commande

   * Sélectionnez la commande **textCode**
   * Sélectionnez la propriété **OnChange** sous l’onglet Avancé
   * Entrez l’expression suivante : `Set(Visit, LookUp(Visits, Code = textCode.Text))`
     C’est la même expression que ci-dessus, sauf que cette fois, nous enregistrons les résultats dans une variable globale. Cela nous permet d’utiliser la variable *Visite* dans toute l’application, sans avoir à ressaisir l’expression de recherche entière.

2. Ajouter des boutons pour l’entrée et la sortie
   
1. Sélectionnez l’onglet **Insertion**
   2. Cliquez sur **Bouton**
   3. Remplacez la valeur de la propriété **Texte** du bouton par **« Entrée »** (vous pouvez taper entre les guillemets existants)
   4. Renommez le bouton **CheckInButton** en cliquant sur le nom du bouton (Bouton1) dans le volet de droite
   5. Cliquez sur **Bouton** pour insérer un autre bouton
   6. Changer la propriété **Texte** du bouton par **« Sortie »**
   7. Renommez le bouton en **BoutonSortie**
   8. Positionnez les boutons côte à côte sous le mode formulaire d’enregistrement 
   
3. Activez et désactivez les boutons en fonction des données de visite. 
   Nous aimerions activer le bouton **Archiver** si l’enregistrement de visite est localisé (non vide), si l’état de l’enregistrement est actif et si la visite n’a pas encore commencé, c’est-à-dire si la valeur du champ Début réel n’est pas renseignée.

   * Sélectionnez le bouton Entrée et cliquez sur la propriété **DisplayMode** du bouton de l’onglet Propriétés

   * Tapez l’expression ci-dessous dans la barre de fonction.

      ```
      If(!IsBlank(Visit) 
      && Visit.Status = 'Status (Visits)'.Active
      && IsBlank(Visit.'Actual Start'),
          DisplayMode.Edit,
          DisplayMode.Disabled
      )
      ```

   L’expression peut être décomposée comme suit :

   * `!IsBlank(Visit)` : un enregistrement de visite a été trouvé
   * `&&` : opérateur ET logique
   * `Visit.Status = 'Status (Visits)'.Active` : l’état de l’enregistrement est *Actif*
   * `IsBlank(Visit.'Actual Start')` : le champ Début effectif ne contient aucune donnée

4. Nous aimerions activer le bouton **Sortie** lorsque l’enregistrement de visite a été localisé (n’est pas vide), l’état de l’enregistrement est actif et la visite a déjà commencé, c’est-à-dire que la valeur de début effectif n’est pas vide.

   * Sélectionnez le bouton Sortie et cliquez sur la propriété **DisplayMode** du bouton situé sous l’onglet Propriétés

   * Tapez l’expression ci-dessous dans la barre de fonction.

     ```
     If(!IsBlank(Visit) 
     && Visit.Status = 'Status (Visits)'.Active
     && !IsBlank(Visit.'Actual Start'),
         DisplayMode.Edit,
         DisplayMode.Disabled
     )
     ```

5. Pour conserver le travail en cours, cliquez sur **Fichier \| Enregistrez** puis appuyez sur **Enregistrer**. Cliquez sur la flèche de retour en haut à droite (sous « Power Apps ») pour revenir à l’application.

6. Appuyez sur **F5** pour exécuter l’application. Les deux boutons doivent être désactivés. Entrez la valeur de code que vous avez copiée précédemment et appuyez sur **Onglet** pour éloigner le focus de la zone de texte. Le bouton **Entrée** doit ensuite s’activer.

7. Appuyez sur **ÉCHAP** pour quitter l’application en cours d’exécution.

## Tâche 4 : Finaliser le processus d’entrée et de sortie

Pour implémenter le processus d’entrée et de sortie, nous devons mettre à jour les données de visite du Common Data Service en procédant comme suit :

* Lorsque le visiteur entre, définissez le champ *Début réel* à la date et à l’heure actuelles
* Lorsque le visiteur sort, définissez la valeur du champ *Fin réelle* sur la date et à l’heure actuelles. 
* Après la sortie, remplacez l’état de l’enregistrement par Inactif, indiquant que la visite est terminée

1. Cliquez sur le bouton **Entrée**.

2. Définissez la propriété **OnSelect** sur l’expression suivante.

   ```
   Patch(
       Visits,
       Visit,
       {'Actual Start': Now()}
   );
   Refresh([@Visits]);
   Set(Visit, LookUp(Visits, Code = textCode.Text));
   ```

   Cette expression se décompose comme suit :

   * `Patch(Visits, Visit, {'Actual Start': Now()});`. La méthode *Patch* met à jour l’entité **Visites**, l’enregistrement identifié par la variable **Visite** (qui correspond à la visite actuelle). L’expression définit la valeur du champ *Début réel* sur la date du jour et l’heure actuelle (méthode **Now()).
   * `Refresh([@Visits]);`. Cette expression actualise les enregistrements de visite à mesure que les valeurs sous-jacentes changent
   * `Set(Visit, LookUp(Visits, Code = textCode.Text));` Cette expression met à jour la variable *Visite* avec de nouvelles données du CDS.

3. Sélectionnez le bouton **Sortie**.

4. Définissez la propriété **OnSelect** sur l’expression suivante.

   ```
   Patch(
       [@Visits],
       Visit,
       {
           'Actual End': Now(),
           Status: 'Status (Visits)'.Inactive
       }
   );
   Refresh([@Visits]);
   Set(Visit, LookUp(Visits, Code = textCode.Text));
   ```

   La seule différence par rapport à l’expression d’entrée est le champ *État* à valeur *Inactif*.

5. Pour conserver le travail en cours, cliquez sur **Fichier \| Enregistrez** puis appuyez sur **Enregistrer**.

6. Appuyez sur **F5** pour exécuter l’application. Entrez la valeur de code que vous avez copiée précédemment et appuyez sur **Onglet** pour éloigner le focus de la zone de texte. Le bouton **Entrée** doit ensuite s’activer.

7. Appuyez sur le bouton **Entrée**. Il devrait alors se produire ceci :

   1. *Début effectif* a une date et une heure actuelles
   2. Le bouton **Entrée** est désactivé
   3. Le bouton **Sortie** est activé

8. Appuyez sur le bouton **Sortie**.

   1. *Fin réelle* est défini sur la date du jour et l’heure actuelle
   2. Les deux boutons sont désactivés

9. Appuyez sur **ÉCHAP** pour quitter l’application en cours d’exécution.

Tâche 5 : Ajouter des indicateurs visuels
--------------------------------------

La convivialité d’une application mobile s’améliore considérablement lorsque, en plus des informations textuelles, des indicateurs visuels sont fournis. Dans cette tâche, nous ajouterons une icône indiquant si un visiteur peut entrer ou sortir.

1. Sélectionnez l’onglet **Insertion**

2. Sélectionnez **Icônes \| Ajouter**. À ce stade, peu importe l’icône que nous sélectionnons car nous voulons que la valeur soit dynamique.

3. Redimensionnez et placez l’icône au milieu de l’écran, sous les boutons

4. Sous l’onglet Avancé de Icon, sélectionnez  **Propriété Icon** (dans la section Design) et entrez l’expression suivante

   ```
   If(
      CheckInButton.DisplayMode = DisplayMode.Disabled 
   && CheckOutButton.DisplayMode = DisplayMode.Disabled,
       Icon.EmojiFrown,
       Icon.EmojiSmile
   )
   ```

5. Pour conserver le travail en cours, cliquez sur **Fichier \| Enregistrez** puis appuyez sur **Enregistrer**.
6. Appuyez sur **F5** pour exécuter l’application. Entrez la valeur de code que vous avez copiée précédemment et appuyez sur **Onglet** pour éloigner le focus de la zone de texte. Vérifiez que l’icône affiche un emoji aux sourcils froncés.
7. Recherchez une valeur de code différente qui n’a pas été utilisée auparavant (sans valeur de début réel ni de fin réelle). Vous pouvez exécuter l’application **Personnel du campus**, créée précédemment, pour créer de nouveaux enregistrements de visites. Vérifiez que l’icône affiche un emoji souriant.
8. Appuyez sur **ÉCHAP** pour quitter l’application en cours d’exécution.

## Tâche 6 : Publier l’application

1. Il est conseillé de garder l’application de sécurité du campus constamment ouverte dans votre navigateur. Si non, sélectionnez l’application **Sécurité du campus**, puis cliquez sur **Modifier**
2. Sélectionnez **Fichier \| Publier** 
3. Cliquez sur **Publier cette version**

# Défis

* Comment éviter une saisie manuelle du code de visite ?
* Ajoutez la validation du bâtiment de la visite
* Ajoutez la validation de l’heure réelle de la visite par rapport à l’heure prévue de la visite (trop tôt, trop tard, etc.)
* Ajoutez l’état détaillé de la visite, par exemple l’affichage et la validation des e-mails du visiteur, la raison du refus d’accès au bâtiment, etc.
* Comment géreriez-vous l’exigence de plusieurs bâtiments / réunions / entrées pendant une seule visite du campus ? Par exemple, une personne peut visiter le campus pendant une journée et au cours de cette journée, elle rencontrera des membres du personnel dans plusieurs bâtiments, à différents moments de la journée. Envisageriez-vous d’intégrer l’entité de *rendez-vous* dans la solution ?
