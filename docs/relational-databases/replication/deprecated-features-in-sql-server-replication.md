---
title: "Fonctionnalit&#233;s d&#233;conseill&#233;es dans la r&#233;plication SQL Server | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "fonctionnalités déconseillées [réplication SQL Server]"
ms.assetid: 46bd3edd-d6de-40a6-a015-21cce8321feb
caps.latest.revision: 67
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 67
---
# Fonctionnalit&#233;s d&#233;conseill&#233;es dans la r&#233;plication SQL Server
  Cette rubrique décrit les fonctionnalités de réplication déconseillées qui sont toujours disponibles dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Il est prévu que ces fonctionnalités soient supprimées dans une prochaine version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Les fonctions déconseillées ne doivent pas être utilisées dans de nouvelles applications.  
  
## Éléments déconseillés dans [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|La réplication est prise en charge si chaque point de terminaison [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se trouve dans deux versions principales de la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ne prend pas en charge la réplication vers ou provenant de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ou [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)].|  
|[!INCLUDE[ssEW](../../includes/ssew-md.md)]|La réplication est prise en charge si chaque point de terminaison [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se trouve dans deux versions principales de la version actuelle de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] ne prend pas en charge la réplication vers ou depuis [!INCLUDE[ssEW](../../includes/ssew-md.md)].|  
  
## Voir aussi  
 [Compatibilité descendante de la réplication](../../relational-databases/replication/replication-backward-compatibility.md)  
  
  