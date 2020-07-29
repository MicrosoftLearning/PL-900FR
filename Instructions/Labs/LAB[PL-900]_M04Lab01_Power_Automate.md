---
lab:
    title: 'Labo : Power Automate'
    module: 'Module 4 : Premiers pas avec Power Automate'
---

# Module 4 : Premiers pas avec Power Automate
## Labo : Power Automate

Scénario
========

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visiteurs du campus sont actuellement enregistrés dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données concernant les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel administratif et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Au cours de ce labo, vous allez créer des flux Power Automate pour automatiser différents aspects de la gestion du campus. 

Étapes de labo de haut niveau
======================

Les éléments suivants ont été identifiés comme des exigences que vous devez implémenter pour terminer le projet.

* Le code unique attribué à chaque visiteur doit être mis à sa disposition avant sa visite.
* Le personnel de sécurité doit recevoir des notifications des visiteurs dépassant leur plage horaire programmée.

## Conditions préalables

* Achèvement du labo 1 - Modélisation de données
* Application Personnel du campus créée dans la première partie du labo 2 : Application canevas (pour les tests)

Éléments à considérer avant de commencer
-----------------------------------

-   Quel est le mécanisme de distribution le plus approprié pour les codes des visiteurs.
-   Comment mesurer les dépassements de plage horaire et appliquer des stratégies strictes.

Exercice \#1 : Créer un flux de notification de visite
===============================

**Objectif :** Dans cet exercice, vous allez créer un flux Power Automate qui met en place ces conditions. La notification des visiteurs se fait par e-mail. La notification comprend le code unique attribué à la visite.

Tâche \#1 : Créer un flux
---------------------------

1.  Ouvrez la solution Gestion du campus.

    -   Connectez-vous à <https://make.powerapps.com>

    -   Sélectionnez votre **environnement**.

    -   Sélectionnez **Solutions**.

    -   Cliquez pour ouvrir la solution de **Gestion du campus**.

2.  Cliquez sur **Nouveau** et sélectionnez **Flux**. Cela ouvrira l’éditeur de flux dans une nouvelle fenêtre.

3. Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**.

4. Sélectionnez le déclencheur **Lorsqu’un enregistrement est créé**, **Mis à jour** ou **Supprimé**.

   * Sélectionnez **Créer** pour **Condition de déclenchement**
   * Sélectionnez **Visites** pour **Le nom de l’entité**
   * Sélectionnez **Organisation** dans la liste **Étendue**

5.  Cliquez sur **Nouvelle étape**. Cette étape est nécessaire pour récupérer les informations des visiteurs, y compris les e-mails.

6. Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**.

7. Sélectionnez l’action **Obtenir un enregistrement**. 

   * Sélectionnez **Contacts** comme **Nom de l’entité**
   * Recherchez du contenu dynamique, sélectionnez **Visiteur (valeur)** comme valeur pour l’**ID de l’article**

8. Cliquez sur **Nouvelle étape**. Il s’agit de l’étape qui permettra de créer et d’envoyer des e-mails au visiteur.

9. Recherchez *courrier*, sélectionnez le connecteur **Courrier** et l’action **Envoyer une notification par e-mail**. 

   * Définissez la valeur de **E-mail** sur **À**

   * Entrez **Votre visite prévue à Bellows College** comme **Sujet**

   * Tapez le texte suivant dans le **corps du message électronique** :  
        *Remarque : Le texte en gras indique le contenu dynamique qui doit être inséré à ces endroits. Il est recommandé de taper d’abord tout le texte, puis d’ajouter du contenu dynamique au bon endroit.*
     >
     > Cher {**Prénom**},
     >
     > Vous avez actuellement prévu une visite à Bellows Campus de {**Début planifié**} à {**Fin planifiée**}.
     >
     > Votre code de sécurité est {**Code**}, veuillez ne pas le partager. Vous devrez renseigner ce code lors de votre visite.
     >
     >
     > Cordialement,
     >
     > Administration du campus
     >
     > Bellows College
     
   
10.  Sélectionnez le nom du flux et renommez-le en **Notification de visite**

11.  Appuyez sur **Enregistrer**

Tâche \#2 : Validez et testez le flux.
--------------------------------

1.  Ouvrez l’application **Personnel du campus** que vous avez créée 
2.  Appuyez sur + pour ajouter un nouvel enregistrement de visite.
3.  Entrez les informations requises, puis appuyez sur **Enregistrer**
4.  Ouvrez le flux, localisez et ouvrez la plus récente **Exécution**
5.  Ouvrez l’étape **Courrier** et vérifiez que le contenu de l’e-mail a été généré correctement.

# Exercice n°2 : Créer un flux de balayage de sécurité

**Objectif :** Dans cet exercice, vous allez créer un flux Power Automate qui met en place ces conditions. Le balayage de sécurité est effectué toutes les 15 minutes et la sécurité est avertie si l’un des visiteurs a dépassé l’heure prévue.

## Tâche #1 : Créer un flux pour récupérer des enregistrements

1. Ouvrez la solution Gestion du campus.

   -   Connectez-vous à <https://make.powerapps.com>

   -   Sélectionnez votre **environnement**.

   -   Sélectionnez **Solutions**.

   -   Cliquez pour ouvrir la solution de **Gestion du campus**.

2. Cliquez sur **Nouveau** et sélectionnez **Flux**. Cela ouvrira l’éditeur de flux dans une nouvelle fenêtre.

3. Recherchez *récurrence*, sélectionnez le connecteur**Planification** et le déclencheur **Récurrence**.

4. Définissez la valeur du champ **Intervalle** sur **15 minutes**

5. Cliquez sur **Nouvelle étape**. Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**. Sélectionnez l’action **Répertorier les enregistrements**.

   * Entrez **Visites** comme **Nom de l’entité**

   * Entrez l’expression suivante comme **Requête de filtre**

     ```
     statecode eq 0 and bc_actualstart ne null and bc_actualend eq null and Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)
     ```

   Nous allons la décomposer.

   * `statecode eq 0` filtre les visites actives (où le statut est égal à Actif)
   * `bc_actualstart ne null` restreint la recherche aux visites où Début effectif a une valeur, c’est-à-dire que quelqu’un est arrivé.
   *  `bc_actualend eq null` limite la recherche aux visites où la personne n’est pas partie (le champ Fin réelle n’est pas renseigné) 
   * `Microsoft.Dynamics.CRM.OlderThanXMinutes (PropertyName = 'bc_scheduledend', PropertyValue = 15)` restreint les visites à celles qui devaient se terminer il y a plus de 15 minutes.  

6.  Cliquez sur **Nouvelle étape**. Recherchez **Appliquer**, sélectionnez l’action **Appliquer à chacun** 

7.  Sélectionnez une **valeur** de contenu dynamique en tant que **Sélectionnez un résultat à partir des étapes précédentes**.

8.  Ajoutez l’extraction de données pour l’enregistrement associé

    * Cliquez sur **Ajouter une action** à l’intérieur de la boucle.
    * Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**. 
    * Sélectionnez l’action **Obtenir un enregistrement**.
    * Cliquez sur les points de suspension (« ... »), puis sélectionnez **Renommer**. Entrez **QuelBâtiment** comme nom d’étape
    * Sélectionnez **Bâtiments** comme **Nom d’entité**
    * Sélectionnez **Bâtiment (Valeur)** comme **ID d’article**

9.  Répétez la séquence d’extraction de données précédente pour **Visiteur** et **Utilisateur**, en sélectionnant le nom de l’entité associée et en utilisant **Visiteur (Valeur)** et **Propriétaire (Valeur) **comme **ID d’article**, respectivement

10.  Ajoutez une action **Envoyer une notification par e-mail** à partir de la connexion **Courrier** tout en restant dans la connexion **Appliquer à chaque boucle**

11.  Tapez votre adresse électronique dans **À**

12.  Entrez « Contact {**Nom complet**} a dépassé sa plage horaire de visite ». **Nom complet** est un contenu dynamique de l’enregistrement de visite actuel.

13.  Entrez « C’est arrivé dans le bâtiment **Nom** », où **Nom** est le contenu dynamique de l’étape **QuelBâtiment**

14.  Localisez **Courriel principal** de l’étape **QuelUtilisateur** et insérez-le dans le champ CC (la personne qui reçoit la visite recevra une copie de l’e-mail)

15.  Sélectionnez le nom du flux **Sans titre** dans le coin supérieur gauche et renommez-le **Balayage de sécurité**

16.  Appuyez sur **Enregistrer**

## Tâche 2 : Validez et testez le flux.

1. Localisez ou créez des enregistrements de visite qui 
   1. ont un statut actif
   2.  L’heure de fin programmée est passée (de plus de 15 minutes)
   3. Le champ Début réel est renseigné.
2. Ouvrez le flux créé dans la tâche 1 et appuyez sur **Tester**
3. Sélectionnez **Je vais effectuer l’action de déclenchement.**
4. Sélectionnez **Exécuter le flux.**
5. Lorsque le flux entre en concurrence, développez **Appliquer à chacun** puis développez l’étape **Envoyer une notification par e-mail**
6. Vérifiez les valeurs **Sujet** et **Corps du message électronique**. Développez **Afficher plus** et vérifiez la valeur **CC**.
8. Accédez à la solution, cliquez sur les points de suspension (« .. .») affichés en regard du flux et sélectionnez **Désactiver**. Cela permet d’empêcher l’exécution du flux selon une planification du système de test.

# Défis

* Ajoutez des informations sur le bâtiment et mappez-les au flux de notification.
* Pouvez-vous générer un code-barres pour le code de visite ? Quand cela sera-t-il utile ?
* Comment garantir une mise en forme conviviale des dates dans le corps de l’e-mail ?
* Est-il possible de générer un tableau avec les informations des visites qui ont duré trop longtemps et d’envoyer un seul e-mail ?
