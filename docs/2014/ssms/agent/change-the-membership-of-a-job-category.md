---
title: Modifier l’appartenance d’une catégorie de travaux | Documents Microsoft
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
- members [SQL Server], job categories
ms.assetid: 6a18f7f0-eb50-485f-a9c7-df31ae0f994e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a3e8497e4f5a8b5e74b7bb0b5d9c01cef78e275d
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54131079"
---
# <a name="change-the-membership-of-a-job-category"></a>Modifier l'appartenance d'une catégorie de travaux
  Cette rubrique explique comment modifier l'appartenance de la catégorie de travaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)]ou de SQL Server Management Objects.  
  
 Les catégories de travaux permettent d'organiser les travaux afin d'en faciliter le filtrage et le regroupement. Vous pouvez créer vos propres catégories de travaux. Vous pouvez également modifier l'appartenance aux catégories des travaux de l'Agent Microsoft SQL Server.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour modifier l'appartenance d'une catégorie de travaux, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
     [SQL Server Management Objects](#SMO)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Pour modifier l'appartenance d'une catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez modifier une catégorie de travaux.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Travaux** et sélectionnez **Gérer les catégories de travaux**.  
  
4.  Dans la boîte de dialogue **Gérer les catégories de travaux**_nom_serveur_ , sélectionnez la catégorie de travaux que vous souhaitez modifier, puis cliquez sur **Afficher les travaux**.  
  
5.  Sélectionnez la case à cocher **Afficher tous les travaux** .  
  
6.  Pour ajouter un travail à la catégorie, dans la grille principale, sélectionnez la case à cocher correspondant au travail dans la colonne **Sélectionner** . Pour supprimer un travail de la catégorie, désactivez la case à cocher correspondante. Lorsque vous avez terminé, cliquez sur **OK**.  
  
7.  Fermez la boîte de dialogue **Gérer les catégories de travaux**_nom_serveur_ .  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-change-the-membership-of-a-job-category"></a>Pour modifier l'appartenance d'une catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
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
  
 Pour plus d’informations, consultez [sp_update_job &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-job-transact-sql).  
  
##  <a name="SMO"></a> À l’aide de SQL Server Management Objects  
 **Pour modifier l'appartenance d'une catégorie de travaux**  
  
 Utilisez la classe `JobCategory` à l'aide d'un langage de programmation que vous choisissez, tel que Visual Basic, Visual C# ou PowerShell.  
  
  
