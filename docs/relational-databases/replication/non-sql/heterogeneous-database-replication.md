---
title: "R&#233;plication h&#233;t&#233;rog&#232;ne d&#39;une base de donn&#233;es | Microsoft Docs"
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
  - "réplication de bases de données hétérogènes, à propos de la réplication de bases de données hétérogènes"
  - "réplication [SQL Server], réplication de bases de données hétérogènes"
  - "réplication de bases de données hétérogènes"
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
caps.latest.revision: 41
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 41
---
# R&#233;plication h&#233;t&#233;rog&#232;ne d&#39;une base de donn&#233;es
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prend en charge les scénarios divers suivants pour la réplication transactionnelle et de capture instantanée :  
  
-   Publication de données d'Oracle vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Publication de données de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] vers des Abonnés non [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 La réplication hétérogène sur les abonnés non SQL Server est déconseillée. La publication Oracle est déconseillée. Pour déplacer des données, créez des solutions à l'aide de la Capture de données modifiées et [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## Publication de données à partir d'Oracle  
 Vous pouvez utiliser [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pour publier des données à partir d'Oracle avec la plupart des fonctions et la même facilité qu'offre la réplication transactionnelle et d'instantané de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. La publication de données à partir d'Oracle est idéale pour les scénarios suivants :  
  
|Scénario|Description|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Déploiements d’applications .NET framework|Développez avec [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio et [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] en exploitant des données répliquées à partir d'une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Serveurs de secours pour l'entreposage des données|Conserver [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] intermédiaire des bases de données synchronisées avec non[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] base de données.|  
|Migration vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]|Testez votre application en temps réel sur [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tout en répliquant les changements du système source. Basculez vers [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] lorsque vous êtes satisfait de la migration.|  
  
 Pour plus d’informations, consultez [vue d’ensemble de la publication Oracle](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md).  
  
## Publication de données vers des Abonnés non-SQL Server  
 Les bases de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sont prises en charge en tant qu'Abonnés aux publications transactionnelles et d'instantané :  
  
-   Oracle pour toutes les plateformes prises en charge par Oracle.  
  
-   IBM DB2 pour AS400, MVS, Unix, Linux et Windows.  
  
 Pour plus d’informations, consultez la page [les abonnés non-SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md).  
  
  