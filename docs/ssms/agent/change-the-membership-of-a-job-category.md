---
title: Modifier l’appartenance d’une catégorie de travaux | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 1e56b8180caf8beec9a0371e79e847fd4ff2e30d
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51701107"
---
# <a name="change-the-membership-of-a-job-category"></a>Modifier l'appartenance d'une catégorie de travaux
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment modifier l'appartenance de la catégorie de travaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de SQL Server Management Objects.  
  
Les catégories de travaux permettent d'organiser les travaux afin d'en faciliter le filtrage et le regroupement. Vous pouvez créer vos propres catégories de travaux. Vous pouvez également modifier l'appartenance aux catégories des travaux de l'Agent Microsoft SQL Server.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour modifier l'appartenance d'une catégorie de travaux, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Pour modifier l'appartenance d'une catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez modifier une catégorie de travaux.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Travaux** et sélectionnez **Gérer les catégories de travaux**.  
  
4.  Dans la boîte de dialogue **Gérer les catégories de travaux***nom_serveur*, sélectionnez la catégorie de travaux que vous souhaitez modifier, puis cliquez sur **Afficher les travaux**.  
  
5.  Sélectionnez la case à cocher **Afficher tous les travaux** .  
  
6.  Pour ajouter un travail à la catégorie, dans la grille principale, sélectionnez la case à cocher correspondant au travail dans la colonne **Sélectionner** . Pour supprimer un travail de la catégorie, désactivez la case à cocher correspondante. Lorsque vous avez terminé, cliquez sur **OK**.  
  
7.  Fermez la boîte de dialogue **Gérer les catégories de travaux***nom_serveur*.  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Pour modifier l'appartenance d'une catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- adding a new job category to the "NightlyBackups" job  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_job  
        @job_name = N'NightlyBackups',  
        @category_name = N'[Uncategorized (Local)]';  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_update_job (Transact-SQL)](https://msdn.microsoft.com/cbdfea38-9e42-47f3-8fc8-5978b82e2623).  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour modifier l'appartenance d'une catégorie de travaux**  
  
Utilisez la classe **JobCategory** à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell.  
  
