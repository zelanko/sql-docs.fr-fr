---
title: SQL Server, objet SQL Errors | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
caps.latest.revision: 13
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5e3bf1e3113f64e68933c27a23e58f21f0cd6553
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36041998"
---
# <a name="sql-server-sql-errors-object"></a>Objet SQLServer:SQL Errors
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
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  