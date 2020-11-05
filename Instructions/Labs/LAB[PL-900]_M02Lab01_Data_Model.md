---
lab:
    title: 'Labo 1 : Modélisation de données'
    module: 'Module 2 : Introduction à Common Data Service'
---

# Module 2 : Introduction à Common Data Service
## Labo : Modélisation de données


# Scénario

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visites sur le campus sont actuellement enregistrées dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données concernant les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel administratif et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Dans ce labo, vous allez accéder à votre environnement, créer une base de données CDS (Common Data Service) et créer une solution pour effectuer le suivi de vos modifications. Vous allez également créer un modèle de données pour prendre en charge les exigences suivantes :

-   R1 - Suivre les emplacements (bâtiments) des visites du campus
-   R2 - Enregistrer des informations de base pour identifier et suivre les visiteurs 
-   R3 - Planifier, enregistrer et gérer les visites 

Enfin, vous allez importer des échantillons de données dans Common Data Service.

# Étapes de labo de haut niveau

Pour préparer vos environnements d’apprentissage, vous devez :

* créer une solution et un éditeur
* ajouter les composants, nouveaux et existants, nécessaires pour répondre aux exigences de l’application. Se référer au [document de modèle de données](../../Allfiles/Campus%20Management.png) pour la description des métadonnées (entités et relations). Vous pouvez maintenir appuyée la touche CTRL et cliquer ou faire un clic droit sur le lien pour ouvrir le document de modèle de données dans une nouvelle fenêtre.

Votre solution contiendra plusieurs entités une fois toutes les personnalisations terminées :

-   Contact
-   Bâtiment
-   Visite

## Conditions préalables :

* Achèvement du **labo 0 du module 0 : Valider l’environnement de laboratoire**

## Éléments à considérer avant de commencer :

* Convention d’affectation de noms

* Types de données, restrictions (par exemple, longueur maximale d’un nom)

* Formatage DateHeure pour prendre en charge une localisation facile

# Exercice \#1 : Créer une solution

## Tâche \n°1 : Créer une solution et un éditeur

1.  Créer une solution

    -   Allez à <https://make.powerapps.com>. Vous devrez peut-être vous authentifier à nouveau. Cliquez sur **Se connecter** et suivez les instructions si nécessaire.

    -   Sélectionnez votre environnement en cliquant sur **Environnement** dans le coin supérieur droit de l’écran et choisissez votre environnement dans le menu déroulant.

    -   Sélectionnez **Solutions** dans le menu de gauche, puis cliquez sur **Nouvelle solution**.

    -   Entrez **« [Votre nom] Gestion du campus »** en tant que **Nom d’affichage**.

2.  Créer un éditeur

    -   Cliquez sur le menu déroulant **Éditeur**, puis sélectionnez **Éditeur**.

    -   Dans la fenêtre qui apparaît, entrez **Bellows College** dans la zone **Nom d’affichage** et **bc** dans la zone **Préfixe**

    -   Cliquez sur **Enregistrer et fermer**. 
    
    -   Cliquez sur **Terminé** dans la fenêtre contextuelle.

3.  Terminez la création de la solution.

    -   Maintenant, cliquez sur la liste déroulante **Éditeur**, puis sélectionnez l’éditeur **Bellows College**
        que vous venez de créer.

    -   Validez que cette **Version** est définie sur **1.0.0.0** 
    
    -   Cliquez sur **Créer.**

## Tâche \n°2 : Ajouter une entité existante

1.  Cliquez pour ouvrir la solution **Gestion du campus** que vous venez de créer.

2.  Cliquez sur **Ajouter existant**, puis sélectionnez **Entité**.

3.  Localisez **Contact** et sélectionnez-le.

4.  Cliquez sur **Suivant**.

5.  Cliquez sur **Sélectionnez les composants** sous Contact.

6.  Sélectionnez l’onglet **Vues**, puis sélectionnez la vue **Contacts actifs**. Cliquez sur
    **Ajouter**.
    
7.  Cliquez à nouveau sur **Sélectionner des composants**.

8.  Cliquez sur l’onglet **Formulaires**, puis sélectionnez le formulaire **Contact**.
    
9.  Cliquez sur **Ajouter**.

    > Vous devez sélectionner les options **1 Vue** et **1 Formulaire**. 
    
10.  Cliquez à nouveau sur **Ajouter**. Cela ajoutera l’entité Contact avec la vue et le formulaire sélectionnés à la solution nouvellement créée. 
    
11.  Votre solution doit maintenant avoir une seule entité : Contact.

# Exercice \#2 : Créer des entités et des relations

**Objectif :** Dans cet exercice, vous allez créer des entités, puis ajouter des relations
entre les entités.

## Tâche #1 : Créer une entité et des champs de bâtiment

1.  Gardez toujours votre navigateur ouvert sur votre solution Gestion du campus. Dans le cas contraire, ouvrez la solution Gestion du campus en procédant comme suit :

    * Connectez-vous à <https://make.powerapps.com> (si vous n’êtes pas déjà connecté)
    
    * Sélectionnez **Solutions**, puis cliquez pour ouvrir la solution **[Votre Nom De Famille] Campus Management**
          que vous venez de créer.
          
2.  Créer une entité de bâtiment

    -   Cliquez sur **Nouveau**, puis sélectionnez **Entité**.
    
    -   Entrez **Bâtiment** dans le champ **Nom d’affichage**. 
    
    -   Cliquez sur **Terminé**. Cette action débute l’approvisionnement de l’entité en arrière-plan, tandis que vous pouvez commencer à ajouter d’autres entités et d’autres champs.

## Tâche n° 2 : Créer une entité et des champs de visite

L’entité **Visite** contient des informations sur les visites du campus, y compris le bâtiment, le visiteur, l’heure prévue et l’heure réelle de chaque visite. 

Nous aimerions attribuer à chaque visite un numéro unique qui peut être facilement saisi et interprété par un visiteur lorsque cela lui est demandé pendant le processus d’enregistrement de la visite.

> Nous utilisons un comportement **indépendant du fuseau horaire** pour enregistrer les informations de date et d’heure. En effet, l’heure d’une visite est toujours locale par rapport à l’emplacement du bâtiment et elle ne doit pas changer lorsqu’elle est vue depuis un autre fuseau horaire. 

1.  Sélectionnez votre solution **Gestion du campus**.

2. Créer une entité de visite

   * Cliquez sur **Nouveau**, puis sélectionnez **Entité**.
   
   * Entrez **Visite** dans le champ **Nom d’affichage**. 
   
   * Cliquez sur **Terminé**. Cette action débute l’approvisionnement de l’entité en arrière-plan, tandis que vous pouvez commencer à ajouter d’autres champs.

3. Créer un champ Début planifié

   * Vérifiez que l’onglet **Champs** est sélectionné, puis cliquez sur **Ajouter un champ**.
   
   * Entrez **Début planifié** pour **Afficher un nom**.
   
   * Sélectionnez **Date et heure** dans la liste **Type de données**.
   
   * Dans le champ **Obligatoire**, sélectionnez **Obligatoire**.
   
   * Développez la section **Options avancées**.
   
   * Dans le champ **Comportement**, sélectionnez **Indépendant du fuseau horaire**.
   
   * Cliquez sur **Terminé**.

4.  Créer un champ Fin planifiée

    * Cliquez sur **Ajouter un champ**.
    
    * Entrez **Fin planifiée** dans le champ **Nom d’affichage**.
    
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    
    * Dans le champ **Obligatoire**, sélectionnez **Obligatoire**.
    
    * Développez la section **Options avancées**.
    
    * Dans le champ **Comportement**, sélectionnez **Indépendant du fuseau horaire**.
    
    * Cliquez sur **Terminé**.
    
5.  Créer un champ Début réel

    * Cliquez sur **Ajouter un champ**.
    
    * Entrez **Début réel** pour **Afficher un nom**.
    
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    
    * Dans le champ **Obligatoire**, laissez ceci comme **Optionnel**.
    
    * Développez la section **Options avancées**.
    
    * Dans le champ **Comportement**, sélectionnez **Indépendant du fuseau horaire**.
    
    * Cliquez sur **Terminé**.
    
6.  Créer un champ Fin réelle

    * Cliquez sur **Ajouter un champ**.
    
    * Entrez **Fin réelle** pour **Afficher un nom**.
    
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    
    * Dans le champ **Obligatoire**, laissez ceci comme **Optionnel**.
    
    * Développez la section **Options avancées**.
    
    * Dans le champ **Comportement**, sélectionnez **Indépendant du fuseau horaire**.
    
    * Cliquez sur **Terminé**.
    
7.  Créer un champ de code

    * Cliquez sur **Ajouter un champ**.
    
    * Entrez **Code** pour **Afficher un nom**.
    
    * Sélectionnez **Numérotation automatique** dans la liste **Type de données**.
    
    * Sélectionnez **Nombre préfixé de date** pour **Type de numérotation automatique**.
    
    * Cliquez sur **Terminé**.
    
8.  Cliquez sur **Enregistrer l’entité**

## Tâche n°3 : Créer des relations

1.  Assurez-vous que vous consultez toujours l’entité **Visite** de votre solution **Gestion du campus**. Si ce n’est pas le cas, accédez à cette entité.

2.  Créer une relation Visite - Contact

    * Sélectionnez l’onglet **Relations**.
    
    * Cliquez sur **Ajouter une relation**, puis sélectionnez **Plusieurs-à-un**
    
    * Sélectionnez **Contact** pour **Connexes (Un)** 
    
    * Entrez **Visiteur** pour **Nom complet du champ de recherche** 
    
    * Cliquez sur **Terminé**.
    
3.  Créer une relation Visite-Bâtiment

    * Cliquez sur **Ajouter une relation**, puis sélectionnez **Plusieurs-à-un**
    
    * Sélectionnez **Bâtiment** pour **Connexes (Un)** 
    
    * Cliquez sur **Terminé**.
    
4.  Cliquez sur **Enregistrer l’entité**.

5.  Sélectionnez **Solutions** dans le menu supérieur, puis cliquez sur **Publier toutes les personnalisations.**

# Exercice \#3 : Importer des données

**Objectif :** Dans cet exercice, vous allez importer des exemples de données dans la base de données Common Data Service.

## Tâche #1 : Importer une solution

Dans cette tâche, vous importerez une solution contenant le flux Power Automate requis pour terminer l’importation des données.

1. Le stockage de fichiers **DataImport_managed.zip** doit être présent sur votre bureau. Si ce n’est pas le cas, téléchargez la [Solution d’importation de données](../../Allfiles/DataImport_managed.zip).

2. Connectez-vous à <https://make.powerapps.com>.

3. Sélectionnez votre environnement de **pratique [mes initiales]** en haut à droite, si ce n’est déjà fait.

4. Sélectionnez **Solutions** dans le panneau de navigation de gauche.

5. Cliquez sur **Importer**, puis cliquez sur **Parcourir**. Parcourez et sélectionnez **DataImport_managed.zip** depuis votre bureau, puis appuyez sur **Suivant**.

>   Vous pouvez recevoir le message suivant :
>
>   Il manque des dépendances. Installez les solutions suivantes avant d’installer celle-ci.
>
>   Ce message indique que, soit le modèle de données n’est pas complet,
>   soit le préfixe de l’éditeur n’est pas **bc**, soit les noms des entités **Bâtiment** et **Visite**
>   diffèrent des noms répertoriés dans les étapes ci-dessus.

6. Appuyez sur **Suivant**. Vous êtes ensuite invité à rétablir les connexions. 

7. Développez le menu déroulant **Sélectionner une connexion**, puis sélectionnez **+ Nouvelle connexion**.

8. Une nouvelle fenêtre ou un nouvel onglet de navigation s’ouvre. Sélectionnez **Créer** lorsque vous êtes invité à créer une connexion Common Data Service. Connectez-vous si nécessaire pour terminer la création de la connexion.

9. Revenez à l’onglet précédent, à partir duquel vous aviez importé la solution.

10. Cliquez sur **Actualiser** pour actualiser la liste des connexions. 

11. Assurez-vous que la connexion que vous venez de créer est sélectionnée.

12. Appuyez sur **Importer**.

13. Attendez que l’importation soit terminée.

## Tâche n° 2 : Importer des données  

1. Ouvrez la solution **Importation de données**.

2. Vérifiez l’**état** du flux **Importation de données**.

3. Si l’**état** est **Inactif**, sélectionnez **...** en regard du champ **Importation des données**, puis sélectionnez **Activer**.

   > **Important :** Si vous recevez un message d’erreur, vérifiez que les entités et les champs que vous avez créés suivent les instructions énoncées ci-dessus.

4. Sélectionnez le composant **Importation des données**. Power Automate s’ouvre dans un nouvel onglet. Cliquez sur **Commencer** s’il est présenté avec une fenêtre contextuelle. 

5. Cliquez sur **Exécuter** puis cliquez **Exécuter le flux** lorsque vous y êtes invité.

6. Cliquez sur **Terminé**.

7. Attendez que l’instance de flux termine son exécution. Vous pouvez actualiser la table de l’**historique des exécutions de 28 jours** pour voir quand le flux s’est exécuté. Le but de ce flux était de générer des exemples de données pour les laboratoires à venir. Dans la tâche suivante, vous vérifierez que l’importation des données a réussi. 

## Tâche n° 3 : Vérifier une importation de données

1. Revenez à l’onglet Power Apps précédent. Cliquez sur **Terminé** sur la fenêtre contextuelle. Sélectionnez **Solutions** dans la barre de navigation de gauche et ouvrez votre solution de **Gestion du campus**.

2. Cliquez pour ouvrir l’entité **Visite**, puis sélectionnez l’onglet **Données**.

3. Cliquez sur **Visites actives** dans le coin supérieur droit pour afficher le sélecteur de mode, puis sélectionnez **Tous les champs**. Cela modifiera le mode utilisé pour afficher les données de visite.

    > Si l’importation a réussi, une liste des entrées de visite s’affiche.

4. Cliquez sur une valeur dans la colonne **Bâtiment** et confirmez que le formulaire de bâtiment s’ouvre dans une fenêtre distincte. Fermez cette fenêtre.

5. Cliquez sur une valeur dans la colonne **Visiteur** (vous devrez peut-être faire défiler la vue vers la droite) et vérifiez si le formulaire de contact s’ouvre dans une fenêtre distincte. Fermez cette fenêtre.

# Défis

* Envisageriez-vous d’utiliser l’activité de *rendez-vous* dans le cadre de la solution ? Qu’est-ce que cela changerait ?
* Comment faire en sorte que la fin planifiée soit ultérieure au début planifié ? 
* Comment ajouter la prise en charge de plusieurs réunions au cours d’une seule visite ?
* Comment sécuriser l’accès au bâtiment non seulement pour les contacts externes mais également pour le personnel interne ?
* Comment faire en sorte qu’une visite dans des bâtiments donnés nécessite l’approbation de la direction ? Qu’est-ce que le processus d’approbation changerait dans le modèle de données ?

