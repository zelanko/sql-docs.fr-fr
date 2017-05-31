---
title: MSSQLSERVER_32043 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 32043 (Database Engine error)
ms.assetid: a0c48ae3-4c8c-419c-afb5-579fcefac01d
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4f4a6d7b4331e1e7953b80d825a638321808ef82
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver32043"></a>MSSQLSERVER_32043
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|32043|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum32043|  
|Texte du message|L'alerte relative au journal non restauré s'est déclenchée. La valeur actuelle de '%d' dépasse le seuil '%d'.|  
  
## <a name="explanation"></a>Explication  
Cet événement de mise en miroir de bases de données est émis sur l'instance du serveur miroir pour indiquer que la quantité de journal non restauré a atteint la valeur de seuil définie par l'utilisateur. En règle générale, cet événement se produit car les performances du système ont changé. Soit la bande passante entre les deux systèmes a diminué, soit la charge a augmenté.  
  
Un journal non restauré est un journal qui a été reçu par l'instance du serveur miroir et qui a été écrit sur le disque, mais qui attend d'être restauré dans la base de données miroir. La quantité de journal non restauré en kilo-octets (Ko) est une mesure de performance qui peut vous aider à évaluer le temps de basculement actuel. La durée requise pour l'application du journal non restauré constitue le principal facteur du temps de basculement, auquel s'ajoute un petit laps de temps supplémentaire nécessaire pour récupérer la base de données et la mettre en ligne.  
  
> [!NOTE]  
> Lorsque le basculement est automatique, la durée nécessaire au système pour détecter la défaillance est indépendante du temps de basculement.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Vérifiez les charges incombant aux instances du serveur principal et du serveur miroir et à leur connexion réseau pour déterminer la cause du problème.  
  
## <a name="see-also"></a>Voir aussi  
[Mise en miroir de bases de données &#40;SQL Server&#41;](~/database-engine/database-mirroring/database-mirroring-sql-server.md)  
[Utiliser des seuils d’avertissement et d’alertes sur des métriques de performances de mise en miroir &#40;SQL Server&#41;](~/database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  

