---
title: "Supprimer un opérateur | Microsoft Docs"
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
- canceling operators
- removing operators
- deleting operators
- dropping operators
- jobs [SQL Server Agent], operators
- operators (users) [Database Engine], deleting with Management Studio
ms.assetid: 2b7b8627-082d-4189-8584-abd3a9b604cf
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: e34da1cc7395a20132d808039834262d66c50887
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="delete-an-operator"></a>Delete an Operator
Cette rubrique décrit la suppression d'un opérateur de façon à ce qu'il ne reçoive plus de notification d'alerte de l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ou de [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour supprimer un opérateur, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
Si vous supprimez un opérateur, toutes les notifications qui lui sont associées le sont également.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Autorisations  
Les membres du rôle serveur fixe **sysadmin** peuvent supprimer des opérateurs.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-an-operator"></a>Pour supprimer un opérateur  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur qui contient l'opérateur que vous souhaitez supprimer.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Opérateurs** .  
  
4.  Cliquez avec le bouton droit sur l’opérateur à supprimer, puis sélectionnez **Supprimer**.  
  
5.  Dans la boîte de dialogue **Supprimer un objet** , assurez-vous que l'opérateur correct est sélectionné, puis cliquez sur **OK**. Si vous voulez qu'un autre opérateur reçoive les alertes et les travaux envoyés à l'opérateur supprimé, activez l'option **Réaffecter à** et sélectionnez un opérateur dans la liste.  
  
## <a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-delete-an-operator"></a>Pour supprimer un opérateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- deletes operator 'Test Operator' and reassigns all alerts and jobs
    --  sent to that operator to 'François Ajenstat'  
    USE msdb ;  
    GO  
  
    EXEC sp_delete_operator @name = 'Test Operator',  
        @reassign_to_operator = 'François Ajenstat';  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_delete_operator (Transact-SQL)](http://msdn.microsoft.com/en-us/ff6c2c4b-e9fe-4d0c-bbc2-a2ddcc1acb95).  
  

