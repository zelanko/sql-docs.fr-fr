---
title: "Classe d&#39;&#233;v&#233;nements PreConnect:Completed | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe d'événements PreConnect:Completed"
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
caps.latest.revision: 18
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 18
---
# Classe d&#39;&#233;v&#233;nements PreConnect:Completed
  La classe d’événements PreConnect:Completed indique quand un déclencheur LOGON ou la fonction classifieur de Resource Governor finit de s’exécuter.  
  
## Colonnes de données de la classe d'événements PreConnect:Completed  
  
|Nom de la colonne de données|Type de données|Description|ID de la colonne|Filtrable|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|216|27|Non|  
|SPID|**int**|ID du processus serveur qui déclenche cet événement.|12|Oui|  
|EventSubClass|**int**|1 pour la fonction classifieur définie par l'utilisateur.|21|Oui|  
|StartTime|**datetime**|Heure de démarrage de la fonction classifieur définie par l'utilisateur.|14|Oui|  
|EndTime|**datetime**|Heure de démarrage de la fonction classifieur définie par l'utilisateur.|15|Oui|  
|Duration|**bigint**|Temps en microsecondes utilisé par la fonction classifieur.|13|Oui|  
|ObjectID|**int**|ID de l'objet classifieur défini par l'utilisateur.|22|Oui|  
|Unité centrale|**int**|Utilisation de l'UC en millisecondes.|18|Oui|  
|Reads|**int**|Nombre de lectures logiques.|16|Oui|  
|Writes|**int**|Nombre d'écritures logiques.|17|Oui|  
|GroupID|**int**|ID du groupe de charges de travail classifié.|66|Oui|  
|Erreur|**int**|Dernier numéro d'erreur si la fonction classifieur définie par l'utilisateur ne peut pas s'exécuter.|31|Oui|  
|État|**int**|État de la dernière erreur.|30|Oui|  
|TargetUserName|**sysname**|Valeur de retour (nom de groupe de charges de travail) pour la fonction classifieur définie par l'utilisateur si le système ne peut pas trouver un groupe actif correspondant. Dans le cas contraire, cette colonne a la valeur NULL.|39|Oui|  
|ObjectName|**nvarchar (256)**|Nom en deux parties de la fonction classifieur définie par l'utilisateur. Par exemple, dbo.classifier.|34|Oui|  
  
## Voir aussi  
 [Événements étendus](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Starting, classe d'événements](../../relational-databases/event-classes/preconnect-starting-event-class.md)   
 [Resource Governor](../../relational-databases/resource-governor/resource-governor.md)  
  
  