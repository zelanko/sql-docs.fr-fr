---
title: SQL Server, objet SQL Errors | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: b8f99ab36545778981ed509ed0575c039916d42f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85758929"
---
# <a name="sql-server-sql-errors-object"></a>Objet SQLServer:SQL Errors
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  L'objet **SQLServer:SQL Errors** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs qui permettent de surveiller les **Erreurs SQL**.  
  
 Ce tableau décrit les compteurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Erreurs SQL**de**.  
  
|Compteurs d'erreurs SQL de SQL Server|Description|  
|------------------------------------|-----------------|  
|**Erreurs/s**|Nombre d'erreurs par seconde.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Élément|Définition|  
|----------|----------------|  
|**_Total**|Informations sur toutes les erreurs.|  
|**DB Offline Errors**|Effectue le suivi des erreurs graves qui amènent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à mettre la base de données actuelle hors ligne.|  
|**Info Errors**|Informations relatives aux messages d'erreur qui fournissent des renseignements aux utilisateurs mais qui ne provoquent pas d'erreurs.|  
|**Kill Connection Errors**|Effectue le suivi des erreurs graves qui amènent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à mettre fin à la connexion actuelle.|  
|**User Errors**|Informations relatives aux erreurs utilisateur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
