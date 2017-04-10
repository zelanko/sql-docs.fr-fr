---
title: "Cr&#233;er une alerte de base de donn&#233;es SQL&#160;Server | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "performances des bases de données [SQL Server], alertes"
  - "alertes [SQL Server], création"
  - "seuils [SQL Server]"
  - "alertes de base de données [SQL Server]"
  - "paramétrage des bases de données [SQL Server], alertes"
  - "analyse des performances [SQL Server], alertes"
  - "analyse des performances du serveur [SQL Server], alertes"
  - "surveillance des bases de données [SQL Server], alertes"
  - "performances du serveur [SQL Server], alertes"
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
caps.latest.revision: 22
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 22
---
# Cr&#233;er une alerte de base de donn&#233;es SQL&#160;Server
  Vous pouvez utiliser le Moniteur système pour créer une alerte qui sera émise lorsque la valeur seuil d'un compteur du Moniteur système sera atteinte. En réponse à l'alerte, le Moniteur système lance une application, telle qu'une application personnalisée écrite pour prendre en charge la condition d'alerte. Par exemple, vous pouvez créer une alerte déclenchée quand le nombre d'interblocages dépasse une valeur spécifique.  
  
 Les alertes peuvent également être définies en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Alertes](../../ssms/agent/alerts.md).  
  
 Pour plus d’informations sur le Moniteur système, afin de configurer une alerte de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Configurer une alerte de base de données SQL Server &#40;Windows&#41;](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md).  
  
## Voir aussi  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  