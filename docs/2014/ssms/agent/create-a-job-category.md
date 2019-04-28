---
title: Créer une catégorie de travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
ms.assetid: e24a6d38-d231-4f64-ab89-2d1ef6f5792c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d904f82c793acf6135f600e1ed5392bda96e1bb8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856124"
---
# <a name="create-a-job-category"></a>Créer une catégorie de travaux
  Cette rubrique explique comment créer une catégorie de travaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Objects.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent contient des catégories de travail intégrées auxquelles vous pouvez affecter des travaux. Vous pouvez également créer une catégorie de travail et lui affecter les travaux. Les catégories de travaux permettent d'organiser les travaux afin d'en faciliter le filtrage et le regroupement. Par exemple, vous pouvez organiser tous vos travaux de sauvegarde de base de données dans la catégorie Maintenance de bases de données. Vous pouvez également créer vos propres catégories de travaux.  
  
 
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
 Les catégories multiserveurs n'existent que sur un serveur maître. Il n’y a qu’une seule catégorie de travaux par défaut disponible sur un serveur maître : [**N’appartenant à aucune catégorie (Multiserveurs)**]. Lors du téléchargement d'un travail multiserveur, sa catégorie passe à **Travaux de MSX** sur le serveur cible.  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  

  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-a-job-category"></a>Pour créer une catégorie de travail  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez créer une catégorie de travaux.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Travaux** et sélectionnez **Gérer les catégories de travaux**.  
  
4.  Dans la boîte de dialogue **Gérer les catégories de travaux**_nom_serveur_ , cliquez sur **Ajouter**.  
  
5.  Dans la nouvelle boîte de dialogue, dans la zone **Nom** , entrez un nom pour la nouvelle catégorie de travaux.  
  
6.  Sélectionnez la case à cocher **Afficher tous les travaux** . Sélectionnez un ou plusieurs travaux pour la nouvelle catégorie en activant les cases à cocher correspondant aux travaux.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans la boîte de dialogue **Gérer les catégories de travaux**_nom_serveur_ , cliquez sur **Actualiser** pour vous assurer que la nouvelle catégorie de travaux est active. Si tout se présente comme prévu, fermez cette boîte de dialogue.  
  
 Pour plus d’informations sur ces boîtes de dialogue, consultez [les catégories de travaux : Gérer les catégories de travaux](job-categories-manage-job-categories.md) et [nouvelle catégorie de travaux et les propriétés des catégories de travail](job-categories-properties-new-job-category.md).  
  
 
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-create-a-job-category"></a>Pour créer une catégorie de travail  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
 Pour plus d’informations, consultez [sp_add_category &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-category-transact-sql).  
  

  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 **Pour créer une catégorie de travail**  
  
 Appelez la classe `JobCategory` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell. Pour obtenir un exemple de code, consultez [Planification des tâches administratives automatiques dans l’Agent SQL Server](sql-server-agent.md).  
  
 
  
  
