---
lab:
    title: 'Labo 3 : Comment créer une application canevas, partie 2'
    module: 'Module 3 : Premiers pas avec Power Apps'
---

# Module 3 : Premiers pas avec Power Apps
## Labo 2 : Comment créer une application canevas, partie 2

### Avis important (en vigueur depuis novembre 2020) :
Common Data Service a été renommé en Microsoft Dataverse. Une partie de la terminologie de Microsoft Dataverse a été mise à jour. Par exemple, l’entité (désormais **table**), le champ (désormais **colonne**) et l’enregistrement (désormais **ligne**) sont susceptibles d’être obsolètes. Veuillez garder ce changement à l’esprit lorsque vous effectuez les labos. Nous prévoyons que notre contenu soit très prochainement à jour dans son intégralité.

Pour plus d’informations et pour une liste complète des termes concernés, veuillez consulter [Présentation de Microsoft Dataverse](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/data-platform-intro#terminology-updates).

# Scénario

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visites sur le campus sont actuellement enregistrées dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données concernant les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel administratif et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Dans la deuxième partie de ce labo, vous allez concevoir et créer une application canevas Power Apps que le personnel de sécurité utilisera aux entrées du bâtiment pour confirmer et enregistrer rapidement les visiteurs.

# Étapes de labo de haut niveau

Vous suivrez le schéma ci-dessous pour concevoir l’application canevas :

-   Créez l’application en utilisant le facteur de formulaire de téléphone.
-   Sélectionnez Dataverse comme source de données.
-   Capturez l’entrée (code visiteur) et localisez la ligne visiteur.
-   Configurez un contrôle de visionneuse de formulaire pour afficher les informations sur le visiteur.
-   Utilisez une vue Dataverse pour remplir la galerie.
-   Gérez le processus d’arrivée et de départ d’un visiteur.

## Prérequis

* Achèvement du **Module 0 - Labo 0 : Valider l’environnement de labo**
* Achèvement du **Module 2 - Labo 1 : Présentation de Microsoft Dataverse**

## Éléments à considérer avant de commencer

-   À quelles informations un agent de sécurité a-t-il besoin d’accéder rapidement ?
-   Que se passe-t-il si le code visiteur n’est pas valide ?
-   Que se passe-t-il si le visiteur arrive en dehors des heures prévues ?

# Exercice \#1 : Créer une application canevas de sécurité

**Objectif :** Au cours de cet exercice, vous allez créer une application canevas.

## Tâche \#1 : Créer une application canevas

1.  Ouvrez votre solution Gestion du campus.

    -   Connectez-vous à <https://make.powerapps.com>.

    -   Si l’environnement affiché en haut à droite n’est pas votre environnement de pratique, sélectionnez-en un dans la liste **Environnement**. 

    -   Sélectionnez **Solutions**.

    -   Cliquez pour ouvrir votre solution de **Gestion du campus**.
    
2.  Créer une nouvelle application canevas

    -   Cliquez sur **Nouveau** et sélectionnez **Application \| Application canevas \| Facteur de formulaire de téléphone**.
        Cela ouvrira l’éditeur d’application dans une nouvelle fenêtre.
        
    -   Cliquez sur **Ignorer** si la boîte de dialogue Bienvenue dans Power Apps Studio apparaît.
    
3.  Enregistrer l’application canevas

    -   Cliquez sur **Fichier** et sélectionnez **Enregistrez sous**.
    
    -   Vérifiez si **le cloud** est sélectionné. 
    
    -   Entrez **[Votre nom de famille] Sécurité du campus** comme Nom et cliquez sur **Enregistrer**.
        
    -   Cliquez sur la flèche **Précédent**, en haut à gauche (sous Power Apps) pour revenir à l’application.

3.  Se connecter à la source de données (visites)

    -   Cliquez sur **Afficher \| Sources de données**
    
    -   Cliquez sur **+ Ajouter des données**.

    -   Cliquez sur **Voir toutes les tables**.
    
    -   Sélectionnez **Visites** et attendez que la table Visite s’affiche sous l’onglet Données.
    
4.  Pour conserver le travail en cours, cliquez sur **Fichier**, puis sur **Enregistrer**. Utilisez la flèche retour pour revenir à l’application.

## Tâche \#2 : Afficher les informations sur les visiteurs

1.  Ajouter une zone de recherche

    -   Sélectionnez l’onglet **Arborescence** sur la barre de navigation de gauche.
    
    -   Sélectionnez **Screen1**.
    
    -   Accédez à l’onglet **Insérer**.
    
    -   Cliquez sur **Texte** et sélectionnez **Saisie de texte**.
    
2.  Modifier l’objet d’entrée de texte

    -   Tout en gardant l’objet d’entrée de texte sélectionné, sélectionnez le texte dans la propriété **Par défaut** et effacez la valeur.
    
    -   Sélectionnez la propriété **Texte d’information** et saisissez la valeur `"Enter visitor code"` (y compris les guillemets).
    
    -   Cliquez sur **[...]** à côté du nom du contrôle dans la vue d’arborescence (TextInput1), sélectionnez **Renommer** et remplacez le nom par `textCode`.
    
3.  Ajouter une vue formulaire

    -   Dans l’onglet **Insertion**, cliquez sur **Formulaires**, puis sélectionnez **Affichage** (il vous faudra peut-être cliquer sur la flèche pointant vers le bas située à droite du ruban, afin de voir l’option Formulaires).
   
    -   Faites glisser le formulaire pour l’aligner avec le bas de l’écran.
   
    -   Tout en sélectionnant le nouveau formulaire, sélectionnez la propriété **Source de données**, puis **Visites**.
   
    -   Dans le volet des propriétés, sélectionnez **Horizontale** dans la zone **Disposition**.

4.  Modifier la vue formulaire

    -   Tout en sélectionnant le nouveau formulaire, cliquez sur **Modifier les champs**.

    -   Supprimez les deux champs **Nom** et **Créé le**.

    -   Cliquez sur **Ajouter un champ** et sélectionnez les champs suivants : **Fin réelle**, **Début réel**, **Bâtiment**, **Fin prévue**, **Début prévu**, **Visiteur**.
   
    -   Appuyez sur **Ajouter**.
   
    -   Modifiez l’ordre des champs sélectionnés en faisant glisser les cartes de champ dans la liste. L’ordre recommandé est le suivant : Visiteur, Bâtiment, Début prévu, Fin prévue, Début réel, Fin réelle (vous pouvez réduire les champs afin de les faire glisser plus facilement).
   
    -   Cliquez sur le **X** pour fermer le volet Champs.
   
5.  Tout en conservant la vue formulaire sélectionnée, sélectionnez l’onglet Avancé dans le volet Propriétés. Sélectionnez Propriété de l’**article** et entrez `LookUp(Visits, Code = textCode.Text)`. 

6.  Pour conserver le travail en cours, cliquez sur **Fichier**, puis sur **Enregistrer**. Utilisez la flèche retour pour revenir à l’application.

7.  Préparez-vous à tester l’application.

    -   Passez à l’onglet du navigateur contenant la solution.

    -   Cliquez sur **Terminé** dans la fenêtre contextuelle.
   
    -   Sélectionnez la table **Visite**.
   
    -   Sélectionnez l’onglet **Données**.
   
    -   Ouvrez le sélecteur de vue en haut à droite en cliquant sur le nom de la vue actuelle, **Visites actives**.
   
    -   Sélectionnez la vue **Toutes les colonnes**.
   
    -   Recherchez une ligne Visite ne possédant pas la valeur Début réel ou Fin réelle. En d’autres termes, ces deux colonnes doivent être vides. Sélectionnez et copiez le **Code** pour cette visite.

8.  Tester l’application

    -   Basculez vers l’onglet du navigateur dans l’application, appuyez sur **F5** ou cliquez sur l’icône **Lire** dans le coin supérieur droit pour afficher un aperçu de l’application.
   
    -   Collez la valeur copiée dans la zone de texte de recherche et vérifiez que l’enregistrement est affiché dans le formulaire
   
9.  Effacez le contenu de la zone de texte de recherche.
   
10.  Appuyez sur **ÉCHAP** pour quitter l’application en cours d’exécution.

## Tâche \#3 : Ajouter des boutons d’entrée et de sortie

Dans cette tâche, nous créerons des boutons permettant à l’utilisateur d’enregistrer l’heure d’arrivée et de départ de sa visite. 

1. Enregistrez les résultats de la recherche dans une variable à réutiliser dans la commande.

    * Sélectionnez la commande **textCode**.
   
    * Dans le volet des propriétés, sélectionnez l’onglet **Avancé** et sélectionnez la propriété **OnChange**.
   
    * Entrez l’expression suivante : `Set(Visit, LookUp(Visits, Code = textCode.Text))`.
    
    > Cela enregistrera la visite dans une variable globale lorsqu’un utilisateur effectuera une recherche dans la zone de recherche textCode. Cela nous permet d’utiliser la variable *Visite* dans toute l’application, sans avoir à ressaisir l’expression de recherche entière.

2. Ajoutez le bouton « Check In ».

   * Sélectionnez l’onglet **Insertion**.
   
   * Cliquez sur **Bouton**.
   
   * Dans le volet des propriétés, remplacez la valeur du bouton propriété **Texte** par "`Check In`" (vous pouvez taper la valeur entre les guillemets existants).
   
   * Cliquez sur **[...]** en regard du nom du bouton dans la vue d’arborescence (Button1), sélectionnez **Renommer** et remplacez le nom par `CheckInButton`.

3. Ajouter le bouton Check Out   

   * Cliquez sur **Bouton** dans l’onglet Insertion pour insérer un autre bouton.
   
   * Dans le volet des propriétés, remplacez la valeur de la propriété du bouton **Texte** par "`Check Out`" (vous pouvez la taper entre les guillemets existants).
   
   * Renommez le bouton `CheckOutButton`.
   
   * Positionnez les boutons sous le champ de recherche, en laissant **Check In** au-dessus de **Check Out**. 
   
## Tâche \#4 : Activer et désactiver les boutons en fonction des données de visite

Dès lors que les utilisateurs ont recherché la visite, nous souhaitons qu’ils puissent utiliser le bouton Entrée pour effectuer le processus d’entrée. Nous aimerions activer le bouton **Entrée** si l’enregistrement de la visite est localisé (non vide), si l’état de l’enregistrement est actif et si la visite n’a pas encore commencé, c’est-à-dire si la valeur du champ Début réel n’est pas renseignée.

1. Sélectionnez le **bouton Entrée** et cliquez sur la propriété **Mode d’affichage** du bouton dans l’onglet Propriétés.

2. Saisissez l’expression ci-dessous dans la barre de fonctions :

      ```
      If(!IsBlank(Visit) 
      && Visit.Status = 'Status (Visits)'.Active
      && IsBlank(Visit.'Actual Start'),
          DisplayMode.Edit,
          DisplayMode.Disabled
      )
      ```

   L’expression peut être décomposée comme suit :

   * **!IsBlank(Visit)** -  : un enregistrement de visite a été trouvé.
   * **&&** -  : opérateur logique ET
   * **Visit.Status = 'Status (Visits)'.Active** : le statut de l’enregistrement est *Actif*.
   * **IsBlank(Visit.'Actual Start')** : le champ Début effectif ne contient aucune donnée.
   * **DisplayMode.Edit, DisplayMode.Disabled** -  : si les conditions ci-dessus sont remplies, le bouton deviendra modifiable. Sinon, le bouton restera désactivé.

Nous aimerions activer le bouton **Sortie** lorsque l’enregistrement de visite a été localisé (n’est pas vide), l’état de l’enregistrement est actif et la visite a déjà commencé, c’est-à-dire que la valeur de début effectif n’est pas vide.

3. Sélectionnez le bouton Sortie et cliquez sur la propriété **Mode d’affichage** du bouton sous l’onglet Propriétés.

4. Saisissez l’expression ci-dessous dans la barre de fonctions :

     ```
     If(!IsBlank(Visit) 
     && Visit.Status = 'Status (Visits)'.Active
     && !IsBlank(Visit.'Actual Start'),
         DisplayMode.Edit,
         DisplayMode.Disabled
     )
     ```

5. Pour conserver le travail en cours, cliquez sur **Fichier**, puis sur **Enregistrer**. Utilisez la flèche retour pour revenir à l’application.

6. Appuyez sur **F5** pour exécuter l’application. 

7. Les deux boutons doivent être désactivés. Saisissez la valeur de code que vous avez copiée précédemment et appuyez sur la touche **Tab** pour éloigner le focus de la zone de texte (ou cliquez en dehors de la zone de texte). Le bouton **Entrée** doit ensuite s’activer. 

8. Effacez le contenu de la zone de recherche.

9. Appuyez sur **ÉCHAP** pour quitter l’application en cours d’exécution.

## Tâche \#5 : Finaliser le processus d’entrée et de sortie

Pour implémenter le processus d’entrée et de sortie, nous devons mettre à jour les données de visite de Dataverse comme suit :

* Lorsque le visiteur entre, saisissez la date et l’heure actuelles dans le champ *Début réel*.
* Lorsque le visiteur sort, définissez la valeur du champ *Fin réelle* sur la date et à l’heure actuelles. 
* Après la sortie, définissez l’état de l’enregistrement sur Inactif, indiquant que la visite est terminée.

1. Cliquez sur le bouton **Entrée**.

2. Définissez la propriété **OnSelect** de l’onglet Avancé sur l’expression suivante.

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

   * **Patch(Visits, Visit, {'Actual Start': Now()});**. La méthode *Patch* met à jour la table **Visites** et la ligne identifiée par la variable **Visite** (qui correspond à la visite actuelle). L’expression définit la valeur de la colonne *Début réel* aux date et heure actuelles (méthode *Now()*).
   * **Refresh([@Visits]);**. Cette expression actualise les lignes de visite à mesure que les valeurs sous-jacentes changent.
   * **Set(Visit, LookUp(Visits, Code = textCode.Text));** Cette expression met à jour la variable *Visite* avec les nouvelles données de Dataverse.
   
   > Lorsqu’un utilisateur clique sur ce bouton, le début réel de la visite est défini sur la date et l’heure actuelles et les données sont actualisées.

3. Sélectionnez le bouton **Sortie**.

4. Définissez la propriété **OnSelect** de l’onglet Avancé sur l’expression suivante :

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

   Lorsqu’un utilisateur clique sur ce bouton, la fin réelle est définie sur la date et l’heure actuelles, l’état de l’enregistrement de visite est défini sur Inactif et les données sont actualisées.

5. Pour conserver le travail en cours, cliquez sur **Fichier**, puis sur **Enregistrer**. Utilisez la flèche **Retour** pour revenir à l’application.

6. Appuyez sur **F5** ou cliquez sur le bouton Lecture pour exécuter l’application. Entrez la valeur de code que vous avez copiée précédemment et appuyez sur **Onglet** pour éloigner le focus de la zone de texte. Le bouton **Entrée** doit ensuite s’activer.

7. Appuyez sur le bouton **Entrée**. Il devrait alors se produire ceci :

   * **Début réel** est défini sur la date et l’heure actuelles.
   
   * Le bouton **Entrée** est désactivé.
   
   * Le bouton **Sortie** est activé.

8. Appuyez sur le bouton **Sortie**.

   * **Fin réelle** est défini sur la date et l’heure actuelles.
   
   * Les deux boutons sont désactivés.

9. Effacez le contenu de la zone de recherche.

10. Appuyez sur **ÉCHAP** pour quitter l’application en cours d’exécution.

## Tâche \#6 : Ajouter des indicateurs visuels

La convivialité d’une application mobile s’améliore considérablement lorsque des indicateurs visuels sont fournis. Dans cette tâche, nous ajouterons une icône indiquant si un visiteur peut entrer ou sortir.

1. Sélectionnez l’onglet **Insertion**.

2. Sélectionnez **Icônes \| Ajouter**. Sélectionnez une icône. À ce stade, peu importe l’icône que nous sélectionnons, car nous voulons que la valeur soit dynamique.

3. Redimensionnez et déplacez l’icône à gauche des boutons.

4. Sous l’onglet Avancé de l’icône, sélectionnez propriété de l’**Icône** (dans la section Conception) et entrez l’expression suivante :

   ```
   If(
      CheckInButton.DisplayMode = DisplayMode.Disabled 
   && CheckOutButton.DisplayMode = DisplayMode.Disabled,
       Icon.EmojiFrown,
       Icon.EmojiSmile
   )
   ```

5. Pour conserver le travail en cours, cliquez sur **Fichier**, puis sur **Enregistrer**. Utilisez la flèche **Retour** pour revenir à l’application.

6. Appuyez sur **F5** pour exécuter l’application. Entrez la valeur de code que vous avez copiée précédemment et appuyez sur **Onglet** pour éloigner le focus de la zone de texte. Vérifiez que l’icône affiche un emoji aux sourcils froncés.

7. Recherchez une valeur de code différente qui n’a pas été utilisée auparavant (elle ne doit pas avoir de valeur de début réel ou de fin réelle). 

    > Vous pouvez accéder à l’onglet précédent pour copier un autre code à partir de l’une des visites que vous avez créées. Vous pouvez également exécuter votre application **Personnel du campus**, créée précédemment, pour créer de nouveaux enregistrements de visites. Vérifiez que l’icône affiche un emoji souriant pour ce code.

Votre application en cours d’exécution doit ressembler à ceci :

![Application de sécurité exécutant un canevas](media/3-canvas-app-running.png)

8. Appuyez sur **ÉCHAP** pour quitter l’application en cours d’exécution.

## Tâche 7 : Publier l’application

1. Vous devriez toujours garder l’application Sécurité du campus ouverte dans votre navigateur. Sinon, sélectionnez l’application **Sécurité du campus**, puis cliquez sur **Modifier**.

2. Sélectionnez **Fichier \| Publier** 

3. Sélectionnez **Publier cette version**.

# Défis

* Évitez une saisie manuelle du code de visite.
* Ajoutez la validation du bâtiment de la visite.
* Ajoutez la validation de l’heure réelle de la visite par rapport à l’heure prévue de la visite (trop tôt, trop tard, etc.).
* Ajoutez l’état détaillé de la visite, par exemple l’affichage et la validation des e-mails du visiteur, la raison du refus d’accès au bâtiment, etc.
* Plusieurs bâtiments / réunions / vérifications lors d’une seule visite du campus. Par exemple, une personne peut visiter le campus pendant une journée et au cours de cette journée, elle rencontrera des membres du personnel dans plusieurs bâtiments, à différents moments de la journée. Envisageriez-vous d’apporter une entité *rendez-vous* dans la solution ?
