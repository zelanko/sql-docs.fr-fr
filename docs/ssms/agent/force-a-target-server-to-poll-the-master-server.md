---
title: Forcer un serveur cible à interroger le serveur maître
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- forcing master server polling
- polling master servers [SQL Server]
- master servers [SQL Server], polling
- target servers [SQL Server], polling the master server
ms.assetid: f1189a47-5ac3-45e2-9c5f-847810672279
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5e0dc40d29ed0efd8dd6ce95172c63a1e1a853b0
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715807"
---
# <a name="force-a-target-server-to-poll-the-master-server"></a>Forcer un serveur cible à interroger le serveur maître
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique explique comment forcer l'interrogation du serveur maître par un serveur cible. Le serveur cible doit être un serveur inscrit sur le serveur maître.  
  
Un travail est une série d'actions exécutées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. Un travail multiserveur est un travail exécuté par un serveur maître sur un ou plusieurs serveurs cibles. Chaque serveur cible peut exécuter une instance du même travail au même moment. Chaque serveur cible interroge régulièrement le serveur maître, télécharge une copie des nouveaux travaux affectés au serveur cible, puis se déconnecte. Le serveur cible exécute localement le travail, puis se reconnecte au serveur maître pour charger l'état de la sortie du travail.  
  
> [!NOTE]  
> Si le serveur maître est accessible lorsque le serveur cible tente de charger l'état du travail, ce dernier est mis en attente dans le spouleur jusqu'à ce que le serveur maître soit accessible.  
  
-   **Avant de commencer :**  [Limitations et restrictions](#Restrictions), [sécurité](#Security)  
  
-   **Pour forcer l’interrogation du serveur maître par un serveur cible, avec :** [SQL Server Management Studio](#SSMS)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="limitations-and-restrictions"></a><a name="Restrictions"></a>Limitations et restrictions  
Le serveur cible doit être un serveur inscrit sur le serveur maître. Vous devez exécuter les instructions fournies dans cette rubrique à partir du serveur maître.  
  
### <a name="security"></a><a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md) et [Choose the Right SQL Server Agent Service Account for Multiserver Environments](../../ssms/agent/choose-the-right-sql-server-agent-service-account-for-multiserver-environments.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Utilisation de SQL Server Management Studio  
**Pour forcer l'interrogation d'un serveur maître par un serveur cible**  
  
1.  Dans l' **Explorateur d'objets**, développez le serveur maître.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, pointez sur **Administration multiserveur**, puis cliquez sur **Gérer les serveurs cibles**.  
  
3.  Cliquez sur un serveur cible, puis sur **Forcer l'interrogation**.  
  
