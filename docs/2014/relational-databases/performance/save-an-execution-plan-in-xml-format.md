---
title: Enregistrer un plan d’exécution au format XML | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- XML query plans [SQL Server]
- opening execution plans
- XML Showplans [SQL Server]
- execution plans [SQL Server], saving
- saving execution plans
ms.assetid: c439e53b-56f3-4442-97c6-dabd48a203d8
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b2e058eba4e21e5e9060e2315dad3c865c46bb78
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63150862"
---
# <a name="save-an-execution-plan-in-xml-format"></a>Enregistrer un plan d'exécution au format XML
  Utilisez [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour enregistrer un plan d'exécution en tant que fichier XML, puis pour l'ouvrir et le consulter.  
  
 Pour utiliser la fonctionnalité de plan d'exécution de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], ou les options SET de Showplan XML, les utilisateurs doivent disposer des autorisations appropriées pour exécuter la requête [!INCLUDE[tsql](../../includes/tsql-md.md)] pour laquelle un plan d'exécution est généré et doivent obtenir l'autorisation SHOWPLAN pour toutes les bases de données référencées par la requête.  
  
### <a name="to-save-a-query-plan-by-using-the-xml-showplan-set-options"></a>Pour enregistrer un plan de requête avec les options SET de Showplan XML  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , ouvrez un éditeur de requête et connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Activez SHOWPLAN_XML avec l'instruction suivante :  
  
    ```  
    SET SHOWPLAN_XML ON;  
    GO  
    ```  
  
     Pour activer STATISTICS XML, utilisez l'instruction suivante :  
  
    ```  
    SET STATISTICS XML ON;  
    GO  
    ```  
  
     SHOWPLAN_XML génère des informations de plan d'exécution de requête de compilation pour une requête, mais sans exécuter cette dernière. STATISTICS XML génère des informations de plan d'exécution de requête à l'exécution pour une requête et exécute cette dernière.  
  
3.  Exécuter une requête. Exemple :  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    SET SHOWPLAN_XML ON;  
    GO  
    -- Execute a query.  
    SELECT BusinessEntityID   
    FROM HumanResources.Employee  
    WHERE NationalIDNumber = '509647174';  
    GO  
    SET SHOWPLAN_XML OFF;  
    ```  
  
4.  Dans le volet **Résultats** , cliquez avec le bouton droit sur le **Plan d’exécution XML Microsoft SQL Server** contenant le plan de requête, puis cliquez sur **Enregistrer les résultats sous**.  
  
5.  Dans la boîte de dialogue **Enregistrer** \<les résultats **de la grille ou du texte>**, dans la zone **Type de fichier**, cliquez sur **Tous les fichiers (\*.\*)**.  
  
6.  Dans la boîte de dialogue **Nom de fichier**, fournissez un nom au format \<nom **>.sqlplan**, puis cliquez sur **Enregistrer**.  
  
### <a name="to-save-an-execution-plan-by-using-sql-server-management-studio-options"></a>Pour enregistrer un plan d'exécution avec les options de SQL Server Management Studio  
  
1.  Générez un plan d'exécution soit estimé soit réel au moyen de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Pour plus d’informations, consultez [Affichage du plan d’exécution estimé](display-the-estimated-execution-plan.md) ou [Afficher un plan d’exécution réel](display-an-actual-execution-plan.md).  
  
2.  Sous l’onglet **Plan d’exécution** du volet de résultats, cliquez avec le bouton droit sur le plan d’exécution graphique, puis choisissez **Enregistrer le plan d’exécution en tant que**.  
  
     Vous pouvez aussi choisir **Enregistrer le plan d’exécution en tant que** dans le menu **Fichier** .  
  
3.  Dans la boîte de dialogue **Enregistrer sous**, assurez-vous que **Type de fichier** est défini à **Fichiers de plan d’exécution (\*.sqlplan)**.  
  
4.  Dans la boîte de dialogue **Nom de fichier**, fournissez un nom au format \<nom **>.sqlplan**, puis cliquez sur **Enregistrer**.  
  
### <a name="to-open-a-saved-xml-query-plan-in-sql-server-management-studio"></a>Pour ouvrir un plan de requête XML dans SQL Server Management Studio  
  
1.  Dans le menu [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Fichier **de** , choisissez **Ouvrir**, puis cliquez sur **Fichier**.  
  
2.  Dans la boîte de dialogue **Ouvrir un fichier**, définissez **Types de fichiers** à **Fichiers de plan d’exécution (\*.sqlplan)** pour produire une liste filtrée des fichiers de plan de requête XML enregistrés.  
  
3.  Sélectionnez le fichier de plan de requête XML que vous voulez consulter, puis cliquez sur **Ouvrir**.  
  
     En guise d’alternative, dans l’Explorateur Windows, double-cliquez sur un fichier avec l’extension **.sqlplan**. Le plan s'ouvre dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [SET SHOWPLAN_XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-showplan-xml-transact-sql)   
 [SET STATISTICs XML &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statistics-xml-transact-sql)  
  
  
