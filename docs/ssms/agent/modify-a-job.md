---
title: Modifier un travail | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
ms.assetid: dd5e5f20-20c4-4ab9-a19a-db87577dcd43
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 34e8c912bf0499166a20fc49fd807544d2b808bd
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="modify-a-job"></a>Modifier un travail
Cette rubrique explique comment modifier les propriétés des travaux de l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)], [!INCLUDE[tsql](../../includes/tsql_md.md)]ou de SQL Server Management Objects.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :** ,  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour modifier un travail, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
Un travail maître [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent ne peut pas être ciblé sur des serveurs locaux et distants à la fois.  
  
### <a name="Security"></a>Sécurité  
Vous pouvez modifier uniquement les travaux dont vous êtes propriétaire, à moins d'être membre du rôle de serveur fixe **sysadmin** . Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-a-job"></a>Pour modifier un travail  
  
1.  Dans l' **Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **Agent SQL Server**et **Travaux**, cliquez avec le bouton droit sur le travail à modifier, puis cliquez sur **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés du travail** , mettez à jour les propriétés, les étapes, la planification, les alertes et les notifications du travail en utilisant les pages correspondantes.  
  
## <a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-modify-a-job"></a>Pour modifier un travail  
  
1.  Dans l'Explorateur d'objets, connectez-vous à une instance du moteur de base de données et développez-la.  
  
2.  Dans la barre d'outils, cliquez sur **Nouvelle requête**.  
  
3.  Dans la fenêtre de requête, utilisez les procédures stockées système suivantes pour modifier un travail.  
  
    -   Exécutez [sp_update_job (Transact-SQL)](http://msdn.microsoft.com/en-us/cbdfea38-9e42-47f3-8fc8-5978b82e2623) pour modifier les attributs d’un travail.  
  
    -   Exécutez [sp_update_schedule (Transact-SQL)](http://msdn.microsoft.com/en-us/97b3119b-e43e-447a-bbfb-0b5499e2fefe) pour modifier les détails de planification d’une définition de travail.  
  
    -   Exécutez [sp_add_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/97900032-523d-49d6-9865-2734fba1c755) pour ajouter de nouvelles étapes de travail.  
  
    -   Exécutez [sp_update_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/e158802c-c347-4a5d-bf75-c03e5ae56e6b) pour modifier des étapes de travail existantes.  
  
    -   Exécutez [sp_delete_jobstep (Transact-SQL)](http://msdn.microsoft.com/en-us/421ede8e-ad57-474a-9fb9-92f70a3e77e3) pour supprimer une étape d’un travail.  
  
    -   Procédures stockées supplémentaires pour modifier un travail maître de l'Agent SQL Server :  
  
        -   Exécutez [sp_delete_jobserver (Transact-SQL)](http://msdn.microsoft.com/en-us/6d63ed32-68cf-4d8f-aa40-05a3826e05b8) pour supprimer un serveur actuellement associé à un travail.  
  
        -   Exécutez [sp_add_jobserver (Transact-SQL)](http://msdn.microsoft.com/en-us/485252cc-0081-490a-9bd1-cbbd68eea286) pour associer un serveur au travail actif.  
  
## <a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour modifier un travail**  
  
Utilisez la classe **Job** à l’aide du langage de programmation de votre choix, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](http://msdn.microsoft.com/library/ms162169.aspx).  
  

