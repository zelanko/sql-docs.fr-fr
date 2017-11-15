---
title: "Créer une catégorie de travaux | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
caps.latest.revision: "5"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 154d801187b23d5c9d3574078eaa9e2ce11ed128
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="create-a-job-category"></a>Créer une catégorie de travaux
Cette rubrique explique comment créer une catégorie de travaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], de [!INCLUDE[tsql](../../includes/tsql_md.md)] ou de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Management Objects.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent contient des catégories de travail intégrées auxquelles vous pouvez affecter des travaux. Vous pouvez également créer une catégorie de travail et lui affecter les travaux. Les catégories de travaux permettent d'organiser les travaux afin d'en faciliter le filtrage et le regroupement. Par exemple, vous pouvez organiser tous vos travaux de sauvegarde de base de données dans la catégorie Maintenance de bases de données. Vous pouvez également créer vos propres catégories de travaux.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour créer une catégorie de travaux, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
Les catégories multiserveurs n'existent que sur un serveur maître. Il n’y a qu’une seule catégorie de travaux par défaut disponible sur un serveur maître : [**N’appartenant à aucune catégorie (Multiserveurs)**]. Lors du téléchargement d'un travail multiserveur, sa catégorie passe à **Travaux de MSX** sur le serveur cible.  
  
### <a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-job-category"></a>Pour créer une catégorie de travail  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez créer une catégorie de travaux.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Travaux** et sélectionnez **Gérer les catégories de travaux**.  
  
4.  Dans la boîte de dialogue **Gérer les catégories de travaux***nom_serveur* , cliquez sur **Ajouter**.  
  
5.  Dans la nouvelle boîte de dialogue, dans la zone **Nom** , entrez un nom pour la nouvelle catégorie de travaux.  
  
6.  Sélectionnez la case à cocher **Afficher tous les travaux** . Sélectionnez un ou plusieurs travaux pour la nouvelle catégorie en activant les cases à cocher correspondant aux travaux.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue **Gérer les catégories de travaux***nom_serveur* , cliquez sur **Actualiser** pour vous assurer que la nouvelle catégorie de travaux est active. Si tout se présente comme prévu, fermez cette boîte de dialogue.  
  
Pour plus d’informations sur ces boîtes de dialogue, consultez [Catégories de travaux - Gérer les catégories de travaux](../../ssms/agent/job-categories-manage-job-categories.md) et [Propriétés des catégories de travaux - Nouvelle catégorie de travaux](../../ssms/agent/job-categories-properties-new-job-category.md).  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-create-a-job-category"></a>Pour créer une catégorie de travail  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- creates a local job category named AdminJobs   
    USE msdb ;  
    GO  
    EXEC dbo.sp_add_category  
        @class=N'JOB',  
        @type=N'LOCAL',  
        @name=N'AdminJobs' ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_add_category (Transact-SQL)](http://msdn.microsoft.com/en-us/6cca32cd-d941-4378-aed6-a7c90cb7520a).  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour créer une catégorie de travail**  
  
Utilisez la classe **JobCategory** à l’aide du langage de programmation de votre choix, tel que Visual Basic, Visual C# ou PowerShell. Pour obtenir un exemple de code, consultez [Planification des tâches administratives automatiques dans l’Agent SQL Server](http://msdn.microsoft.com/en-us/900242ad-d6a2-48e9-8a1b-f0eea4413c16).  
  
