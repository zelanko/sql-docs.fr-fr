---
title: Répertorier les informations de catégorie de travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 0fc668d4-6244-4fef-b90e-62d2c776cd7c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dae8f1d98fb1758e9a9802883def1574bda68a78
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798205"
---
# <a name="list-job-category-information"></a>Répertorier les informations de catégorie de travaux
  Comment répertorier les informations de catégorie de travaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou SQL Server Management Objects.  

  
##  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  

  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-list-job-category-information"></a>Pour répertorier les informations de catégorie de travaux  
  
1.  Dans l'**Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```sql
    -- returns information about jobs that are administered locally  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_category  
        @type = N'LOCAL' ;  
    GO  
    ```  
  
 Pour plus d’informations, [consultez &#40;SP_HELP_CATEGORY Transact-&#41;SQL](/sql/relational-databases/system-stored-procedures/sp-help-category-transact-sql).  
  
  
##  <a name="SMO"></a>Utilisation de SQL Server Management Objects  
 **Pour répertorier les informations de catégorie de travaux**  
  
 Utilisez la classe `JobCategory` dans le langage de programmation de votre choix, par exemple Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, [consultez &#40;SQL Server Management Objects&#41; le Guide de programmation Smo](../../relational-databases/server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md).  
