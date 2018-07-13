---
title: PreConnect:Completed, classe d’événements | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5a91728174a11ecf1cdd008b5aa1c9829da890ff
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37150690"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed, classe d’événements
  La classe d’événements PreConnect:Completed indique quand un déclencheur LOGON ou la fonction classifieur de Resource Governor finit de s’exécuter.  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>Colonnes de données de la classe d'événements PreConnect:Completed  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|`int`|216|27|non|  
|SPID|`int`|ID du processus serveur qui déclenche cet événement.|12|Oui|  
|EventSubClass|`int`|1 pour la fonction classifieur définie par l'utilisateur.|21|Oui|  
|StartTime|`datetime`|Heure de démarrage de la fonction classifieur définie par l'utilisateur.|14|Oui|  
|EndTime|`datetime`|Heure de démarrage de la fonction classifieur définie par l'utilisateur.|15|Oui|  
|Duration|`bigint`|Temps en microsecondes utilisé par la fonction classifieur.|13|Oui|  
|ObjectID|`int`|ID de l'objet classifieur défini par l'utilisateur.|22|Oui|  
|Unité centrale|`int`|Utilisation de l'UC en millisecondes.|18|Oui|  
|Reads|`int`|Nombre de lectures logiques.|16|Oui|  
|Writes|`int`|Nombre d'écritures logiques.|17|Oui|  
|GroupID|`int`|ID du groupe de charges de travail classifié.|66|Oui|  
|Error|`int`|Dernier numéro d'erreur si la fonction classifieur définie par l'utilisateur ne peut pas s'exécuter.|31|Oui|  
|État|`int`|État de la dernière erreur.|30|Oui|  
|TargetUserName|`sysname`|Valeur de retour (nom de groupe de charges de travail) pour la fonction classifieur définie par l'utilisateur si le système ne peut pas trouver un groupe actif correspondant. Dans le cas contraire, cette colonne a la valeur NULL.|39|Oui|  
|ObjectName|`nvarchar(256)`|Nom en deux parties de la fonction classifieur définie par l'utilisateur. Par exemple, dbo.classifier.|34|Oui|  
  
## <a name="see-also"></a>Voir aussi  
 [Événements étendus](../extended-events/extended-events.md)   
 [PreConnect:Starting, classe d'événements](preconnect-starting-event-class.md)   
 [Resource Governor](../resource-governor/resource-governor.md)  
  
  
