---
title: Créer une alerte de base de données SQL Server | Microsoft Docs
description: Vous pouvez utiliser le Moniteur système pour créer une alerte de base de données SQL Server qui est émise quand la valeur seuil d’un compteur du Moniteur système est atteinte.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
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
author: WilliamDAssafMSFT
ms.author: wiassaf
ms.openlocfilehash: 512c902e0b35e15b65866464500b4928e105d4ad
ms.sourcegitcommit: 0e0cd9347c029e0c7c9f3fe6d39985a6d3af967d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96506033"
---
# <a name="create-a-sql-server-database-alert"></a>Créer une alerte de base de données SQL Server
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Vous pouvez utiliser le Moniteur système pour créer une alerte qui sera émise lorsque la valeur seuil d'un compteur du Moniteur système sera atteinte. En réponse à l'alerte, le Moniteur système lance une application, telle qu'une application personnalisée écrite pour prendre en charge la condition d'alerte. Par exemple, vous pouvez créer une alerte déclenchée quand le nombre d'interblocages dépasse une valeur spécifique.  
  
 Les alertes peuvent également être définies en utilisant [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] et l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Alertes](../../ssms/agent/alerts.md).  
  
 Pour plus d’informations sur le Moniteur système, afin de configurer une alerte de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [Configurer une alerte de base de données SQL Server &#40;Windows&#41;](../../relational-databases/performance/set-up-a-sql-server-database-alert-windows.md).  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)  
  
  
