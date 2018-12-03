---
title: SQL Server, objet SQL Errors | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 0372670c89a2367bf12bc646d6aada5ceba29776
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158587"
---
# <a name="sql-server-sql-errors-object"></a>Objet SQLServer:SQL Errors
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  L'objet **SQLServer:SQL Errors** de Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des compteurs qui permettent de surveiller les **Erreurs SQL**.  
  
 Le tableau suivant décrit les compteurs d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Erreurs SQL** .  
  
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
  
## <a name="see-also"></a> Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
