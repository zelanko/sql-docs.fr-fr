---
title: Affecter un travail à une catégorie de travaux | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], assigning
- SQL Server Agent jobs, categories
- jobs [SQL Server Agent], categories
- categories [SQL Server Agent jobs]
- SQL Server Agent jobs, assigning
- assigning job to category
ms.assetid: a9ea65a2-1d73-4582-a335-63adeb450cb6
caps.latest.revision: 28
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 75be4bb829cfae6bafecc76591f03db805438014
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045281"
---
# <a name="assign-a-job-to-a-job-category"></a>Affecter un travail à une catégorie de travaux
  Cette rubrique décrit comment affecter des travaux de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent aux catégories de travaux dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou de SQL Server Management Objects.  
  
 Les catégories de travaux permettent d'organiser les travaux afin d'en faciliter le filtrage et le regroupement. Par exemple, vous pouvez organiser tous vos travaux de sauvegarde de base de données dans la catégorie Maintenance de bases de données. Vous pouvez affecter des travaux à des catégories de travaux intégrées, ou vous pouvez créer une catégorie de travaux définie par l’utilisateur, à laquelle vous affectez ensuite des travaux.  
  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Pour affecter un travail à une catégorie de travaux  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus pour développer le serveur sur lequel vous souhaitez affecter un travail à une catégorie de travaux.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Travaux** .  
  
4.  Cliquez avec le bouton droit sur le travail à modifier, puis sélectionnez **Propriétés**.  
  
5.  Dans la boîte de dialogue **Propriétés du travail -***nom_travail*, dans la liste **Catégorie**, sélectionnez la catégorie de travaux que vous voulez affecter au travail.  
  
6.  Cliquez sur **OK**.  
  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-assign-a-job-to-a-job-category"></a>Pour affecter un travail à une catégorie de travaux  
  
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
 **Pour affecter un travail à une catégorie de travaux**  
  
 Utilisez la `JobCategory` classe à l’aide d’un langage de programmation que vous choisissez, tel que Visual Basic, Visual c# ou PowerShell.  
  
  
  
  
