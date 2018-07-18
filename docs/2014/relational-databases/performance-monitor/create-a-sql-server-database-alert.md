---
title: Créer une alerte de base de données SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- database performance [SQL Server], alerts
- alerts [SQL Server], creating
- thresholds [SQL Server]
- database alerts [SQL Server]
- tuning databases [SQL Server], alerts
- monitoring performance [SQL Server], alerts
- monitoring server performance [SQL Server], alerts
- database monitoring [SQL Server], alerts
- server performance [SQL Server], alerts
ms.assetid: 0511136a-1b6b-4095-aa45-39e77b67aba2
caps.latest.revision: 21
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 15de81eda0aac3e2f441aade557d8f7730a3f22f
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37283075"
---
# <a name="create-a-sql-server-database-alert"></a>Créer une alerte de base de données SQL Server
  Vous pouvez utiliser le Moniteur système pour créer une alerte qui sera émise lorsque la valeur seuil d'un compteur du Moniteur système sera atteinte. En réponse à l'alerte, le Moniteur système lance une application, telle qu'une application personnalisée écrite pour prendre en charge la condition d'alerte. Par exemple, vous pouvez créer une alerte déclenchée quand le nombre d'interblocages dépasse une valeur spécifique.  
  
 Les alertes peuvent également être définies en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Alertes](../../ssms/agent/alerts.md).  
  
 Pour plus d’informations sur le Moniteur système, afin de configurer une alerte de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Configurer une alerte de base de données SQL Server &#40;Windows&#41;](../performance/set-up-a-sql-server-database-alert-windows.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_alert &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-alert-transact-sql)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql)  
  
  
