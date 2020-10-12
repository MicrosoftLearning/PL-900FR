---
lab:
    title: 'Labo : Power Automate'
    module: 'Module 4 : Premiers pas avec Power Automate'
---

# Module 4 : Premiers pas avec Power Automate
## Labo : Power Automate

Scénario
========

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visiteurs du campus sont actuellement enregistrés dans des journaux papier. Les informations ne sont pas entrées de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données concernant les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel administratif et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Au cours de ce labo, vous allez créer des flux Power Automate pour automatiser différents aspects de la gestion du campus. 

Étapes de labo de haut niveau
======================

Les éléments suivants ont été identifiés comme des exigences que vous devez implémenter pour finaliser le projet :

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

3. Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**.

4. Sélectionnez le déclencheur **Lorsqu’un enregistrement est créé**, **Mis à jour** ou **Supprimé**.

   * Sélectionnez **Créer** pour **Condition de déclenchement**
   * Sélectionnez **Visites** pour **Le nom de l’entité**
   * Sélectionnez **Organisation** dans la liste **Étendue**

5.  Cliquez sur **Nouvelle étape**. Cette étape est nécessaire pour récupérer les informations des visiteurs, y compris les e-mails.

6. Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**.

7. Sélectionnez l’action **Obtenir un enregistrement**. 

   * Sélectionnez **Contacts** comme **Nom de l’entité**
   * Dans le champ **ID de l’élément**, sélectionnez **Visiteur (valeur)** dans la liste Contenu dynamique.

8. Cliquez sur **Nouvelle étape**. Il s’agit de l’étape qui permettra de créer et d’envoyer des e-mails au visiteur.

9. Recherchez *courrier*, sélectionnez le connecteur **Courrier** et l’action **Envoyer une notification par e-mail**. 
   * Si vous êtes invité à accepter les conditions d’utilisation de cette action, cliquez sur **Accepter**.
   
   * Sélectionnez le champ **À** puis **E-mail** dans le volet Contenu dynamique.

   * Entrez **Votre visite prévue à Bellows College** dans le champ **Objet**.

   * Entrez le texte suivant dans le **Corps de l’e-mail** :  
        *Remarque : Le contenu dynamique doit être placé où les champs sont nommés entre crochets. Il est recommandé de taper d’abord tout le texte, puis d’ajouter le contenu dynamique approprié au bon endroit.*

   ```
    Cher/Chère {Prénom},

    Vous avez programmé une visite à Bellows Campus du {Début prévu} au {Fin prévue}.

    Votre code de sécurité est {Code}, veuillez ne le donner à personne. Vous devrez renseigner ce code lors de votre visite.


    Cordialement,

    L’administration du campus
    Bellows College
   ```
   
10.  Sélectionnez le nom du flux **Sans titre** dans la partie supérieure et renommez-le **Avis de visite**

11.  Appuyez sur **Enregistrer**

Tâche \#2 : Validez et testez le flux.
--------------------------------

1.  Ouvrez l’application **Personnel du campus** que vous avez créée 
2.  Appuyez sur + pour ajouter un nouvel enregistrement de visite.
3.  Entrez les informations requises, puis appuyez sur **Enregistrer**
4.  Ouvrez le flux, localisez et ouvrez la plus récente **Exécution**
5.  Ouvrez l’étape **Courrier** et vérifiez que le contenu de l’e-mail a été généré correctement.

# Exercice #2 : Créer un flux de balayage de sécurité

**Objectif :** Dans cet exercice, vous allez créer un flux Power Automate qui met en place ces conditions. Le balayage de sécurité est effectué toutes les 15 minutes et la sécurité est avertie si l’un des visiteurs a dépassé l’heure prévue.

## Tâche #1 : Créer un flux pour récupérer des enregistrements

1. Ouvrez la solution Gestion du campus.

   -   Connectez-vous à <https://make.powerapps.com>

   -   Sélectionnez votre **environnement**.

   -   Sélectionnez **Solutions**.

   -   Cliquez pour ouvrir la solution de **Gestion du campus**.

2. Cliquez sur **Nouveau** et sélectionnez **Flux**. Cela ouvrira l’éditeur de flux dans une nouvelle fenêtre.

3. Recherchez *récurrence*, sélectionnez le connecteur**Planification**, puis le déclencheur **Récurrence**.

4. Définissez la valeur du champ **Intervalle** sur **15 minutes**

5. Cliquez sur **Nouvelle étape**. Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**. Sélectionnez l’action **Répertorier les enregistrements**.

   * Entrez **Visites** comme **Nom de l’entité**
   
   * Cliquez sur **Afficher les options avancées**

   * Entrez l’expression suivante comme **Requête de filtre**

     ```
     statecode eq 0 et bc_actualstart ne null et bc_actualend eq null et Microsoft.Dynamics.CRM.OlderThanXMinutes(PropertyName='bc_scheduledend',PropertyValue=15)
     ```

   Nous allons la décomposer.

   * `statecode eq 0` filtre les visites actives (où le statut est égal à Actif)
   * `bc_actualstart ne null` restreint la recherche aux visites où Début effectif a une valeur, c’est-à-dire que quelqu’un est arrivé.
   * `bc_actualend eq null` limite la recherche aux visites où la personne n’est pas partie (le champ Fin réelle n’est pas renseigné) 
   * `Microsoft.Dynamics.CRM.OlderThanXMinutes (PropertyName = 'bc_scheduledend', PropertyValue = 15)` restreint les visites à celles qui devaient se terminer il y a plus de 15 minutes.  

6.  Cliquez sur **Nouvelle étape**. Recherchez **Appliquer**, sélectionnez l’action **Appliquer à chacun** 

7.  Sélectionnez une **valeur** dans le contenu dynamique du champ **Sélectionner un résultat à partir des étapes précédentes**.

8.  Accédez aux données sur le bâtiment de l’enregistrement connexe

    * Cliquez sur **Ajouter une action** à l’intérieur de la boucle.
    * Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**. 
    * Sélectionnez l’action **Obtenir un enregistrement**.
    * Cliquez sur les points de suspension (« ... ») affichés en regard de l’option **Accéder à un enregistrement** et sélectionnez **Renommer**. Entrez **QuelBâtiment** comme nom d’étape
    * Sélectionnez **Bâtiments** comme **Nom d’entité**
    * Sélectionnez **Bâtiment (valeur)** comme **ID de l’élément** depuis le contenu dynamique

9.  Accédez aux données Visiteur pour l’enregistrement connexe

    * Cliquez sur **Ajouter une action** à l’intérieur de la boucle.
    * Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**. 
    * Sélectionnez l’action **Obtenir un enregistrement**.
    * Cliquez sur les points de suspension (« ... ») affichés en regard de l’option **Accéder à un enregistrement** et sélectionnez **Renommer**. Entrez **GetVisitor** comme nom d’étape
    * Sélectionnez **Visites** comme **Nom de l’entité**
    * Sélectionnez **Visiteur (valeur)** comme **ID de l’élément** dans le contenu dynamique
    
10.  Accédez aux données Propriétaire pour l’enregistrement connexe

    * Cliquez sur **Ajouter une action** à l’intérieur de la boucle.
    * Recherchez **Actuel** et sélectionnez le connecteur **Common Data Service (Environnement actuel)**. 
    * Sélectionnez l’action **Obtenir un enregistrement**.
    * Cliquez sur les points de suspension (« ... ») affichés en regard de l’option **Accéder à un enregistrement** et sélectionnez **Renommer**. Entrez **GetUser** comme nom d’étape
    * Sélectionnez **Visites** comme **Nom de l’entité**
    * Sélectionnez **Propriétaire (valeur)** comme **ID de l’élément** dans le contenu dynamique

11.  Ajoutez l’action **Envoyer une notification par e-mail** depuis la connexion **Messagerie**, tout en restant au niveau de l’option **Appliquer à chaque boucle**

12.  Tapez votre adresse électronique dans **À**

13.  Entrez « Le contact {**Visiteur (valeur)**} est resté trop longtemps » dans le champ **Objet**. **Visiteur (valeur)** est un contenu dynamique de l’étape **GetVisitor**.

14.  Entrez « C’est arrivé dans le bâtiment {**Nom**} », dans le champ **Corps**. **Nom** est un contenu dynamique de l’étape **GetBuilding**.

15.  Cliquez sur **Afficher les options avancées**.

16.  Localisez **Courriel principal** de l’étape **QuelUtilisateur** et insérez-le dans le champ CC (la personne qui reçoit la visite recevra une copie de l’e-mail)

17.  Sélectionnez le nom du flux **Sans titre** dans le coin supérieur gauche et renommez-le **Balayage de sécurité**

16.  Appuyez sur **Enregistrer**

## Tâche #2 : Validez et testez le flux.

1. Localisez ou créez des enregistrements de visite qui :
   1. ont un statut actif
   2. L’heure de fin programmée est passée (de plus de 15 minutes)
   3. Le champ Début réel est renseigné.
2. Accédez à votre solution et localisez le flux **Balayage de sécurité**. Cliquez sur les points de suspension (« ... ») puis sélectionnez **Modifier**.
3. Lorsque votre flux s’ouvre, cliquez sur **Tester**.
4. Sélectionnez **Je vais effectuer l’action de déclenchement**.
5. Cliquez sur **Tester**, puis sur **Exécuter le flux**.
6. Lorsque le flux est terminé, cliquez sur **Terminé**. 
7. Développez **Appliquer à chacun**, puis développez les étapes **Envoyer une notification par e-mail** Vérifiez les valeurs **Sujet** et **Corps du message électronique**. Développez **Afficher plus** et vérifiez la valeur **CC**.
8. Accédez à la solution, cliquez sur les points de suspension (« ... ») affichés en regard du flux, puis sélectionnez **Désactiver**. Cela permet d’empêcher l’exécution du flux selon une planification du système de test.

# Défis

* Ajoutez des informations sur le bâtiment et mappez-les au flux de notification.
* Pouvez-vous générer un code-barres pour le code de visite ? Quand cela sera-t-il utile ?
* Comment garantir une mise en forme conviviale des dates dans le corps de l’e-mail ?
* Est-il possible de générer un tableau avec les informations des visites qui ont duré trop longtemps et d’envoyer un seul e-mail ?
