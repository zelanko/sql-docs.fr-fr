---
title: Afficher l’activité du travail | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing job activity
- jobs [SQL Server Agent], viewing
- SQL Server Agent jobs, viewing
- displaying job activity
ms.assetid: 5c284e5e-7775-435d-ac49-f3f12a27ddc7
caps.latest.revision: 24
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 278b52cb4716a6cf7a6bef9044d740faecf4176a
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43815015"
---
# <a name="view-job-activity"></a>Afficher l’activité du travail
  Cette rubrique explique comment afficher l'état d'exécution des travaux de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Lorsque le service [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent démarre, une nouvelle session est créée et la table **sysjobactivity** de la base de données **msdb** est remplie avec tous les travaux définis existants. Cette table enregistre l'activité du travail en cours et son état. Vous pouvez utiliser le Moniteur d'activité des travaux dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent pour afficher l'état actuel des travaux. Si le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent se termine de manière inattendue, reportez-vous à la table **sysjobactivity** pour déterminer les travaux qui étaient en cours d'exécution au moment de l'interruption du service.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher l'activité des travaux, utilisez :**  
  
     [SQL Server Management Studio](#SSMS)  
  
     [Transact-SQL](#TSQL)  
  
## <a name="before-you-begin"></a>Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
 Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](implement-sql-server-agent-security.md).  
  
##  <a name="SSMS"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-job-activity"></a>Pour afficher l'activité des travaux  
  
1.  Dans **l’Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], puis développez-la.  
  
2.  Développez **SQL Server Agent**.  
  
3.  Cliquez avec le bouton droit sur **Moniteur d’activité des travaux** , puis cliquez sur **Afficher l’activité du travail**.  
  
4.  Dans le **Moniteur d'activité des travaux**, vous trouverez des détails relatifs à chaque travail défini pour ce serveur.  
  
5.  Cliquez avec le bouton droit sur un travail pour le démarrer, l'arrêter, l'activer ou le désactiver, actualiser son état tel qu'il est affiché dans le Moniteur d'activité des travaux, le supprimer ou encore afficher son historique ou ses propriétés.  Pour démarrer, arrêter, activer, désactiver ou actualiser plusieurs travaux, sélectionnez plusieurs lignes dans le Moniteur d'activité des travaux et cliquez avec le bouton droit sur votre sélection.  
  
6.  Pour mettre à jour le Moniteur d'activité des travaux, cliquez sur **Actualiser**. Pour afficher moins de lignes, cliquez sur **Filtre** et saisissez les paramètres de filtre.  
  
##  <a name="TSQL"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-job-activity"></a>Pour afficher l'activité des travaux  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- lists activity for all jobs that the current user has permission to view.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_help_jobactivity ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_help_jobactivity &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-jobactivity-transact-sql).  
  
  
