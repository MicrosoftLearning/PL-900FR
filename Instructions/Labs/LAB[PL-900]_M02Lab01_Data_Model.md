---
lab:
    title: 'Labo : Modélisation de données'
    module: 'Module 2 : Introduction au Common Data Service'
---

# Module 2 : Introduction au Common Data Service
## Labo : Modélisation de données


# Scénario
    
Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visites sur le campus sont actuellement enregistrées dans des journaux papier. Les informations ne sont pas entrées de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données concernant les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel administratif et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Dans ce labo, vous allez configurer un environnement, créer une base de données CDS (Common Data Service) et créer une solution pour suivre vos modifications. Vous allez également créer un modèle de données pour prendre en charge les exigences suivantes :

-   R1 - Suivre les emplacements (bâtiments) des visites du campus
-   R2 - Enregistrer des informations de base pour identifier et suivre les visiteurs 
-   R3 - Planifier, enregistrer et gérer les visites 

Enfin, vous allez importer des exemples de données dans Common Data Service.

# Étapes de labo de haut niveau

Pour préparer vos environnements d’apprentissage, vous devez :

* créer une solution et un éditeur
* ajouter les composants, nouveaux et existants, nécessaires pour répondre aux exigences de l’application. Consultez le [document de modèle de données](https://github.com/MicrosoftLearning/PL-900-Microsoft-Power-Platform-Fundamentals/raw/master/Allfiles/Labs/Campus%20Management.png) pour la description des métadonnées (entités et relations). Utilisez le raccourci CTRL + clic ou cliquez avec le bouton droit sur le lien pour ouvrir le document de modèle de données dans une nouvelle fenêtre.

Votre solution contiendra plusieurs entités une fois toutes les personnalisations terminées :

-   Contact
-   Bâtiment
-   Visite

## Conditions préalables :

* Avoir terminé le **Module 0 - Labo 0 - Valider l’environnement de laboratoire**

## Éléments à considérer avant de commencer :

* Convention d’affectation de noms
* Types de données, restrictions (par exemple, longueur maximale d’un nom)
* Formatage DateHeure pour prendre en charge une localisation facile

# Exercice \#1 : Créer une solution

**Objectif :** Au cours de cet exercice, vous allez préparer l’environnement et créer une solution pour prendre en charge le processus de modélisation des données. 

## Tâche \#1 : Créer une solution et un éditeur

1.  Créer une solution

    -   Connectez-vous à <https://make.powerapps.com>. Vous devrez peut-être vous authentifier à nouveau. Cliquez sur **Se connecter** et suivez les instructions si nécessaire.

    -   Sélectionnez votre environnement en cliquant sur **Environnement** dans le coin supérieur droit de l’écran et choisissez votre environnement dans le menu déroulant.

    -   Sélectionnez **Solutions** dans le menu de gauche, puis cliquez sur **Nouvelle solution**.

    -   Entrez [Votre Nom] **Gestion du campus** pour **Afficher un nom**.

2.  Créer un éditeur

    -   Cliquez sur le menu déroulant **Éditeur**, puis sélectionnez **Éditeur**.

    -   Dans la fenêtre qui apparaît, entrez **Bellows College** dans la zone **Afficher un nom** et **bc** dans la zone **Préfixe**

    -   Cliquez sur **Enregistrer et fermer**. 
    
    -   Cliquez sur **Terminé** dans la fenêtre contextuelle.

3.  Terminez la création de la solution.

    -   Maintenant, cliquez sur la liste déroulante **Éditeur**, puis sélectionnez l’éditeur **Bellows College**
        que vous venez de créer.

    -   Vérifiez que **Version** est défini sur **1.0.0.0** 
    
    -   Cliquez sur **Créer**.

## Tâche \#2 : Ajouter une entité existante

1.  Cliquez pour ouvrir la solution **Gestion du campus** que vous venez de créer.
2.  Cliquez sur **Ajouter existant**, puis sélectionnez **Entité**.
3.  Recherchez **Contact** et sélectionnez-le.
4.  Cliquez sur **Suivant**.
5.  Cliquez sur **Sélectionner les composants**.
6.  Sélectionnez l’onglet **Vues**, puis sélectionnez la vue **Contacts actifs**. Cliquez sur
    **Ajouter**.
7.  Cliquez à nouveau sur **Sélectionner des composants**.
8.  Cliquez sur l’onglet **Formulaires**, puis sélectionnez le formulaire **Contact**.
9.  Cliquez sur **Ajouter**.
10. Vous devez sélectionner les options **1 Vue** et **1 Formulaire**. Cliquez sur **Ajouter**.
    Cela ajoutera l’entité Contact avec la vue et le formulaire sélectionnés à la solution nouvellement créée. 
11. Votre solution doit maintenant avoir une seule entité : Contact.

# Exercice \#2 : Créer des entités et des relations

**Objectif :** Dans cet exercice, vous allez créer des entités, puis ajouter des relations
entre les entités.

## Tâche #1 : Créer une entité et des champs de bâtiment

1.  Votre navigateur doit toujours être ouvert sur la solution Gestion du campus. Si ce n’est pas le cas, ouvrez la solution Gestion du campus en procédant comme suit :
    * Connectez-vous à <https://make.powerapps.com> (si vous n’êtes pas déjà connecté)
    * Sélectionnez **Solutions**, puis cliquez pour ouvrir la solution **Gestion du campus**
          que vous venez de créer.
2.  Créer une entité de bâtiment

    -   Cliquez sur **Nouveau**, puis sélectionnez **Entité**.
    -   Entrez **Bâtiment** pour **Afficher un nom**. 
    -   Cliquez sur **Terminé**. Cette action
            permet de démarrer l’approvisionnement de l’entité en arrière-plan, tandis que vous pouvez commencer à ajouter des éléments
            d’autres entités et champs.

## Tâche #2 : Créer une entité et des champs de visite

L’entité **Visite** contient des informations sur les visites du campus, y compris le bâtiment, le visiteur, l’heure prévue et l’heure réelle de chaque visite. 

Nous aimerions attribuer à chaque visite un numéro unique qui peut être facilement saisi et interprété par un visiteur lorsque cela lui est demandé pendant le processus d’enregistrement de la visite.

> [REMARQUE]
> Nous utilisons un comportement **indépendant du fuseau horaire** pour enregistrer les informations de date et d’heure car l’heure d’une visite est *toujours* locale par rapport à l’emplacement du bâtiment et ne doit pas changer lorsqu’elle est vue depuis un autre fuseau horaire. 

1.  Sélectionnez votre solution **Gestion du campus**.
2. Créer une entité de visite

   * Cliquez sur **Nouveau**, puis sélectionnez **Entité**.
   * Entrez **Visite** dans la zone **Afficher un nom**. 
   * Cliquez sur **Terminé**. Cette action débute l’approvisionnement de l’entité en arrière-plan, tandis que vous pouvez commencer à ajouter d’autres champs.

3. Créer un champ Début planifié

   * Vérifiez que l’onglet **Champs** est sélectionné, puis cliquez sur **Ajouter un champ**.
   * Entrez **Début planifié** pour **Afficher un nom**.
   * Sélectionnez **Date et heure** dans la liste **Type de données**.
   * Dans le champ **Requis**, sélectionnez **Requis**.
   * Développez la section **Options avancées**.
   * Dans le champ **Comportement**, sélectionnez **Sans fuseau horaire**.
   * Cliquez sur **Terminé**.

4.  Créer un champ Fin planifiée

    * Cliquez sur **Ajouter un champ**.
    * Entrez **Fin planifiée** dans le champ **Nom d’affichage**.
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    * Dans le champ **Requis**, sélectionnez **Requis**.
    * Développez la section **Options avancées**.
    * Dans le champ **Comportement**, sélectionnez **Sans fuseau horaire**.
    * Cliquez sur **Terminé**.
    
6.  Créer un champ Début réel

    * Cliquez sur **Ajouter un champ**.
    * Entrez **Début réel** pour **Afficher un nom**.
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    * Développez la section **Options avancées**.
    * Dans le champ **Comportement**, sélectionnez **Sans fuseau horaire**.
    * Cliquez sur **Terminé**.
    
7.  Créer un champ Fin réelle

    * Cliquez sur **Ajouter un champ**.
    * Entrez **Fin réelle** pour **Afficher un nom**.
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    * Développez la section **Options avancées**.
    * Dans le champ **Comportement**, sélectionnez **Sans fuseau horaire**.
    * Cliquez sur **Terminé**.
    
7.  Créer un champ de code

    * Cliquez sur **Ajouter un champ**.
    * Entrez **Code** pour **Afficher un nom**.
    * Sélectionnez **Numérotation automatique** dans la liste **Type de données**.
    * Sélectionnez **Nombre préfixé de date** pour **Type de numérotation automatique**.
    * Cliquez sur **Terminé**.
    
8.  Cliquez sur **Enregistrer l’entité**

## Tâche #3 : Créer des relations

1.  Vérifiez que vous visualisez encore l’entité **Visite** de votre solution **Gestion du campus**. Sinon, accédez à cette page.
2.  Créer une relation Visite - Contact
    * Sélectionnez l’onglet **Relations**.
    * Cliquez sur **Ajouter une relation**, puis sélectionnez **Plusieurs-à-un**
    * Sélectionnez **Contact** pour **Connexes (Un)** 
    * Entrez **Visiteur** pour **Nom complet du champ de recherche** 
    * Cliquez sur **Terminé**.
3.  Créer une relation Visite-Bâtiment
    * Cliquez sur **Ajouter une relation**, puis sélectionnez **Plusieurs-à-un**
    * Sélectionnez **Bâtiment** pour **Connexes (un)** 
    * Cliquez sur **Terminé**.
4.  Cliquez sur **Enregistrer l’entité**.
5.  Sélectionnez **Solutions** dans le menu supérieur, puis cliquez sur **Publier toutes les personnalisations.**

# Exercice \#3 : Importer des données

**Objectif :** Dans cet exercice, vous allez importer des exemples de données dans la base de données Common Data Service.

## Tâche #1 : Importer un mappage de données

1. Téléchargez [CampusDataMap.xml](../../Allfiles/Labs/CampusDataMap.xml) si ce n’est déjà fait.
2. Accédez au Centre d’administration Power Platform à l’adresse <https://admin.powerplatform.microsoft.com>, puis connectez-vous.
3. Sélectionnez votre environnement Bellows College.
4. Cliquez sur **Paramètres** dans la partie supérieure.
5. Développez la section **Gestion des données**, puis sélectionnez **Mappages de données**. Cette action permet d’ouvrir un écran de mappage d’importation dans un nouvel onglet du navigateur.
6. Cliquez sur **Importer**, puis sur **Choisir un fichier**. Recherchez et sélectionnez **CampusDataMap.xml**, téléchargé plus tôt, puis appuyez sur **OK**. 
7. Le fichier Campus Data Map doit maintenant être importé avec succès. Si vous rencontrez une erreur, revenez en arrière et vérifiez que vous avez créé toutes les entités et champs requis à partir des tâches précédentes.
8. Sélectionnez **Solutions** dans le menu supérieur, puis cliquez sur **Publier toutes les personnalisations.**

## Tâche #2 : Importer des données  

1. Téléchargez [CampusData.zip](../../Allfiles/Labs/CampusData.zip).
2. Accédez au Centre d’administration Power Platform à l’adresse <https://admin.powerplatform.microsoft.com>.
3. Sélectionnez votre environnement Bellows College.
4. Cliquez sur **Paramètres** dans la partie supérieure.
5. Développez la section **Gestion des données**, puis sélectionnez **Assistant Importation de données**.
6. Appuyez sur **IMPORTER DES DONNÉES**.
7. Cliquez sur **Choisir un fichier**, puis recherchez et sélectionnez **CampusData.zip**, téléchargé plus tôt.
8. Appuyez sur **Suivant**, puis à nouveau sur **Suivant**.
9. Sélectionnez **CampusImportDataMap**, puis appuyez sur **Suivant**.
10. Examinez le résumé du mappage, puis appuyez sur **Suivant**, puis sur **Soumettre**.
11. Appuyez sur **Terminer**.
12. L’importation des données va maintenant commencer. Vous pouvez maintenant utiliser le bouton Actualiser dans le volet droit **Mes importations** pour actualiser le tableau et affecter aux quatre importations le motif de statut **Terminé**. Cela peut prendre quelques minutes.

## Tâche #3 : Vérifier une importation de données

1. Sélectionnez la solution **Gestion du campus**. Si vous ne l’avez pas encore ouvert, accédez à make.powerapps.com et cliquez sur solutions dans le volet gauche pour localiser votre solution.
2. Sélectionnez l’entité **Visite**, puis l’onglet **Données**.
3. Cliquez sur **Visites actives** dans le coin supérieur droit pour afficher le sélecteur de vue, puis sélectionnez **Tous les champs**
4. Si l’importation a réussi, la liste des entrées de visite s’affiche.
5. Cliquez sur une valeur dans la colonne **Bâtiment** et confirmez que le formulaire Bâtiment s’ouvre dans une fenêtre distincte.
6. Cliquez sur une valeur dans la colonne **Visiteur** (vous devrez peut-être faire défiler la vue vers la droite) et confirmez que le formulaire Contact s’ouvre dans une fenêtre distincte.

# Défis

* Envisageriez-vous d’utiliser l’activité de rendez-vous dans le cadre de la solution ? Qu’est-ce que cela changerait ?
* Comment faire en sorte que la fin planifiée soit ultérieure au début planifié ? 
* Ajoutez la prise en charge de plusieurs réunions au cours d’une seule visite.
* Sécurisez l’accès au bâtiment non seulement pour les contacts externes mais également pour le personnel interne.
* Les visites de certains bâtiments nécessitent l’approbation de la direction. Qu’est-ce que le processus d’approbation changerait dans le modèle de données ?

