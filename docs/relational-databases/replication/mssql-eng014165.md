---
title: "MSSQL_ENG014165 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014165 (erreur)"
ms.assetid: 7bb07672-310c-4f51-ae76-c55e7c8d51ea
caps.latest.revision: 12
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 12
---
# MSSQL_ENG014165
    
## Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14165|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le seuil [%s:%s] de la publication [%s] a été défini. Assurez-vous que l'Agent de fusion s'exécute et peut respecter les conditions de latence.|  
  
## Explication  
 La réplication vous permet d'activer des avertissements pour plusieurs situations. Vous pouvez, entre autres, signaler l'incapacité à traiter un nombre suffisant de lignes lors de la synchronisation des modifications entre un serveur de publication de fusion et un Abonné. Vous pouvez spécifier des seuils différents pour les connexions LAN et pour les connexions d'accès à distance.  
  
 Lorsque vous activez un avertissement à l’aide du moniteur de réplication ou [sp_replmonitorchangepublicationthreshold](../../relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql.md), vous spécifiez un seuil qui détermine si un avertissement est déclenché. Quand ce seuil est atteint ou dépassé, un avertissement s'affiche dans le moniteur de réplication et un événement est enregistré dans le journal des événements Windows. Le franchissement d'un seuil peut également déclencher une alerte de l'Agent SQL Server. Pour plus d’informations, consultez [définition des seuils et des avertissements dans le moniteur de réplication](../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md) et [surveiller la réplication par programme](../../relational-databases/replication/monitor/programmatically-monitor-replication.md).  
  
## Action de l'utilisateur  
 Si un abonnement ne respecte pas un seuil de traitement de lignes, vous devez déterminer si le système a un problème de performance ou si le seuil doit être modifié. Une fois la réplication configurée, élaborez un référentiel de performances qui vous permettra d'évaluer les performances de la réplication avec une charge de travail standard pour vos applications et votre topologie. Intégrez le nombre de lignes traitées à ce référentiel afin de pouvoir définir une valeur appropriée pour le seuil.  
  
 Si la valeur du seuil est appropriée, mais qu'elle continue à être franchie, vous devez déterminer où se trouve le goulet d'étranglement dans le système. Pour plus d'informations sur le contrôle des performances de réplication et la résolution des éventuels problèmes, consultez les rubriques suivantes :  
  
-   [Surveiller les performances avec le moniteur de réplication](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md) (en particulier la section « Affichage détaillé synchronisation performances de réplication de fusion »)  
  
## Voir aussi  
 [Erreurs et événements référence & #40 ; Réplication & #41 ;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  