---
title: Inscrire un serveur cible dans un serveur maître | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- enlisting target servers [SQL Server]
- SQL Server Agent jobs, target servers
- master servers [SQL Server], enlisting target servers
- SQL Server Agent jobs, master servers
- target servers [SQL Server], enlisting
ms.assetid: 7633adb5-d140-4e58-a8f2-5b4b50c2f95b
author: markingmyname
ms.author: maghan
manager: jroth
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: c4caf0b7b65f084d7810e0d718fae1a402cbb9c3
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67687136"
---
# <a name="enlist-a-target-server-to-a-master-server"></a>Inscrire un serveur cible dans un serveur maître
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment ajouter des serveurs cibles à une configuration d'administration multiserveur. Exécutez la procédure suivante à partir du serveur maître : dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)], ou d'objets SMO (SQL Server Management Objects).  
  
Pour plus d’informations sur la manière dont le compte Windows utilisé pour le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent affecte un environnement multiserveur, consultez [Créer un environnement multi-serveur](../../ssms/agent/create-a-multiserver-environment.md).  
  
Le chiffrement SSL (Secure Sockets Layer) complet et la validation de certificats sont activés pour les connexions entre les serveurs maîtres et les serveurs cible par défaut. Pour plus d’informations, consultez [Définir des options de chiffrement sur des serveurs cibles](../../ssms/agent/set-encryption-options-on-target-servers.md).  
  
**Dans cette rubrique**  
  
-   **Pour inscrire un serveur cible à l'aide de :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-enlist-a-target-server"></a>Pour inscrire un serveur cible  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur configuré en tant que serveur maître.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent**, pointez sur **Administration multiserveur**, puis cliquez sur **Ajouter des serveurs cibles**.  
  
3.  Exécutez l'Assistant Création d'un serveur cible, qui vous guide tout au long du processus.  
  
## <a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-enlist-a-target-server"></a>Pour inscrire un serveur cible  
  
1.  Utilisez la procédure stockée **sp_msx_enlist** .  Pour plus d’informations, consultez [sp_msx_enlist (Transact-SQL)](https://msdn.microsoft.com/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f).  
  
## <a name="see-also"></a>Voir aussi  
[Administration automatisée à l'échelle d'une entreprise](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  
