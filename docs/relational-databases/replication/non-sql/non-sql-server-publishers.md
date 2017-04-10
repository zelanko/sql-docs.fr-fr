---
title: "Serveurs de publication non-SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "réplication de bases de données hétérogènes, serveurs de publications non-SQL Server"
  - "serveurs de publications non-SQL Server"
  - "sources de données hétérogènes, serveurs de publications non-SQL Server"
  - "Serveurs de publications [réplication SQL Server], Oracle"
ms.assetid: 08a160a6-33be-46b5-bc7b-d53180d8bdf1
caps.latest.revision: 31
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 31
---
# Serveurs de publication non-SQL Server
  Publication de données de non -[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sources vous permet de regrouper des données dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] peuvent s’abonner à des données transactionnelles publiées à partir d’une base de données Oracle ou d’instantané. Pour plus d’informations sur la publication à partir d’Oracle, consultez [vue d’ensemble de la publication Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
 La réplication hétérogène sur les abonnés non SQL Server est déconseillée. La publication Oracle est déconseillée. Pour déplacer des données, créez des solutions à l'aide de la Capture de données modifiées et [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 La publication à partir de bases de données non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est idéale pour les scénarios suivants :  
  
|Scénario|Description|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Déploiements d’applications .NET framework|Développez avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en exploitant des données répliquées à partir d'une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Serveurs de secours pour l'entreposage des données|Conserver [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] intermédiaire des bases de données synchronisées avec non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de données.|  
|Migration vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Testez votre application en temps réel sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tout en répliquant les changements du système source. Basculez vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque vous êtes satisfait de la migration.|  
  
## Voir aussi  
 [Réplication hétérogène d'une base de données](../../../relational-databases/replication/non-sql/heterogeneous-database-replication.md)  
  
  