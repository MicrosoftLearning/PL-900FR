---
lab:
    title: 'Labo 7 : Comment créer un tableau de bord simple'
    module: ' Module 5 : Premiers pas avec Power BI'
---

# Module 5 : Premiers pas avec Power BI
## Labo : Comment créer un tableau de bord simple

# Scénario

Bellows College est une organisation éducative disposant de plusieurs bâtiments sur le campus. Les visiteurs du campus sont actuellement enregistrés dans des journaux papier. Les informations ne sont pas saisies de manière cohérente et il n’y a aucun moyen de collecter ni d’analyser les données concernant les visites sur l’ensemble du campus. 

L’administration du campus souhaite moderniser son système d’inscription des visiteurs où l’accès aux bâtiments est contrôlé par le personnel de sécurité et toutes les visites doivent être pré-enregistrées et enregistrées par leurs hôtes.

Tout au long de ce cours, vous créerez des applications et effectuerez une automatisation pour permettre au personnel administratif et de sécurité du Bellows College de gérer et de contrôler l’accès aux bâtiments du campus. 

Dans ce labo, vous allez créer un tableau de bord Power BI qui visualise les données sur les visites sur le campus.

# Étapes de labo de haut niveau

Nous allons suivre les étapes ci-dessous pour concevoir et créer le tableau de bord Power BI :

-   Connectez-vous à Common Data Service 
-   Transformez les données pour inclure des descriptions conviviales pour les enregistrements associés (recherches)
-   Créez et publiez un rapport avec diverses visualisations des informations sur les visites du campus
-   Utiliser une requête en langage naturel pour créer des visualisations supplémentaires
-   Créer une vue mobile du tableau de bord Power BI


## Prérequis

* Achèvement du **labo 0 du module 0 : Valider l’environnement de laboratoire**
* Achèvement du **labo 1 du module 2 : Introduction à Common Data Service**

## Éléments à considérer avant de commencer

-   À quel public ce rapport est-il destiné ?
-   Comment les participants utiliseront-t-il le rapport ? Appareil courant ? Emplacement ?
-   Avez-vous suffisamment de données à visualiser ?
-   Quelles sont les caractéristiques qu’il est possible d’utiliser pour analyser les données sur les visites ?

# Exercice \#1 : Créer des rapports Power BI 

**Objectif :** Dans cet exercice, vous allez créer un rapport Power BI basé sur les données de la base de données Common Data Service.

## Tâche n°1 : Installer Power BI Desktop/Préparer Power BI service

1. Suivez les instructions ci-dessous pour configurer Power BI : 

    - Si Power BI Desktop est **déjà** installé, passez directement à la [Tâche n°2](#task-2-prepare-data).
    
    - Si vous n’avez pas installé Power BI Desktop, passez à l’**Étape n°2**.
    
    - Si vous ne disposez pas des autorisations requises ou si vous rencontrez des problèmes lors de l’exécution de Power BI Desktop, passez à l’**Étape n°4**.

2. Accédez à [https://aka.ms/pbidesktopstore](https://aka.ms/pbidesktopstore) pour télécharger et installer Power BI Desktop.

    > [!IMPORTANT]
    > Si vous rencontrez des problèmes lors de l’installation de Power BI Desktop en utilisant le Microsoft Store, essayez le programme d’installation autonome pouvant être téléchargé à l’adresse [https://aka.ms/pbiSingleInstaller](https://aka.ms/pbiSingleInstaller).

3. Si vous avez correctement installé Power BI Desktop, vous pouvez passer directement à la [Tâche n°2](#task-2-prepare-data). Dans le cas contraire, passez à l’étape suivante.

    > Si vous ne disposez pas des autorisations requises pour installer des applications de bureau ou si vous rencontrez des difficultés lors de l’exécution ou de la configuration de Power BI Desktop, procédez comme suit.

4. Téléchargez [visites.pbix](../../Allfiles/visits.pbix) et enregistrez sur votre ordinateur.

5. Accédez à [https://app.powerbi.com/](https://app.powerbi.com/) et cliquez sur **Se connecter**. 

6. Cliquez sur **Mon espace de travail**. 

7. Si la page **Obtenir les données** s’affiche, cliquez sur **Ignorer**. 

8. Développez **+Nouveau** et sélectionnez **Charger un fichier**.

    > [!IMPORTANT]
    > Si vous ne voyez pas **+Nouveau**, vous devrez peut-être activer la nouvelle version de Power BI. Assurez-vous que la **Nouvelle apparence** soit définie sur **Activée** en haut de votre écran.

9. Sélectionnez **Fichier local**.

10. Localisez et sélectionnez le fichier **visits.pbix** que vous avez téléchargé précédemment.

11. Une fois le chargement des données terminé, sélectionnez le rapport **visites** (notez que le Type est défini sur **Rapport**).

12. Cliquez sur **Modifier**. Si l’élément de menu**Modifier** n’est pas visible cliquez sur **...**, puis sélectionnez **Modifier**.

13. Vous avez terminé la configuration du service Power BI que vous utiliserez pour vos labos. Passez à la [Tâche n°3](#task-3-create-chart-and-time-visualizations), puis, durant toute la durée du labo, utilisez le service Power BI en ligne à l’adresse [https://app.powerbi.com](https://app.powerbi.com) au lieu de Power BI Desktop.

## Tâche \n°2 : Préparez les données

1.  Découvrez l’URL de votre organisation

    * Sous un nouvel onglet, accédez au Centre d’administration Power Platform à l’adresse <https://admin.powerplatform.com>
    
    * Dans le volet de navigation de gauche, sélectionnez Environnements, puis ouvrez votre environnement d’entraînement.
    
    * Faites un clic droit sur l’**URL de l’environnement** sur le panneau **Détails**, puis sélectionnez **Copier le lien**.
    
2. Ouvrez Power BI Desktop. Puis, si vous y êtes invité, connectez-vous avec vos informations d’identification.

3. Sélectionnez **Obtenir les données**.

4. Sélectionnez **Power Platform** sur la gauche, puis **Common Data Service** et appuyez sur **Connecter**.

5. Collez l’URL d’environnement que vous avez copiée précédemment dans le champ **URL du serveur** et cliquez sur **OK**.

6. Développez le nœud **Entités**, sélectionnez les entités **bc_Building** et **bc_Visit** et cliquez sur **Charger**.

7. Cliquez sur l’icône **Modèle** dans la barre d’outils verticale de gauche.

8. Faites glisser la colonne **bc_buildingid** du tableau **bc_Building** et déposez-la sur la colonne **bc_building** dans le tableau **bc_Visit**. Cela créera une relation entre les deux entités que Power BI pourra utiliser pour afficher les données associées.

9. Sélectionnez l’icône **Rapport** dans la barre d’outils de gauche.

10. Développez le nœud **bc_Visit** dans le panneau **Champs**.

11. Cliquez sur **...** en regard de **bc_Visit** et sélectionnez **Nouvelle colonne**.

12. Complétez la formule comme suit :

    ```
    Column = RELATED(bc_Building[bc_name])
    ```

    Appuyez ensuite sur Entrée. Cela ajoutera un nouveau champ avec le nom du bâtiment dans les données de visites.

13. Cliquez sur **...** en regard du champ **Colonne** que vous venez de créer et sélectionnez **Renommer**. Saisissez **Bâtiment** comme nom de champ.

14. Cliquez sur **...** en regard du champ **bc_visitid** et sélectionnez **Renommer**. Saisissez **Visite** comme nom de champ.

15. Cliquez sur  **...** en regard du champ **bc_scheduledstart** et sélectionnez **Renommer**. Entrez **Démarrer** comme nom de champ.

16. Enregistrez le travail en cours en appuyant sur **Fichier \| Enregistrez** en saisissant le nom de fichier de votre choix.

## Tâche n°3 : Créer un graphique et des visualisations temporelles

1. Appuyez sur l’icône de graphique en secteurs dans le panneau **Visualisations** pour insérer un graphique.

2. Faites glisser le champ **Bâtiment** et déposez-le dans la zone **Légende**.

3. Faites glisser le champ **Visite** et déposez-le dans la zone cible **Valeurs**.

4. Redimensionnez le graphique en secteurs à l’aide des poignées d’angle afin que tous les composants du graphique soient visibles.

5. Cliquez sur le rapport en dehors du graphique en secteurs pour le désélectionner et sélectionnez l’histogramme empilé dans le panneau **Visualisations**. 

6. Faites glisser le champ **Visite** et déposez-le dans la zone cible **Valeurs**.

7. Faites glisser le champ **Début** et déposez-le dans la zone cible **Axe**.

8. Dans le panneau Visualisations, cliquez sur **X** en regard des champs **Jour** et **Trimestre** pour ne laisser que les totaux **Année** et **Mois**pour l’Axe.

9. Redimensionnez le graphique selon les besoins, à l’aide des poignées d’angle.

10. Testez l’interactivité du rapport :

    * Sélectionnez différents secteurs sur le graphique en secteurs et observez les changements sur le rapport de temps.
    
    * Cliquez sur l’histogramme. Appuyez sur la flèche vers le bas pour activer le mode **Descendre dans la hiérarchie**, puis appuyez sur la colonne pour descendre au niveau suivant (mois). Vous pouvez également cliquer sur **Données/Descendre \| Développer le niveau suivant** sur le ruban.
    
    * Explorez en remontant ou en descendant d’un niveau et sélectionnez diverses barres sur l’histogramme du temps pour observer les changements sur le graphique en secteurs.
    
11. Enregistrez le travail en cours en appuyant sur **Fichier \| Enregistrez**.

# Exercice n°2 : Créer un tableau de bord Power BI

## Tâche 1 : Publier un rapport Power BI

1. Appuyez sur le bouton **Publier** sous l’onglet Accueil du ruban.

2. Sélectionnez **Mon espace de travail** comme destination, puis appuyez sur **Sélectionner**.

3. Attendez la fin de la publication et cliquez sur **Ouvrez \<nom de votre rapport \>.pbix dans Power BI**.

## Tâche 2 : Créer un tableau de bord Power BI

1. Vous pouvez accéder au rapport ouvert depuis la tâche précédente.

2. Sélectionnez **Épingler à un tableau de bord** dans le menu. Selon la disposition, vous devrez peut-être appuyer sur **...** pour afficher des éléments de menu supplémentaires.

3. Sélectionnez **Nouveau tableau de bord** sur l’invite **Épingler au tableau de bord**.

4. Entrez ***Votre nom* Gestion du campus** comme **Nom du tableau de bord** puis appuyez sur **Épingler en direct**.

5. Sélectionnez **Mon espace de travail** dans la partie supérieure, puis le tableau de bord ***Votre nom* Gestion du campus**.

6. Testez l’interactivité des graphiques en secteurs et à barres affichés.

## Tâche n°3 : Ajouter des visualisations à l’aide du langage naturel

1. Au sein de votre tableau de bord **Gestion du campus**, sélectionnez la barre **Poser une question sur vos données**.

2. Entrez **bâtiments par nombre de visites** dans la zone Questions et réponses. Le graphique à barres s’affiche.

3. Sélectionnez **Épingler un élément visuel**.

4. Sélectionnez **Tableau de bord existant**, puis votre tableau de bord ***Votre nom* Gestion du campus** et appuyez sur **Épingler**.

5. Cliquez sur **Quitter les Q/R**.

Votre tableau de bord ***Votre nom de famille* Gestion du campus** doit être affiché. Vous devrez peut-être faire défiler vers le bas pour voir le nouveau visuel de questions et réponses. 

Votre tableau de bord doit ressembler à ce qui suit :

![Tableau de bord Power BI](media/5-powerbi-result.png)

## Tâche 4 : Créer une vue de téléphone mobile et partager un rapport avec un code QR

1. Dans le tableau de bord, sélectionnez **Modifier \| Vue mobile**.

2. Réorganisez les vignettes comme vous le souhaitez.

3. Cliquez sur **Vue téléphone** en haut à droite et remplacez la vue par **Affichage web**.

4. Sélectionnez **Mon espace de travail** en haut puis sélectionnez votre **Rapport**.

5. Sélectionnez **Modifier** puis sélectionnez **... \| Générer un code QR**.

6. *Facultatif :* Si vous avez un appareil mobile, scannez le code à l’aide d’une application de scan QR disponible sur les plates-formes iOS et Android, ou l’application caméra si votre téléphone le permet. Connectez-vous à votre compte si vous y êtes invité. Parcourez et découvrez le rapport sur un appareil mobile.

# Défis

* Les tableaux de bord et les rapports comprendront bientôt les plans de votre campus et de vos bâtiments
* Signaler et analyser les schémas et tendances des visites
* Visualisation des visites qui ont duré trop longtemps
* Diffuser Power BI en continu pour le traitement en temps quasi réel d’un grand campus 
