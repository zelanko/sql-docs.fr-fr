---
title: "Répertorier les informations de catégorie de travaux | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f369092eeb9e9ab004d0bd2fb91065af9a9bbfea
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="list-job-category-information"></a>Répertorier les informations de catégorie de travaux
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Cette rubrique explique comment répertorier les informations de catégorie de travaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l’aide de [!INCLUDE[tsql](../../includes/tsql_md.md)] ou SQL Server Management Objects.  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour répertorier les informations de catégorie de travaux, utilisez :**  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>Pour répertorier les informations de catégorie de travaux  
  
1.  Dans l'**Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_help_category (Transact-SQL)](http://msdn.microsoft.com/en-us/8cad1dcc-b43e-43bd-bea0-cb0055c84169).  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour répertorier les informations de catégorie de travaux**  
  
Utilisez la classe **JobCategory** à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell.  
  
