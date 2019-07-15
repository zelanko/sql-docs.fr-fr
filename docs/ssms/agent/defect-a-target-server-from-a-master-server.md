---
title: Annuler l’inscription d’un serveur cible dans un serveur maître | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: f7d83a7904f3b3d8f77f8ded6d4a30a88314a38e
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67688069"
---
# <a name="defect-a-target-server-from-a-master-server"></a>Annuler l'inscription d'un serveur cible dans un serveur maître
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique décrit comment désinscrire un serveur cible d'un serveur maître dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'objets SMO (SQL Server Management Objects). Exécutez cette procédure à partir du serveur cible.  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour annuler l'inscription d'un serveur cible à l'aide de :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
    [SMO](#PowerShellProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Pour exécuter cette procédure stockée, l'utilisateur doit être membre du rôle de serveur fixe **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Pour annuler l'inscription d'un serveur cible dans un serveur maître  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur qui est configuré comme serveur cible.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, pointez sur **Administration multiserveur**, puis cliquez sur **Désinscrire**.  
  
3.  Cliquez sur **Oui** pour confirmer que vous voulez désinscrire ce serveur cible d'un serveur maître.  
  
## <a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Pour annuler l'inscription d'un serveur cible dans un serveur maître  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
```  
sp_msx_defect ;  
```  
  
Pour plus d’informations, consultez [sp_msx_defect (Transact-SQL)](https://msdn.microsoft.com/0dfd963a-3bc5-4b58-94f7-aec976da2883).  
  
## <a name="PowerShellProcedure"></a>Utilisation d'objets SMO (SQL Server Management Objects)  
Utilisez la méthode **MsxDefect**.  
  
## <a name="see-also"></a>Voir aussi  
[Créer un environnement multi-serveur](../../ssms/agent/create-a-multiserver-environment.md)  
[Administration automatisée à l'échelle d'une entreprise](../../ssms/agent/automated-administration-across-an-enterprise.md)  
[Annuler l'inscription de plusieurs serveurs cibles dans un serveur maître](../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
