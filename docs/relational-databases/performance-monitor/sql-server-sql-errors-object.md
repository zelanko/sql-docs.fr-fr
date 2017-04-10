---
title: "Objet SQLServer:SQL Errors | Microsoft Docs"
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
  - "SQL Errors (objet)"
  - "SQLServer:SQL Errors"
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# Objet SQLServer:SQL Errors
  L'objet **SQLServer:SQL Errors** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs qui permettent de surveiller les **Erreurs SQL**.  
  
 Le tableau suivant décrit les compteurs d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Erreurs SQL** .  
  
|Compteurs d'erreurs SQL de SQL Server|Description|  
|------------------------------------|-----------------|  
|**Erreurs/s**|Nombre d'erreurs par seconde.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Élément|Définition|  
|----------|----------------|  
|**_Total**|Informations sur toutes les erreurs.|  
|**DB Offline Errors**|Effectue le suivi des erreurs graves qui amènent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à mettre la base de données actuelle hors ligne.|  
|**Info Errors**|Informations relatives aux messages d'erreur qui fournissent des renseignements aux utilisateurs mais qui ne provoquent pas d'erreurs.|  
|**Kill Connection Errors**|Effectue le suivi des erreurs graves qui amènent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à mettre fin à la connexion actuelle.|  
|**User Errors**|Informations relatives aux erreurs utilisateur.|  
  
## Voir aussi  
 [Surveiller l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  