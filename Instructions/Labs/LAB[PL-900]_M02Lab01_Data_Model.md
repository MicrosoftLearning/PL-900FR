---
lab:
    title: 'Labo 1 : Modélisation de données'
    module: 'Module 2 : Présentation de Microsoft Dataverse'
---

# Module 2 : Présentation de Microsoft Dataverse
## Labo : Modélisation de données

### Avis important (en vigueur depuis novembre 2020) :
Common Data Service a été renommé en Microsoft Dataverse. Une partie de la terminologie de Microsoft Dataverse a été mise à jour. Par exemple, l’entité (désormais **table**), le champ (désormais **colonne**) et l’enregistrement (désormais **ligne**) sont susceptibles d’être obsolètes. Veuillez garder ce changement à l’esprit lorsque vous effectuez les labos. Nous prévoyons que notre contenu soit très prochainement à jour dans son intégralité.

Pour plus d’informations et pour une liste complète des termes concernés, veuillez consulter [Présentation de Microsoft Dataverse](https://docs.microsoft.com/en-us/powerapps/maker/common-data-service/data-platform-intro#terminology-updates).

# Scénario

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visites sur le campus sont actuellement enregistrées dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données concernant les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel administratif et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Dans ce labo, vous accéderez à votre environnement et créerez une base de données Microsoft Dataverse ainsi qu’une solution pour effectuer le suivi de vos modifications. Vous allez également créer un modèle de données pour prendre en charge les exigences suivantes :

-   R1 - Suivre les emplacements (bâtiments) des visites du campus
-   R2 - Enregistrer des informations de base pour identifier et suivre les visiteurs 
-   R3 - Planifier, enregistrer et gérer les visites 

Enfin, vous importerez des échantillons de données dans Microsoft Dataverse.

# Étapes de labo de haut niveau

Pour préparer vos environnements d’apprentissage, vous devez :

* Créer une solution et un éditeur
* Ajouter les composants, nouveaux et existants, nécessaires pour répondre aux exigences de l’application Vous référer au [document de modèle de données](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/blob/master/Allfiles/Campus%20Management.png) pour la description des métadonnées (tables et relations) Vous pouvez maintenir appuyée la touche CTRL et cliquer ou faire un clic droit sur le lien pour ouvrir le document de modèle de données dans une nouvelle fenêtre.

Votre solution contiendra plusieurs tables une fois toutes les personnalisations effectuées :

-   Contact
-   Bâtiment
-   Visite

## Prérequis :

* Achèvement du **Module 0 - Labo 0 : Valider l’environnement de labo**

## Éléments à considérer avant de commencer :

* Convention d’affectation de noms

* Types de données, restrictions (par exemple, longueur maximale d’un nom)

* Formatage DateHeure pour prendre en charge une localisation facile

# Exercice \#1 : Créer une solution

## Tâche \#1 : Créer une solution et un éditeur

1.  Créer une solution

    -   Accédez à <https://make.powerapps.com>. Vous devrez peut-être vous authentifier à nouveau. Cliquez sur **Se connecter** et suivez les instructions si nécessaire.

    -   Sélectionnez votre environnement en cliquant sur **Environnement** dans le coin supérieur droit de l’écran et choisissez votre environnement dans le menu déroulant.

    -   Sélectionnez **Solutions** dans le menu de gauche, puis cliquez sur **Nouvelle solution**.

    -   Entrez **[Votre nom de famille] Gestion du campus** en tant que **Nom d’affichage**.

2.  Créer un éditeur

    -   Cliquez sur le menu déroulant **Éditeur**, puis sélectionnez **+ Éditeur**.

    -   Dans la fenêtre qui apparaît, saisissez **Bellows College** dans la zone **Nom d’affichage**. 
    
    -   Entrez **bc** dans la zone **Préfixe**.

    -   Cliquez sur **Enregistrer et fermer**.
    
    -   Cliquez sur **Terminé** dans la fenêtre contextuelle.

3.  Terminez la création de la solution.

    -   Maintenant, cliquez sur la liste déroulante **Éditeur**, puis sélectionnez l’éditeur **Bellows College**
        que vous venez de créer.

    -   Validez que cette **Version** est définie sur **1.0.0.0**. 
    
    -   Cliquez sur **Créer**.

# Exercice \#2 : Ajouter ou créer de nouvelles tables

**Objectif :** Au cours de cet exercice, vous apprendrez à ajouter une table Contact standard et à créer de nouvelles tables Bâtiment et Visite personnalisées au sein de la solution. 

## Tâche \#1 : Ajouter une table existante

1.  Cliquez pour ouvrir la solution **Gestion du campus** que vous venez de créer.

2.  Cliquez sur **Ajouter existant**, puis sur **Table**.

3.  Repérez et sélectionnez **Contact**.

4.  Cliquez sur **Suivant**.

5.  Cliquez sur **Sélectionnez les composants** sous Contact.

6.  Sélectionnez l’onglet **Vues**, puis sélectionnez la vue **Contacts actifs**. Cliquez sur
    **Ajouter**.
    
7.  Cliquez à nouveau sur **Sélectionner des composants**.

8.  Cliquez sur l’onglet **Formulaires**, puis sélectionnez le formulaire **Contact**.
    
9.  Cliquez sur **Ajouter**.

    > Vous devez sélectionner les options **1 Vue** et **1 Formulaire**. 
    
10.  Cliquez à nouveau sur **Ajouter**. Cela ajoutera la table Contact, l’affichage et le formulaire sélectionnés à la solution nouvellement créée. 
    
    > Votre solution doit désormais avoir une seule table : Contact.

## Tâche n° 2 : Créer une table Bâtiment

1.  Gardez toujours votre navigateur ouvert sur votre solution Gestion du campus. Dans le cas contraire, ouvrez la solution Gestion du campus en procédant comme suit :

    * Connectez-vous à <https://make.powerapps.com> (si vous n’êtes pas déjà connecté).
    
    * Sélectionnez **Solutions**, puis cliquez pour ouvrir la solution **[Votre nom de famille] Campus Management**
          que vous venez de créer.
          
2.  Créer une table Bâtiment

    -   Cliquez sur **Nouveau** et sélectionnez **Table**.
    
    -   Entrez **Bâtiment** dans le champ **Nom d’affichage**. 
    
    -   Cliquez sur **Créer**. Cette action commence l’approvisionnement de la table en arrière-plan, tandis que vous pouvez commencer à ajouter d’autres tables et d’autres colonnes.

## Tâche n° 3 : Créer des tables et des colonnes Visite

La table **Visite** contient des informations sur les visites du campus, y compris le bâtiment, le visiteur, l’heure prévue et l’heure réelle de chaque visite. 

Nous aimerions attribuer à chaque visite un numéro unique qui peut être facilement saisi et interprété par un visiteur lorsque cela lui est demandé pendant le processus d’enregistrement de la visite.

> Nous utilisons un comportement **indépendant du fuseau horaire** pour enregistrer les informations de date et d’heure. En effet, l’heure d’une visite est toujours locale par rapport à l’emplacement du bâtiment et elle ne doit pas changer lorsqu’elle est vue depuis un autre fuseau horaire. 

1.  Sélectionnez votre solution **Gestion du campus**.

2. Créer une table Visite

   * Cliquez sur **Nouveau** et sélectionnez **Table**.
   
   * Entrez **Visite** dans le champ **Nom d’affichage**. 
   
   * Cliquez sur **Créer**. Cette action commence l’approvisionnement de la table en arrière-plan, tandis que vous pouvez commencer à ajouter d’autres colonnes.

3. Créer une colonne Début prévu

   * Vérifiez que l’onglet **Colonnes** est sélectionné, puis cliquez sur **Ajouter une colonne**.
   
   * Saisissez le **Début prévu** dans la zone **Nom d’affichage**.
   
   * Sélectionnez **Date et heure** dans la liste **Type de données**.
   
   * Dans le champ **Obligatoire**, sélectionnez **Obligatoire**.
   
   * Développez la section **Options avancées**.
   
   * Dans le champ **Comportement**, sélectionnez **Indépendant du fuseau horaire**.
   
   * Cliquez sur **Terminé**.

4.  Créer une colonne Fin prévue

    * Cliquez sur **Ajouter une colonne**.
    
    * Saisissez **Fin prévue** dans le champ **Nom d’affichage**.
    
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    
    * Dans le champ **Obligatoire**, sélectionnez **Obligatoire**.
    
    * Développez la section **Options avancées**.
    
    * Dans le champ **Comportement**, sélectionnez **Indépendant du fuseau horaire**.
    
    * Cliquez sur **Terminé**.
    
5.  Créer une colonne Début réel

    * Cliquez sur **Ajouter une colonne**.
    
    * Saisissez le **Début réel** dans le champ **Nom d’affichage**.
    
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    
    * Dans le champ **Obligatoire**, laissez ceci comme **Optionnel**.
    
    * Développez la section **Options avancées**.
    
    * Dans le champ **Comportement**, sélectionnez **Indépendant du fuseau horaire**.
    
    * Cliquez sur **Terminé**.
    
6.  Créer une colonne Fin réelle

    * Cliquez sur **Ajouter une colonne**.
    
    * Saisissez **Fin réelle** dans la zone **Nom d’affichage**.
    
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    
    * Dans le champ **Obligatoire**, laissez ceci comme **Optionnel**.
    
    * Développez la section **Options avancées**.
    
    * Dans le champ **Comportement**, sélectionnez **Indépendant du fuseau horaire**.
    
    * Cliquez sur **Terminé**.
    
7.  Créer une colonne Code

    * Cliquez sur **Ajouter une colonne**.
    
    * Saisissez **Code** dans la zone **Nom d’affichage**.
    
    * Sélectionnez **Numérotation automatique** dans la liste **Type de données**.
    
    * Sélectionnez **Nombre préfixé de date** pour **Type de numérotation automatique**.
    
    * Cliquez sur **Terminé**.
    
8.  Cliquez sur **Enregistrer la table**.

# Exercice \#3 : Créer des relations

**Objectif :** Au cours de cet exercice, vous apprendrez à ajouter des relations entre les tables.

## Tâche n° 1 : Créer des relations

1.  Assurez-vous que vous affichez toujours la table **Visite** de votre solution **Gestion du campus**. Si ce n’est pas le cas, accédez à cette table.

2.  Créer une relation Visite - Contact

    * Sélectionnez l’onglet **Relations**.
    
    * Cliquez sur **Ajouter une relation**, puis sélectionnez **Plusieurs-à-un**.
    
    * Sélectionnez **Contact** pour **Connexes (Un)**. 
    
    * Saisissez **Visiteur** dans la zone **Nom complet de la colonne de recherche**. 
    
    * Cliquez sur **Terminé**.
    
3.  Créer une relation Visite-Bâtiment

    * Cliquez sur **Ajouter une relation**, puis sélectionnez **Plusieurs-à-un**.
    
    * Sélectionnez **Bâtiment** pour **Connexes (Un)**. 
    
    * Cliquez sur **Terminé**.
    
4.  Cliquez sur **Enregistrer la table**.

5.  Sélectionnez **Solutions** dans le menu supérieur, puis cliquez sur **Publier toutes les personnalisations**.

# Exercice \#4 : Importer des données

**Objectif :** Au cours de cet exercice, vous apprendrez à importer des échantillons de données dans la base de données Dataverse.

## Tâche n° 1 : Importer une solution

Dans cette tâche, vous importerez une solution contenant le flux Power Automate requis pour terminer l’importation des données.

1. Les fichiers **DataImport_managed.zip** doivent être stockés sur votre bureau. Si ce n’est pas le cas, téléchargez la [Solution d’importation de données](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/blob/master/Allfiles/DataImport_managed.zip?raw=true).

2. Connectez-vous à <https://make.powerapps.com>.

3. Sélectionnez votre environnement **Exercices pratiques [mes initiales]** en haut à droite, si ce n’est déjà fait.

4. Sélectionnez **Solutions** dans le panneau de navigation de gauche.

5. Cliquez sur **Importer**, puis cliquez sur **Parcourir**. Parcourez et sélectionnez **DataImport_managed.zip** depuis votre bureau, puis appuyez sur **Suivant**.

>   Vous pouvez recevoir le message suivant :
>
>   Il manque des dépendances. Installez les solutions suivantes avant d’installer celle-ci.
>
>   Ce message indique que, soit le modèle de données n’est pas complet,
>   soit le préfixe de l’éditeur n’est pas **bc**, soit le nom des tables **Bâtiment** et **Visite**
>   diffère des noms répertoriés dans les étapes ci-dessus.

6. Appuyez sur **Suivant**. Vous êtes ensuite invité à rétablir les connexions. 

7. Développez le menu déroulant **Sélectionner une connexion**, puis sélectionnez **+ Nouvelle connexion**.

8. Une nouvelle fenêtre ou un nouvel onglet de navigation s’ouvre. Cliquez sur **Créer** lorsque vous êtes invité à vous connecter. Connectez-vous si nécessaire pour terminer la création de la connexion.

9. Fermez l’onglet ouvert afin de revenir à l’onglet précédent intitulé **Importer une solution**.

10. Assurez-vous que la connexion que vous venez de créer est sélectionnée. Si votre connexion n’apparaît pas, cliquez sur **Actualiser** afin d’actualiser la liste de connexions. 

11. Appuyez sur **Importer**.

12. Attendez que l’importation soit terminée.

## Tâche n° 2 : Importer des données  

1. Ouvrez la solution **Importation de données**.

2. Vérifiez l’**état** du flux **Importation de données**.

3. Si la valeur du champ **Statut** est définie sur **Inactif**, sélectionnez **[...]** en regard du champ **Importer des données**, puis sélectionnez **Activer**.

   > **Important :** Si vous recevez un message d’erreur, vérifiez que les tables et les colonnes que vous avez créées suivent les instructions énoncées ci-dessus.

4. Ouvrez le composant **Importer des données**. Power Automate s’ouvre dans un nouvel onglet. 

5. Cliquez sur **Commencer** s’il est présenté avec une fenêtre contextuelle. 

6. Cliquez sur **Exécuter** puis cliquez **Exécuter le flux** lorsque vous y êtes invité.

7. Cliquez sur **Terminé**.

8. Attendez que l’instance de flux termine son exécution. Vous pouvez actualiser la table de l’**historique des exécutions de 28 jours** pour voir quand le flux s’est exécuté. 

    > Le but de ce flux était de générer des exemples de données pour les labos à venir. Dans la tâche suivante, vous vérifierez que l’importation des données a réussi. 

## Tâche n° 3 : Vérifier une importation de données

1. Revenez à l’onglet Power Apps précédent. Cliquez sur **Terminé** sur la fenêtre contextuelle. 

2. Sélectionnez **Solutions** dans la barre de navigation de gauche et ouvrez votre solution de **Gestion du campus**.

2. Cliquez pour ouvrir la table **Visite**, puis sélectionnez l’onglet **Données**.

3. Cliquez sur **Visites actives** dans le coin supérieur droit pour afficher le sélecteur d’affichage, puis sélectionnez **Toutes les colonnes**. Cela modifiera le mode utilisé pour afficher les données de visite. 

    > Si vous ne voyez pas **Visites actives** en raison d’une résolution plus petite, il se peut qu’une icône en forme d’œil s’affiche au même emplacement.

    > Si l’importation a été correctement effectuée, une liste des lignes de visite s’affiche.

4. Cliquez sur une valeur dans la colonne **Bâtiment** et confirmez que le formulaire de bâtiment s’ouvre dans une fenêtre distincte. 

5. Fermez la fenêtre récemment ouverte.

6. Cliquez sur une valeur dans la colonne **Visiteur** (vous devrez peut-être faire défiler la vue vers la droite) et vérifiez si le formulaire de contact s’ouvre dans une fenêtre distincte.

7. Fermez la fenêtre récemment ouverte.

# Défis

* Envisageriez-vous d’utiliser l’activité de *rendez-vous* dans le cadre de la solution ? Qu’est-ce que cela changerait ?
* Comment faire en sorte que la fin planifiée soit ultérieure au début planifié ? 
* Comment ajouter la prise en charge de plusieurs réunions au cours d’une seule visite ?
* Comment sécuriser l’accès au bâtiment non seulement pour les contacts externes, mais également pour le personnel interne ?
* Comment faire en sorte qu’une visite dans des bâtiments donnés nécessite l’approbation de la direction ? Qu’est-ce que le processus d’approbation changerait dans le modèle de données ?

