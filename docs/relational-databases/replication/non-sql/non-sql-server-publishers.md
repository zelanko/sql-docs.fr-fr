---
title: Serveurs de publications non-SQL Server | Microsoft Docs
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- heterogeneous database replication, non-SQL Server Publishers
- non-SQL Server Publishers
- heterogeneous data sources, non-SQL Server Publishers
- Publishers [SQL Server replication], Oracle
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
caps.latest.revision: "31"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 95c9750c86cfe5bb82d37948c24c5e140b2c3187
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="non-sql-server-publishers"></a>Serveurs de publications non-SQL Server  
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]  

La publication de données provenant de sources non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vous permet de regrouper des données dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peut s'abonner à des données transactionnelles ou à des données d'instantané à partir d'une base de données Oracle. Pour plus d’informations sur la publication à partir d’Oracle, consultez [Présentation de la publication Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge les scénarios divers suivants pour la réplication transactionnelle et d'instantané :  
  
-   Publication de données de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers des Abonnés non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  

-   La publication de données sur et depuis Oracle présente les restrictions suivantes :  
  | |Version 2016 ou antérieure |Version 2017 ou ultérieure |
  |-------|-------|--------|
  |Réplication depuis Oracle |Prise en charge d’Oracle 10g ou version antérieure uniquement |Prise en charge d’Oracle 10g ou version antérieure uniquement |
  |Réplication vers Oracle |Jusqu’à Oracle 12c |Non pris en charge |


 La réplication hétérogène sur les abonnés non SQL Server est déconseillée. La publication Oracle est déconseillée. Pour déplacer des données, créez des solutions à l'aide de la Capture de données modifiées et [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 La publication à partir de bases de données non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est idéale pour les scénarios suivants :  
  
|Scénario|Description|  
|--------------|-----------------|  
|Déploiements d'applications[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework|Développez avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en exploitant des données répliquées à partir d’une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Serveurs de secours pour l'entreposage des données|Gardez les bases de données intermédiaires [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] synchronisées avec une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .|  
|Migration vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Testez votre application en temps réel sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tout en répliquant les changements du système source. Basculez vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque vous êtes satisfait de la migration.|  
  
## <a name="see-also"></a>Voir aussi  
 [Réplication de base de données hétérogène](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  
