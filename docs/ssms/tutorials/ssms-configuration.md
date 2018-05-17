---
Title: 'Tutorial: SQL Server Management Studio Components and Configuration'
description: Tutoriel décrivant les composants et les options de configuration de base pour votre environnement SQL Server Management Studio.
keywords: SQL Server, SSMS, SQL Server Management Studio
author: MashaMSFT
ms.author: mathoma
ms.date: 03/16/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod: sql
ms.technology: ssms
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
ms.openlocfilehash: 51fb197c3b5177c699134a48fc4888cd134e1711
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="tutorial-sql-server-management-studio-components-and-configuration"></a>Tutoriel : Composants et configuration de SQL Server Management Studio
Ce tutoriel décrit les différents composants de fenêtres dans SSMS (SQL Server Management Studio) et certaines options de configuration de base pour votre espace de travail. Dans cet article, vous allez approfondir les sujets suivants : 

> [!div class="checklist"]
> * Différents composants qui constituent l’environnement SSMS
> * Modification de la disposition de l’environnement et réinitialisation des valeurs par défaut
> * Agrandissement de l’éditeur de requête
> * Modification de la police 
> * Configuration des options de démarrage 
> * Réinitialisation de la configuration par défaut 

## <a name="prerequisites"></a>Conditions préalables requises
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio.  

- Installez [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms).

## <a name="sql-server-management-studio-components"></a>Composants de SQL Server Management Studio
Cette section couvre les différents composants de fenêtres disponibles dans l’espace de travail et leur fonction. 

- Chaque composant de fenêtre peut être fermé en cliquant sur le X dans l’angle de la barre de titre, puis rouvert à partir de la liste déroulante **Affichage** dans le menu principal. 

    ![Menu Afficher](media/ssms-configuration/viewmenu.png)

- **Explorateur d’objets** (F8) : l’Explorateur d’objets est une arborescence qui présente tous les objets de base de données sur un serveur. Cela peut inclure les bases de données du moteur de base de données SQL Server, Analysis Services, Reporting Services et Integration Services. L'Explorateur d'objets contient des informations sur tous les serveurs auxquels il est connecté. 
    
    ![Explorateur d’objets](media/ssms-configuration/objectexplorer.png)
- **Fenêtre de requête** (Ctrl+N) : une fois que vous avez cliqué sur **Nouvelle requête**, il s’agit de la fenêtre dans laquelle vous tapez vos requêtes T-SQL (Transact-SQL). Les résultats de vos requêtes sont visibles ici également.
    
    ![Fenêtre de nouvelle requête](media/ssms-configuration/newquery.png)

- **Propriétés** (F4) : cette option est visible une fois que la **fenêtre de requête** s’ouvre et affiche les propriétés de base de la requête. Par exemple, elle affiche l’heure de début d’une requête, le nombre de lignes retournées et les détails de la connexion.  

    ![Propriétés](media/ssms-configuration/properties.png)

- **Explorateur de modèles** (Ctrl+Alt+T) : il existe plusieurs modèles T-SQL prédéfinis qui figurent dans l’Explorateur de modèles. Ces modèles vous permettent d’effectuer diverses tâches telles que la création ou la sauvegarde d’une base de données. 

    ![Explorateur de modèles](media/ssms-configuration/templates.png)

- **Détails de l’Explorateur d’objets**(F7) : il s’agit d’un affichage plus détaillé des éléments visibles dans l’Explorateur d’objets qui vous permet de manipuler plusieurs objets à la fois. Par exemple, la fenêtre Détails de l’Explorateur d’objets vous permet de sélectionner simultanément plusieurs bases de données et de les supprimer ou de générer des scripts pour elles. 

    ![Détails de l’Explorateur d’objets](media/ssms-configuration/objectexplorerdetails.PNG) 
 

    

## <a name="change-the-environmental-layout"></a>Modifier la disposition de l’environnement 
Cette section décrit la manipulation de la disposition de l’environnement, comme le déplacement des différentes fenêtres. 

-  Chaque composant de fenêtre peut être déplacé en maintenant le titre enfoncé et en faisant glisser la fenêtre. 
- Chaque composant de fenêtre peut être épinglé et désépinglé en sélectionnant l’icône de punaise dans la barre de titre :
    
    ![Épinglage d’objets](media/ssms-configuration/pushpin.png)

- Chaque composant de fenêtre a une flèche de déroulement qui permet de manipuler la fenêtre de différentes manières : 

    ![Options de fenêtres](media/ssms-configuration/windowoptions.png)

- Une fois qu’au moins deux fenêtres de requête sont ouvertes, elles peuvent se présenter comme des onglets verticaux ou horizontaux, afin que les deux fenêtres de requête soient visibles à la fois. Pour ce faire, cliquez avec le bouton droit sur le titre de la requête, puis sélectionnez l’option à onglets souhaitée. 
 
    ![Options des onglets de requête](media/ssms-configuration/querytabbedoptions.png)

    - Il s’agit du **groupe d’onglets horizontal** : ![Groupe d’onglets horizontal](media/ssms-configuration/horizontaltab.png)     
    
    - Il s’agit du **groupe d’onglets vertical** :  
        ![Groupe d’onglets vertical](media/ssms-configuration/verticaltabgroup.png)
        

    - Pour refusionner les onglets, cliquez à nouveau avec le bouton droit sur le titre de la requête, puis sélectionnez **Déplacer vers le groupe d’onglets suivant** ou **Déplacer vers le groupe d’onglets précédent** :
    
        ![Fusionner les onglets de requête](media/ssms-configuration/mergetabgroups.png)

- Pour restaurer la disposition de l’environnement par défaut, cliquez sur le **Menu Fenêtre** > **Rétablir la disposition de fenêtre** :
 
    ![Restaurer la disposition de fenêtre](media/ssms-configuration/resetwindowlayout.png)
    
## <a name="maximize-query-editor"></a>Agrandir l'Éditeur de requête
L’éditeur de requête peut être agrandi en mode plein écran.

1. Cliquez n’importe où dans la fenêtre de l’éditeur de requête.
2. Appuyez sur Maj+Alt+Entrée pour basculer du mode plein écran au mode normal. 

Ce raccourci clavier fonctionne dans toute fenêtre de document. 



## <a name="change-basic-settings"></a>Changer les paramètres de base
Cette section explique comment modifier certains paramètres de base dans SSMS. Ces options se trouvent dans le menu **Outils** :

  ![Menu Outils](media/ssms-configuration/tools.png)


- La barre d’outils mise en surbrillance peut être modifiée en accédant au menu : **Outils** > **Personnaliser** :

    ![Personnaliser la barre d’outils](media/ssms-configuration/toolbar.png)

### <a name="change-the-font"></a>Changer la police
- La police peut être modifiée à partir du menu : **Outils** > **Options** > **Polices et couleurs** :

     ![Polices et couleurs](media/ssms-configuration/fontsandcolors.png)

### <a name="change-the-startup-options"></a>Changer les options de démarrage
- Les options de démarrage déterminent l’aspect de votre espace de travail lors du premier lancement de SSMS. Elles peuvent être configurées dans le menu : **Outils** > **Options** > **Démarrage** :
 
    ![Options de démarrage](media/ssms-configuration/startup.png)

### <a name="reset-settings-to-default"></a>Rétablir les valeurs par défaut des paramètres
- Tous ces paramètres peuvent être exportés et importés dans le menu : **Outils** > **Importation et exportation de paramètres** 

    ![Importation et exportation de paramètres](media/ssms-configuration/settings.png)
    - Il s’agit également de l’emplacement où vous pouvez réinitialiser tous les paramètres par défaut. 


## <a name="next-steps"></a>Étapes suivantes
L’article suivant vous donne quelques conseils et astuces supplémentaires pour utiliser SSMS, par exemple comment rechercher votre journal des erreurs SQL Server et le nom de votre instance SQL. 

Passez à l’article suivant pour en savoir plus
> [!div class="nextstepaction"]
> [Bouton Étapes suivantes](ssms-tricks.md)
 
 




