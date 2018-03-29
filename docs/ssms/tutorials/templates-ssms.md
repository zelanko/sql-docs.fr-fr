---
Title: 'Tutorial: Using Templates in SQL Server Management Studio'
description: Tutoriel pour l’utilisation de modèles dans SSMS. .
keywords: SQL Server, SSMS, SQL Server Management Studio, modèles
author: MashaMSFT
ms.author: mathoma
ms.date: 03/13/2018
ms.topic: Tutorial
ms.suite: sql
ms.prod_service: sql-tools
ms.reviewer: sstein
manager: craigg
helpviewer_keywords:
- templates [SQL Server], SQL Server Management Studio
- source controls [SQL Server Management Studio], tutorials
- Help [SQL Server], SQL Server Management Studio
- tutorials [SQL Server Management Studio]
- Transact-SQL tutorials
- SQL Server Management Studio [SQL Server], tutorials
- scripts [SQL Server], SQL Server Management Studio
ms.openlocfilehash: a01586f4ab3d002e33b7679f6fe2e5a165f260e1
ms.sourcegitcommit: ccb05cb5a4cccaf7ffa9e85a4684fa583bab914e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2018
---
# <a name="tutorial-using-templates-within-sql-server-management-studio"></a>Tutoriel : Utilisation de modèles dans SQL Server Management Studio
Ce tutoriel vous présente les modèles T-SQL (Transact-SQL) prédéfinis qui sont disponibles dans SSMS (SQL Server Management Studio). Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Utiliser l’Explorateur de modèles pour générer des scripts T-SQL
> * Modifier un modèle existant 
> * Rechercher les modèles sur le disque
> * Créer un modèle
   

## <a name="prerequisites"></a>Prérequis
Pour suivre ce tutoriel, vous avez besoin de SQL Server Management Studio et de l’accès à un serveur SQL Server. 

- Installez [SQL Server Management Studio](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms).
- Installez [SQL Server 2017 Developer Edition](https://www.microsoft.com/en-us/sql-server/sql-server-downloads).

 

## <a name="using-the-template-browser"></a>Utilisation de l’Explorateur de modèles
Dans cette section, vous allez apprendre à localiser et utiliser **l’Explorateur de modèles**. 

1. Démarrez SQL Server Management Studio.
2. Dans le menu **Affichage** > **Explorateur de modèles** (Ctrl+Alt+T) : 

    ![Explorateur de modèles](media/templates-ssms/templatebrowser.png)
    - Vous pouvez également voir les modèles récemment utilisés au bas de **l’Explorateur de modèles**.

3. Développez le nœud qui vous intéresse > cliquez avec le bouton droit sur le modèle > Ouvrir :

    ![Ouvrir le modèle](media/templates-ssms/opentemplate.png)
    - Un double-clic sur le modèle aura le même effet.

4. Cette action lance une fenêtre de nouvelle requête avec le script T-SQL déjà rempli. 
5. Modifiez le modèle pour l’adapter à vos besoins, puis **exécutez** la requête :
    
    ![Créer un modèle de base de données](media/templates-ssms/createdbtemplate.png)


## <a name="edit-an-existing-template"></a>Modifier un modèle existant
Vous pouvez également modifier les modèles existants dans **l’Explorateur de modèles**.  

1. Recherchez le modèle qui vous intéresse dans **l’Explorateur de modèles**.
2. Cliquez avec le bouton droit sur le modèle > **Modifier** :

    ![Modifier le modèle](media/templates-ssms/edittemplate.png)

3. Apportez les modifications souhaitées dans la fenêtre de requête qui s’ouvre.
4. Enregistrez le modèle en accédant à **Fichier** > **Enregistrer** (Ctrl+S).
5. Fermez la fenêtre de requête.
6. Rouvrez le modèle que vous avez enregistré > vos nouvelles modifications doivent y figurer.
 

## <a name="locate-the-templates-on-disk"></a>Rechercher les modèles sur le disque
Une fois qu’un modèle est ouvert, vous pouvez le localiser sur le disque.

1. Sélectionnez un modèle dans **l’Explorateur de modèles** > **Modifier**.
2. Cliquez avec le bouton droit sur le **Titre de la requête** > **Ouvrir le dossier contenant**. Cela doit ouvrir votre explorateur à l’endroit où les modèles sont stockés sur le disque : 

    ![Modèles sur le disque](media/templates-ssms/templatesondisk.png)
  

## <a name="create-a-new-template"></a>Créer un modèle
Dans **l’Explorateur de modèles**, vous avez également la possibilité de créer des modèles. Ces étapes vont vous apprendre à créer un dossier, puis à créer un modèle dans ce dossier. Toutefois, ces étapes vous permettent également de créer un modèle personnalisé dans les dossiers existants. 

1. Ouvrez **l’Explorateur de modèles**.
2. Cliquez avec le bouton droit sur Modèles SQL Server > **Nouveau** > **Dossier**.
3. Nommez ce dossier **Modèles personnalisés** :

    ![Création de modèles personnalisés](media/templates-ssms/creatingcustomtemplate.png)

4. Cliquez avec le bouton droit sur le dossier **Modèles personnalisés** nouvellement créé > **Nouveau** > **Modèle** > nommez votre modèle :
 
    ![Créer un modèle personnalisé](media/templates-ssms/createnewtemplate.png)
   
5. Cliquez avec le bouton droit sur le modèle que vous venez de créer > **Modifier**. Vous ouvrez ainsi une **Fenêtre de nouvelle requête**.
6. Tapez le texte T-SQL que vous souhaitez enregistrer. 
7. Enregistrez le fichier en accédant au menu **Fichier** > **Enregistrer**.
8. Fermez la **fenêtre de requête** existante et ouvrez votre nouveau modèle personnalisé. 

    

## <a name="next-steps"></a>Étapes suivantes
L’article suivant propose des conseils et astuces supplémentaires sur l’utilisation de SQL Server Management Studio. 

Passez à l’article suivant pour en savoir plus
> [!div class="nextstepaction"]
> [Bouton Étapes suivantes](ssms-tricks.md)
