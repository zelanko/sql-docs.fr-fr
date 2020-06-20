---
title: Créer des modèles personnalisés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- tql
- templates [Transact-SQL], creating
- templates [Transact-SQL]
ms.assetid: 41098e78-b482-410e-bfe8-2ac10769ac4a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d44d8d8bdda5f8c15fffe8f3aaf0eaf2d099e81
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85040888"
---
# <a name="create-custom-templates"></a>Créer des modèles personnalisés
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est fourni avec des modèles pour de nombreuses tâches communes, mais le réel intérêt des modèles réside dans la possibilité de créer un modèle personnalisé pour les scripts complexes qui doivent être créés souvent. Au cours de cet exercice pratique, vous allez créer un script simple avec quelques paramètres, mais les modèles peuvent être utiles également pour les scripts longs et répétitifs.  
  
## <a name="using-custom-templates"></a>Utilisation de modèles personnalisés  
  
#### <a name="to-create-a-custom-template"></a>Pour créer un modèle personnalisé  
  
1.  Dans l’Explorateur de modèles, développez **Modèles SQL Server**, cliquez avec le bouton droit sur **Procédure stockée**, pointez sur **Nouveau**et cliquez sur **Dossier**.  
  
2.  Tapez **Personnalisé** comme nom de dossier de modèles et appuyez sur Entrée.  
  
3.  Cliquez avec le bouton droit sur **Personnalisé**, pointez sur **Nouveau**et cliquez sur **Modèle**.  
  
4.  Tapez **ProcBonTravail** comme nom de votre nouveau modèle et appuyez sur **Entrée**.  
  
5.  Cliquez avec le bouton droit sur **ProcBonTravail**, puis cliquez sur **Modifier**.  
  
6.  Dans la boîte de dialogue **Se connecter au moteur de base de données** , vérifiez les informations de connexion, puis cliquez sur **Se connecter**.  
  
7.  Dans l'Éditeur de requête, tapez le script suivant pour créer une procédure stockée qui recherche les bons d'une pièce en particulier, dans le cas présent : blade (la lame en français). (Vous pouvez copier et coller le code à partir de la fenêtre du didacticiel.)  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersForBlade')  
       DROP PROCEDURE dbo.WorkOrdersForBlade;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersForBlade  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = 'Blade';  
    GO  
    ```  
  
8.  Appuyez sur F5 pour exécuter ce script et créer la procédure **WorkOrdersForBlade** .  
  
9. Dans l’Explorateur d’objets, cliquez avec le bouton droit sur votre serveur et choisissez **Nouvelle requête**. Une nouvelle fenêtre de l'Éditeur de requête s'ouvre.  
  
10. Dans l’Éditeur de requête, tapez **EXECUTE dbo.WorkOrdersForBlade**et appuyez sur F5 pour exécuter la requête. Vérifiez si le volet **Résultats** affiche la liste des bons de travaux pour les lames.  
  
11. Modifiez le script du modèle (le script de l’étape 7) en remplaçant le nom du produit Blade par le paramètre <strong> *<* product_name</strong>, `nvarchar(50)` , <strong> *>* Name</strong>, à quatre endroits.  
  
    > [!NOTE]  
    >  Les paramètres nécessitent trois éléments : le nom du paramètre à remplacer, le type de données du paramètre et une valeur par défaut pour le paramètre.  
  
12. Le script doit à présent ressembler à ce qui suit :  
  
    ```  
    USE AdventureWorks20012;  
    GO  
    IF EXISTS (  
    SELECT *   
       FROM INFORMATION_SCHEMA.ROUTINES   
       WHERE SPECIFIC_NAME = 'WorkOrdersFor<product_name, nvarchar(50), name>')  
       DROP PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>;  
    GO  
    CREATE PROCEDURE dbo.WorkOrdersFor<product_name, nvarchar(50), name>  
    AS  
    SELECT Name, WorkOrderID   
    FROM Production.WorkOrder AS WO  
    JOIN Production.Product AS Prod  
    ON WO.ProductID = Prod.ProductID  
    WHERE Name = '<product_name, nvarchar(50), name>';  
    GO  
    ```  
  
13. Dans le menu **Fichier** , cliquez sur **Save WorkOrdersProc.sql** (Enregistrer ProcBonTravail.sql) pour enregistrer votre modèle.  
  
#### <a name="to-test-the-custom-template"></a>Pour tester le modèle personnalisé  
  
1.  Dans l’Explorateur de modèles, développez **Procédure stockée**puis **Personnalisé**et double-cliquez sur **ProcBonTravail**.  
  
2.  Dans la boîte de dialogue **Se connecter au moteur de base de données** , fournissez les informations de connexion, puis cliquez sur **Se connecter**. Une nouvelle fenêtre de l’Éditeur de requête s’affiche avec le modèle **ProcBonTravail** .  
  
3.  Dans le menu **Requête** , cliquez sur **Spécifier les valeurs des paramètres du modèle**.  
  
4.  Dans la boîte de dialogue **remplacer les paramètres de modèle** , pour la `product_name` valeur, tapez **freewheel** (en remplaçant le contenu par défaut), puis cliquez sur **OK** pour fermer la boîte de dialogue remplacer les **paramètres de modèle** et modifier le script dans l’éditeur de requête.  
  
5.  Appuyez sur F5 pour exécuter la requête et créer la procédure.  
  
## <a name="next-task-in-lesson"></a>Tâche suivante de la leçon  
 [Enregistrer des scripts sous forme de projets ou de solutions](lesson-3-3-save-scripts-as-projects-or-solutions.md)  
  
  
