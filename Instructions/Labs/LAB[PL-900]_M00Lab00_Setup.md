---
lab:
    title: 'Labo : Valider l’environnement de labo'
    module: 'Module 0 : Présentation du cours'
---

Module 0 : Présentation du cours
=================================

## Labo : validation d’un environnement de laboratoire

Scénario
--------

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visiteurs du campus sont actuellement enregistrés dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données concernant les visites sur l’ensemble du campus.

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel administratif et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus.

Dans ce labo du module 0, vous allez acquérir un locataire d’essai Power Platform et accéder au centre d’administration Power Platform. Dans le Centre d’administration, vous allez créer votre environnement **Exercices pratiques**, dans lequel vous effectuerez la majorité de votre travail de labo.

## Exercice n°1 - Configuration

### Tâche n°1 - Acquérir votre locataire d’essai Power Platform

1. Copiez vos **informations d’identification Microsoft 365** à partir de l’hébergeur de labo autorisé.

2. Accédez à <https://powerapps.microsoft.com> et cliquez sur **Démarrer gratuitement.**

3. En dessous de **Démarrer**, saisissez l’adresse e-mail de vos informations d’identification Microsoft 365 dans la zone de texte qui indique **Entrez votre adresse e-mail professionnelle.**

4. Une invite apparaît indiquant que vous avez un compte existant avec Microsoft. Sélectionnez **Se connecter.**

5. Saisissez le mot de passe fourni par l’hébergeur de labo autorisé. 

6. Sélectionnez **Oui** pour rester connecté.

### Tâche n°2 : Créer un environnement

1.  Accédez à <https://admin.powerplatform.microsoft.com> et connectez-vous avec vos informations d’identification Microsoft 365 si vous y êtes à nouveau invité.

2. Sélectionnez **Environnements** et cliquez sur **+Nouveau.**

    - Pour le **Nom**, saisissez **Exercice pratique [Mes initiales].** (Exemple : Exercice pratique AJ.)
    
    - Pour le **Type**, sélectionnez **Essai** (ne sélectionnez pas l’option d’essai (basée sur un abonnement)).
    
    - Faites basculer **Créer une base de données pour cet environnement ?** sur **Oui.**
    
    - Laissez toutes les autres sélections par défaut et cliquez sur **Suivant.**
    
    - Dans l’onglet suivant, laissez toutes les sélections par défaut et cliquez sur **Enregistrer.**

3. Votre environnement **Exercice pratique** doit maintenant apparaître dans la liste des environnements. 

    > L’approvisionnement de votre environnement peut prendre quelques minutes. Actualisez la page si nécessaire.

# Exercice \#2 : Configurer un portail Power Apps

**Objectif :** L’approvisionnement d’un portail Power Apps peut prendre un certain temps. Au cours de cet exercice, vous apprendrez à créer votre portail Power Apps dans votre environnement afin que le processus d’approvisionnement puisse être lancé. Vous utiliserez ce portail dans un labo ultérieur.

## Tâche n°1 : Créez un portail Power Apps

1.  Connectez-vous à <https://make.powerapps.com>

2.  Si l’**Environnement** affiché en haut à droite n’est pas votre environnement de pratique, sélectionnez votre environnement.

3.  Cliquez sur le panneau **Portail à partir de zéro ** sous **Créer votre propre application**

    > Si vous ne voyez pas cette option, essayez de faire un zoom arrière.

4.  Fournissez de nouveaux détails sur le portail

    -   Saisissez **Visiteurs du Bellows College** comme **Nom** du portail

    -   Fournissez une URL unique : **quelque chose**.powerappsportals.com (si le nom est déjà pris, choisissez-en un autre)

    -   Sélectionnez un **Langage** pour le portail de base

    -   Cliquez sur **Créer**

    > Le processus d’approvisionnement du portail durera de 30 à 45 minutes. Vous n’avez pas à attendre, le processus se poursuit lors du passage au module suivant.
