---
title: Modifier un proxy de SQL Server Agent | Microsoft Docs
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-agent
ms.reviewer: 
ms.suite: sql
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- proxies [SQL Server Agent], modifying
- modifying SQL Server Agent proxy
ms.assetid: 6e1dfbaa-8089-4813-940c-d5a2e13d8552
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1f790e80504bcd6bac16b76a3d1ad0e751044979
ms.sourcegitcommit: d8ab09ad99e9ec30875076acee2ed303d61049b7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/23/2018
---
# <a name="modify-a-sql-server-agent-proxy"></a>Modifier un proxy de SQL Server Agent
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Cette rubrique explique comment modifier un proxy de l'Agent [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ou de [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour modifier un proxy de SQL Server Agent, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] utilisent les informations d'identification pour stocker les informations relatives aux comptes d'utilisateur Windows. L'utilisateur spécifié dans l'information d'identification doit être habilité à ouvrir une session en tant que programme de traitement par lots sur l'ordinateur sur lequel [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] est en cours d'exécution.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] vérifie l'accès au sous-système pour un proxy et donne accès au proxy à chaque exécution de l'étape de travail. Si le proxy n'a plus accès au sous-système, l'étape de travail échoue. Sinon, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] emprunte l'identité de l'utilisateur spécifié dans le proxy et exécute l'étape de travail.  
  
-   Si la connexion de l'utilisateur a accès au proxy ou que l'utilisateur appartient à un rôle qui y a accès, l'utilisateur peut recourir au proxy dans une étape de travail.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Autorisations  
Seuls les membres du rôle serveur fixe **sysadmin** peuvent créer, modifier ou supprimer des comptes proxy.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-modify-a-includessnoversionincludesssnoversionmdmd-agent-proxy"></a>Pour modifier un proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  
  
1.  Dans **Explorateur d'objets**, cliquez sur le signe plus pour développer le serveur qui contient le compte proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] que vous souhaitez modifier.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez sur le signe plus (+) pour développer le dossier **Proxys** .  
  
4.  Cliquez sur le signe plus pour développer le nœud du sous-système du proxy ( **Script ActiveX**, par exemple).  
  
5.  Cliquez avec le bouton droit sur le compte proxy que vous voulez modifier, puis sélectionnez **Propriétés**.  
  
6.  Dans la boîte de dialogue *Propriétés du compte proxy***nom_proxy**, apportez les modifications nécessaires au compte proxy. Pour plus d’informations sur les options de cette boîte de dialogue, consultez [Créer un proxy de SQL Server Agent](../../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
## <a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-modify-a-includessnoversionincludesssnoversionmdmd-agent-proxy"></a>Pour modifier un proxy de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]  
  
1.  Dans l'**Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- Disables the proxy named 'Catalog application proxy'.  
    USE msdb ;  
    GO  
    EXEC dbo.sp_update_proxy  
        @proxy_name = 'Catalog application proxy',  
        @enabled = 0;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_update_proxy (Transact-SQL)](http://msdn.microsoft.com/en-us/864fd0e6-9d61-4f07-92ef-145318d2f881).  
  
