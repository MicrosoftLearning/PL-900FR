---
lab:
    title: 'Labo 01 : Modélisation de données'
    module: 'Module 03 : Introduction au Common Data Service'
---

# PL-900 : Bases-Microsoft-Power-Platform
## Module 3, Labo 1 : Modélisation des données

## Avis important concernant les locataires : solution de contournement temporaire

Depuis le 23 janvier 2020, WWL n’est plus en mesure de fournir aux participants un accès Dynamics 365 préapprovisionné et travaille sur une solution qui devrait être disponible dans les 4 à 6 prochaines semaines. Pour contourner ce problème, nous vous recommandons d’utiliser des comptes d’essai Dynamics 365. Chaque participant sera responsable de demander le sien. Pour aider les participants à obtenir les locataires Dynamics 365 (y compris le marketing), les locataires M365 seront fournis par les hébergeurs de labo autorisés. Il s’agit d’une solution à court terme. Nous tiendrons informées toutes les parties prenantes, y compris Learning Partners et les MCT, au fur et à mesure des progrès réalisés. Nous proposerons un calendrier de solutions plus durable pour le pré-approvisionnement de Dynamics 365 pour l’utilisation en labo. Travaillez main dans la main avec votre hébergeur de labo agréé pour l’approvisionnement des locataires M365 pour les participants. Suivez les instructions ci-dessous pour utiliser le locataire M365 en vue de sécuriser un test Dynamics 365 pour l’application concernée.
 
1. En utilisant vos informations d’identification M365 fournies, connectez-vous à https://admin.microsoft.com/ et acceptez les conditions.
2. Une fois connecté, accédez à https://trials.dynamics.com/. Sélectionnez la catégorie adéquate pour votre cours.
3. Sous « E-mail professionnel », entrez l’adresse e-mail des informations d’identification M365. Sous « numéro de téléphone », entrez votre propre numéro de téléphone.
4. Sélectionnez Démarrer.
5. Vous serez invité à entrer votre mot de passe pour le compte on.microsoft.com. Entrez le mot de passe du locataire M365.
6. Si vous êtes invité à accepter les termes et conditions, acceptez-les. L’approvisionnement de votre environnement peut prendre quelques minutes.

Scénario
========

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visites sur le campus sont actuellement enregistrées dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données sur les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel d’administration et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Dans ce labo, vous allez configurer un environnement, créer une base de données CDS (Common Data Service) et créer une solution pour retracer le suivi de vos modifications. Vous allez également créer un modèle de données pour prendre en charge les exigences suivantes :

-   R1 - Suivre les emplacements (bâtiments) des visites du campus
-   R2 - Enregistrer des informations de base pour identifier et suivre les visiteurs 
-   R3 - Planifier, enregistrer et gérer les visites 

Enfin, vous allez importer des exemples de données dans CDS.

Étapes de labo de haut niveau
======================

Pour préparer vos environnements d’apprentissage, vous devez :

* créer une solution et un éditeur
* ajouter les composants, nouveaux et existants, nécessaires pour répondre aux exigences de l’application. Consultez le [document de modèle de données](../../Allfiles/Labs/Campus%20Management.vsdx) pour la description des métadonnées (entités, types de champs et relations). 

Votre solution contiendra plusieurs entités une fois toutes les personnalisations terminées :

-   Contact
-   Bâtiment
-   Visite

## Conditions préalables

* Aucun

Éléments à considérer avant de commencer
-----------------------------------

* Convention d’affectation de noms
* Types de données, restrictions (par exemple, longueur maximale d’un nom)
* Formatage DateHeure pour prendre en charge une localisation facile

Exercice \#1 : Créer un environnement et une solution
==================================================

**Objectif :** Dans cet exercice, vous allez préparer l’environnement et créer une solution pour prendre en charge le processus de modélisation des données. 

Tâche \#1 : Créer un environnement
-----------------------------

Si vous ne disposez pas et n’avez pas reçu d’environnement avant l’exercice, dans cette tâche, vous allez créer un nouvel environnement de travail. Sinon, vous pouvez passer à la tâche suivante.

1.  Connectez-vous à <https://aka.ms/ppac>

2.  Sélectionnez **Environnements** et cliquez sur **Nouveau** dans le menu supérieur. Cela ouvrira
    un menu sur le côté droit de la fenêtre.

3.  Entrez **Bellows College [Votre nom de famille]** pour **Nom**.

4.  Sélectionnez **Production** dans la liste déroulante pour **Type.**

5.  Sélectionnez votre **Région**

6.  Entrez l’**objectif** de la création de cet environnement (facultatif). 
    
7.  Activez le **bouton bascule** pour **créer une base de données pour cet environnement** si vous
    souhaitez créer la base de données avec cela, sinon cette action peut être initiée une fois que
    l’environnement est configuré.

8.  Cliquez sur **Suivant**.

9.  Sélectionnez **Langue** et **Devise**. Pour les besoins de ces labos, les
    environnements ont les options **Anglais** et **Dollars américains** (USD) sélectionnées.

10. Laissez **Activer les applications Dynamics 365** désactivé aux fins de ces
    labos.

11. Laissez **Déployer des exemples d’applications et de données** désactivé aux fins de ces
    labos.

12. Cliquez sur **Enregistrer**.

13. L’approvisionnement de votre environnement peut prendre quelques minutes. Vous pouvez utiliser le bouton **Rafraîchir** pour actualiser la liste. Lorsque l’environnement est approvisionné, l’**État** bascule à Prêt.

14. Si vous n’avez pas créé votre base de données auparavant, sélectionnez votre environnement, puis cliquez sur **Créer ma base de données**. Sinon, ignorez cette étape.

    - Sélectionnez **Devise** et **Langue**. Pour les besoins de ces labos, les
    les environnements ont les options **Dollars américains** (USD) et **Anglais** sélectionnées.

    - Cliquez sur **Créer ma base de données**.

Tâche \#2 : Créer une solution et un éditeur
---------------------------------------

1.  Créer une solution

    -   Connectez-vous à <https://make.powerapps.com>

    -   Sélectionnez votre environnement dans le menu déroulant supérieur.

    -   Sélectionnez **Solutions** dans le menu de gauche, puis cliquez sur **Nouvelle solution**.

    -   Entrez **Gestion du campus** pour **Afficher un nom**.

2.  Créer un éditeur

    -   Cliquez sur le menu déroulant **Éditeur**, puis sélectionnez **+ Éditeur**.

    -   Entrez **Bellows College** dans la zone **Afficher un nom** et **bc** dans la zone **Préfixe**

    -   Cliquez sur **Enregistrer et fermer**.

3.  Terminez la création de la solution.

    -   Maintenant, cliquez sur la liste déroulante **Éditeur**, puis sélectionnez l’éditeur **Bellows College**
        que vous venez de créer.

    -   Entrez **1.0.0.0** pour **Version**, puis cliquez sur **Créer**.

Tâche \#3 : Ajouter une entité existante
-----------------------------

1.  Cliquez pour ouvrir la solution **Gestion du campus** que vous venez de créer.
2.  Cliquez sur **Ajouter existant**, puis sélectionnez **Entité**.
3.  Recherchez **Contact**, puis sélectionnez cette option.
4.  Cliquez sur **Suivant**.
5.  Cliquez sur **Sélectionner les composants**.
6.  Sélectionnez l’onglet **Vues**, puis sélectionnez la vue **Contacts actifs**. Cliquez sur
    **Ajouter**.
7.  Cliquez à nouveau sur **Sélectionner des composants**.
8.  Cliquez sur l’onglet **Formulaires**, puis sélectionnez le formulaire **Contact**.
9.  Cliquez sur **Ajouter**.
10. Vous devez sélectionner les options **1 Vue** et **1 Formulaire**. Cliquez à nouveau sur **Ajouter**.
    Cette action ajoute l’entité Contact à la solution nouvellement créée. 
21.  Votre solution doit maintenant avoir une seule entité : Contact.

Exercice \#2 : Créer des entités et des relations
========================================

**Objectif :** Dans cet exercice, vous allez créer des entités, puis ajouter des relations
entre les entités.

Tâche #1 : Créer une entité et des champs de bâtiment
-----------------------------------------

1.  Tout en continuant dans votre environnement de développement, ouvrez la solution Gestion du campus
    .
    * Connectez-vous à <https://make.powerapps.com> (si vous n’êtes pas déjà connecté)
    * Sélectionnez **Solutions**, puis cliquez pour ouvrir la solution **Gestion du campus**
          que vous venez de créer (si vous n’êtes pas déjà dans cette solution).
2.  Créer une entité de bâtiment

    -   Cliquez sur **Nouveau**, puis sélectionnez **Entité**.
    -   Entrez **Bâtiment** pour **Afficher un nom**, puis cliquez sur **Créer**. Cela
            permet de démarrer l’approvisionnement de l’entité en arrière-plan, tandis que vous pouvez commencer à ajouter des éléments
            d’autres entités et champs.

## Tâche n°2 : Créer une entité et des champs de visite

L’entité **Visite** contient des informations sur les visites du campus, y compris le bâtiment, le visiteur, l’heure prévue et l’heure réelle de chaque visite. 

Nous aimerions attribuer à chaque visite un numéro unique qui peut être facilement saisi et interprété par un visiteur lorsque cela lui est demandé pendant le processus d’enregistrement de la visite.

> [!REMARQUE]
> Nous utilisons un comportement **indépendant du fuseau horaire** pour enregistrer les informations de date et d’heure car l’heure d’une visite est *toujours* locale par rapport à l’emplacement du bâtiment et ne doit pas changer lorsqu’elle est vue depuis un autre fuseau horaire. 

1.  Sélectionnez la solution **Gestion du campus**
2. Créer une entité de visite

   * Cliquez sur **Nouveau**, puis sélectionnez **Entité**.
   * Entrez **Visite** dans le champ **Nom d’affichage**, puis cliquez sur **Créer**. Cette action débute l’approvisionnement de l’entité en arrière-plan, tandis que vous pouvez commencer à ajouter d’autres champs.

3. Créer un champ Début planifié

   * Vérifiez que l’onglet **Champs** est sélectionné, puis cliquez sur **Ajouter un champ**.
   * Entrez **Début planifié** pour **Afficher un nom**.
   * Sélectionnez **Date et heure** dans la liste **Type de données**.
   * Activez la case à cocher **Obligatoire**.
   * Développez la section **Avancé**.
   * Sélectionnez **Sans fuseau horaire** dans la liste **Comportement**.
   * Cliquez sur **Terminé**.

4.  Créer un champ Fin planifiée

    * Cliquez sur **Ajouter un champ**.
    * Entrez **Fin planifiée** dans le champ **Nom d’affichage**.
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    * Activez la case à cocher **Obligatoire**.
    * Développez la section **Avancé**.
    * Sélectionnez **Sans fuseau horaire** dans la liste **Comportement**.
    * Cliquez sur **Terminé**.
6.  Créer un champ Début réel
    * Cliquez sur **Ajouter un champ**.
    * Entrez **Début réel** pour **Afficher un nom**.
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    * Développez la section **Avancé**.
    * Sélectionnez **Sans fuseau horaire** dans la liste **Comportement**.
    * Cliquez sur **Terminé**.
7.  Créer un champ Fin réelle
    * Cliquez sur **Ajouter un champ**.
    * Entrez **Fin réelle** pour **Afficher un nom**.
    * Sélectionnez **Date et heure** dans la liste **Type de données**.
    * Développez la section **Avancé**.
    * Sélectionnez **Sans fuseau horaire** dans la liste **Comportement**.
    * Cliquez sur **Terminé**.
7.  Créer un champ de code
    * Cliquez sur **Ajouter un champ**.
    * Entrez **Code** pour **Afficher un nom**.
    * Sélectionnez **Numérotation automatique** dans la liste **Type de données**.
    * Sélectionnez **Nombre préfixé de date** pour **Type de numérotation automatique**.
    * Cliquez sur **Terminé**.
8.  Cliquez sur **Enregistrer l’entité**

Tâche n°3 : Créer des relations
------------------------------

1.  Sélectionnez la solution **Gestion du campus**.
4.  Créer une relation Visite - Contact
    * Cliquez pour ouvrir l’entité **Visite**.
    * Sélectionnez l’onglet **Relations**.
    * Cliquez sur **Ajouter une relation**, puis sélectionnez **Plusieurs-à-un**
    * Sélectionnez Contact dans la liste **Connexes (Un)** 
    * Entrez **Visiteur** pour **Nom complet du champ de recherche** 
    * Cliquez sur **Terminé**.
3.  Créer une relation Visite-Bâtiment
    * Cliquez pour ouvrir l’entité **Visite**.
    * Sélectionnez l’onglet **Relations**.
    * Cliquez sur **Ajouter une relation**, puis sélectionnez **Plusieurs-à-un**
    * Sélectionnez un bâtiment pour **Associé (un)** 
    * Cliquez sur **Terminé**.
4.  Cliquez sur **Enregistrer l’entité**.
5.  Sélectionnez **Solutions** dans le menu supérieur, puis cliquez sur **Publier toutes
    Personnalisations.**

# Exercice \#3 : Importer des données

**Objectif :** Dans cet exercice, vous allez importer des exemples de données dans la base de données Common Data Service.

## Tâche #1 : Importer un mappage de données

1. Téléchargez [CampusDataMap.xml](../../Allfiles/Labs/CampusDataMap.xml).
2. Accédez à Centre d’administration Power Platform à l’adresse https://aka.ms/ppac, puis connectez-vous.
3. Dans la page de navigation de gauche, sélectionnez Environnements, puis l’environnement cible et cliquez sur **Réglages**.
4. Développez la section **Gestion des données**, puis sélectionnez **Mappages de données**. Cette action permet d’ouvrir un écran de mappage d’importation dans un nouvel onglet du navigateur.
5. Cliquez sur **Importer**, puis sur **Choisir un fichier**. Recherchez et sélectionnez **CampusDataMap.xml**, téléchargé plus tôt, puis appuyez sur **OK**.

## Tâche n°2 : Importer des données  

1. Téléchargez [CampusData.zip](../../Allfiles/Labs/CampusData.zip).
2. Revenez à l’onglet d’origine avec l’environnement.  
3. Appuyez sur **Assistants d’importation de données**.
4. Appuyez sur **IMPORTER DES DONNÉES**.
5. Cliquez sur **Choisir un fichier**, puis recherchez et sélectionnez **CampusData.zip**, téléchargé plus tôt.
6. Appuyez sur **Suivant**, puis à nouveau sur **Suivant**.
7. Sélectionnez **CampusImportDataMap**, puis appuyez sur **Suivant**.
8. Examinez le résumé du mappage, puis appuyez sur **Suivant**, puis sur **Soumettre**.
9. Appuyez sur **Terminer**.

## Tâche n°3 : Vérifier une importation de données

1. Sélectionnez la solution **Gestion du campus**.
2. Sélectionnez l’entité **Visite**, puis l’onglet **Données**.
3. Appuyez sur le sélecteur de vue dans le coin supérieur droit, puis sélectionnez **Tous les champs**
4. Si l’importation a réussi, vous devriez voir une liste des entrées de visite.
5. Cliquez sur une valeur dans la colonne **Bâtiment** et confirmez que le formulaire de bâtiment s’ouvre dans une fenêtre distincte.
6. Cliquez sur une valeur dans la colonne **Visiteur** (vous devrez peut-être faire défiler la vue vers la droite) et confirmez que le formulaire de contact s’ouvre dans une fenêtre distincte.

# Défis

* Envisageriez-vous d’utiliser l’activité de *rendez-vous* dans le cadre de la solution ? Qu’est-ce que cela changerait ?
* Comment faire en sorte que la fin planifiée soit ultérieure au début planifié ? 
* Ajoutez la prise en charge de plusieurs réunions au cours d’une seule visite.
* Sécurisez l’accès au bâtiment non seulement pour les contacts externes mais également pour le personnel interne.
* Les visites de certains bâtiments nécessitent l’approbation de la direction. Qu’est-ce que le processus d’approbation changerait dans le modèle de données ?

