---
title: Base de données, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], Database event category
- Database event category [SQL Server]
- SQL Server event classes, Database event category
ms.assetid: b61af738-f144-4992-b0b2-d44cb7240991
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0d725f95fc8e9de0865ad895abd860d5f03687b
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793001"
---
# <a name="database-event-category"></a>Catégorie d'événement Base de données
  La catégorie d’événement **Base de données** contient des classes d’événements pour surveiller le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Classe d'événements Data File Auto Grow](data-file-auto-grow-event-class.md)|Indique que la taille du fichier de données a augmenté automatiquement. Cet événement n'est pas déclenché si la taille du fichier de données augmente de manière explicite par le biais d'ALTER DATABASE.|  
|[Data File Auto Shrink, classe d’événements](data-file-auto-shrink-event-class.md)|Indique que la taille du fichier de données a diminué.|  
|[Classe d'événements de connexion de mise en miroir de bases de données](database-mirroring-connection-event-class.md)|Événement généré pour signaler l'état d'une connexion de transport de la mise en miroir de bases de données.|  
|[Classe d'événements Database Mirroring State Change](database-mirroring-state-change-event-class.md)|Indique l'état des modifications de la base de données en miroir.|  
|[Classe d'événements Database Suspect Data Page](database-suspect-data-page-event-class.md)|Indique qu’une page est ajoutée à la table **suspect_pages** dans la base de données **msdb** .|  
|[Classe d'événements Log File Auto Grow](log-file-auto-grow-event-class.md)|Indique que la taille du fichier journal croît automatiquement. Cet événement n'est pas déclenché si le fichier journal a été augmenté de manière explicite par le biais d'ALTER DATABASE.|  
|[Log File Auto Shrink, classe d’événements](log-file-auto-shrink-event-class.md)|Indique que la taille du fichier journal croît automatiquement. Cet événement n'est pas déclenché si la taille du fichier journal diminue explicitement par le biais d'ALTER DATABASE.|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)  
  
  
