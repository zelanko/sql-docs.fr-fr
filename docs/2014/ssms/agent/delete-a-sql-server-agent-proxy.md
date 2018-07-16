---
title: Supprimer un proxy de SQL Server Agent | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- deleting SQL Server Agent proxies
- proxies [SQL Server Agent], deleting
- removing SQL Server Agent proxies
ms.assetid: 9248841d-7294-47d4-94f3-b34a0521fabc
caps.latest.revision: 23
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3cb408f82e10f4abb57ebe010b63707b2b9d5f96
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37265770"
---
# <a name="delete-a-sql-server-agent-proxy"></a>Supprimer un proxy de SQL Server Agent
  Cette rubrique explique comment supprimer un compte proxy de l'Agent dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Sécurité](#Security)  
  
-   **Pour supprimer un compte proxy de SQL Server Agent, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Lorsque vous supprimez un compte proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vérifiez que le proxy ne fait pas référence à des étapes de travail actives. Pour vérifier si des étapes de travail référencent le proxy, cliquez avec le bouton droit sur le proxy, sélectionnez **Propriétés** puis, dans la boîte de dialogue *Propriétés du compte proxy***nom_proxy**, sélectionnez la page **Références**. Si vous supprimez un proxy, il vous est proposé de réaffecter toutes les étapes de travail qui utilisent ce proxy dans la boîte de dialogue **Supprimer un objet** .  
  
-   Les proxys de l'Agent[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent les informations d'identification pour stocker les informations relatives aux comptes d'utilisateur Windows. L'utilisateur spécifié dans l'information d'identification doit être habilité à ouvrir une session en tant que programme de traitement par lots sur l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d'exécution.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vérifie l'accès au sous-système pour un proxy et donne accès au proxy à chaque exécution de l'étape de travail. Si le proxy n'a plus accès au sous-système, l'étape de travail échoue. Sinon, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] emprunte l'identité de l'utilisateur spécifié dans le proxy et exécute l'étape de travail.  
  
-   Si la connexion de l'utilisateur a accès au proxy ou que l'utilisateur appartient à un rôle qui y a accès, l'utilisateur peut recourir au proxy dans une étape de travail.  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent créer, modifier ou supprimer des comptes proxy.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Pour supprimer un compte proxy de SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus pour développer un serveur qui contient le compte proxy à supprimer.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Proxys** .  
  
4.  Cliquez sur le signe plus pour développer le sous-système qui contient le compte proxy à supprimer (par exemple, **Script ActiveX**).  
  
5.  Cliquez avec le bouton droit sur le compte proxy à supprimer, puis sélectionnez **Supprimer**.  
  
6.  Dans la boîte de dialogue **Supprimer un objet** , confirmez que le compte proxy correct est sélectionné. Activez la case à cocher **Réaffecter à** pour réaffecter les étapes de travail qui référencent ce compte proxy à un autre compte.  
  
7.  Cliquez sur **OK**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-delete-a-sql-server-agent-proxy-account"></a>Pour supprimer un compte proxy de SQL Server Agent  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- deletes the proxy "Catalog application proxy"  
    USE msdb ;  
    GO  
    EXEC dbo.sp_delete_proxy  
        @proxy_name = N'Catalog application proxy' ;  
    GO  
    ```  
  
 Pour plus d’informations, consultez [sp_delete_proxy &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql).  
  
  
