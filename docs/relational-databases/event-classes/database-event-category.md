---
title: Base de données, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cf3fd2a6cd222320e55b7336272bf9f662b81694
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68009570"
---
# <a name="database-event-category"></a>Catégorie d'événement Base de données
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  La catégorie d’événement **Base de données** contient des classes d’événements pour surveiller le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Data File Auto Grow, classe d’événements](../../relational-databases/event-classes/data-file-auto-grow-event-class.md)|Indique que la taille du fichier de données a augmenté automatiquement. Cet événement n'est pas déclenché si la taille du fichier de données augmente de manière explicite par le biais d'ALTER DATABASE.|  
|[Data File Auto Shrink, classe d’événements](../../relational-databases/event-classes/data-file-auto-shrink-event-class.md)|Indique que la taille du fichier de données a diminué.|  
|[Database Mirroring Connection, classe d’événements](../../relational-databases/event-classes/database-mirroring-connection-event-class.md)|Événement généré pour signaler l'état d'une connexion de transport de la mise en miroir de bases de données.|  
|[Database Mirroring State Change, classe d’événements](../../relational-databases/event-classes/database-mirroring-state-change-event-class.md)|Indique l'état des modifications de la base de données en miroir.|  
|[Database Suspect Data Page, classe d’événements](../../relational-databases/event-classes/database-suspect-data-page-event-class.md)|Indique qu’une page est ajoutée à la table **suspect_pages** dans la base de données **msdb** .|  
|[Classe d'événements Log File Auto Grow](../../relational-databases/event-classes/log-file-auto-grow-event-class.md)|Indique que la taille du fichier journal croît automatiquement. Cet événement n'est pas déclenché si le fichier journal a été augmenté de manière explicite par le biais d'ALTER DATABASE.|  
|[Log File Auto Shrink, classe d’événements](../../relational-databases/event-classes/log-file-auto-shrink-event-class.md)|Indique que la taille du fichier journal croît automatiquement. Cet événement n'est pas déclenché si la taille du fichier journal diminue explicitement par le biais d'ALTER DATABASE.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)  
  
  
