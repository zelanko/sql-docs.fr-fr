---
title: "Modifier un opérateur | Microsoft Docs"
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
- SQL Server Agent jobs, operators
- modifying operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], modifying with Management Studio
ms.assetid: b2ba2168-ca0b-4b59-9007-4e1e4c30679e
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b8628cf736650c53493501777f79f970ff864209
ms.contentlocale: fr-fr
ms.lasthandoff: 08/18/2017

---
# <a name="edit-an-operator"></a>Modifier un opérateur
Cette rubrique explique comment modifier la disponibilité d'un opérateur pour recevoir des notifications et leurs adresses d'envoi par courrier électronique, récepteur de radiomessagerie et réseau dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ou de [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour modifier un opérateur, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   Les options du récepteur de radiomessagerie et **net send** seront supprimées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans une version future de [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Évitez d'utiliser ces fonctionnalités dans une nouvelle tâche de développement et prévoyez de modifier les applications qui les utilisent actuellement.  
  
-   Remarque : SQL Server Agent doit être configuré pour utiliser la messagerie de base de données pour envoyer des notifications aux opérateurs par messagerie électronique ou radiomessagerie. Pour plus d'informations, consultez [Affecter des alertes à un opérateur](http://msdn.microsoft.com/library/ms190038.aspx).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] est un outil dont l'interface graphique permet de gérer facilement les travaux. Son utilisation est recommandée pour créer et gérer l'infrastructure des travaux.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Seuls les membres du rôle serveur fixe **sysadmin** peuvent modifier des opérateurs.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-edit-an-operator"></a>Pour modifier un opérateur  
  
1.  Dans **l’Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient l'opérateur que vous souhaitez modifier.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Opérateurs** .  
  
4.  Cliquez avec le bouton droit sur l’opérateur que vous souhaitez modifier, puis sélectionnez **Propriétés**.  
  
    Pour plus d’informations sur les options disponibles contenues dans la boîte de dialogue *Propriétés de***nom_opérateur** , consultez :  
  
    -   [Propriétés des opérateurs - Nouvel opérateur &#40;page Général&#41;$$$](../../ssms/agent/operator-properties-new-operator-general-page.md)  
  
    -   [Propriétés des opérateurs - Nouvel opérateur &#40;page Notifications&#41;$$$](../../ssms/agent/operator-properties-new-operator-notifications-page.md)  
  
    -   [Propriétés Opérateur &#40;page Historique&#41;](../../ssms/agent/operator-properties-history-page.md)  
  
5.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
## <a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-edit-an-operator"></a>Pour modifier un opérateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- updates the operator status to enabled, and sets the days   
    -- (from Monday through Friday, from 8 A.M. through 5 P.M.)
    --  when the operator can be paged.   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_operator   
        @name = N'François Ajenstat',  
        @enabled = 1,  
        @email_address = N'françoisa',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 64 ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_update_operator (Transact-SQL)](http://msdn.microsoft.com/en-us/231750a6-4828-4d03-afe6-b91d38c42ed3).  
  

