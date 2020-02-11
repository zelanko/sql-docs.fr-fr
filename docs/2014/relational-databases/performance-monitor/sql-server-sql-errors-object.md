---
title: SQL Server, objet SQL Errors | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQL Errors object
- SQLServer:SQL Errors
ms.assetid: 6e5273ca-29cb-4618-88a2-70b9b8d6cf76
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f36cd694756544a44df657d97fd84e1967167b55
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63183010"
---
# <a name="sql-server-sql-errors-object"></a>Objet SQLServer:SQL Errors
  L’objet **SqlServer : SQL Errors** de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Microsoft fournit des compteurs pour surveiller les **Erreurs SQL**.  
  
 Le tableau suivant décrit les compteurs d' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Erreurs SQL** .  
  
|Compteurs d'erreurs SQL de SQL Server|Description|  
|------------------------------------|-----------------|  
|**Erreurs/s**|Nombre d'erreurs par seconde.|  
  
 Chaque compteur de l'objet contient les instances suivantes :  
  
|Élément|Définition|  
|----------|----------------|  
|**_Total**|Informations sur toutes les erreurs.|  
|**Erreurs de BD hors connexion**|Effectue le suivi des erreurs graves qui amènent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à mettre la base de données actuelle hors ligne.|  
|**Informations sur les erreurs**|Informations relatives aux messages d'erreur qui fournissent des renseignements aux utilisateurs mais qui ne provoquent pas d'erreurs.|  
|**Supprimer les erreurs de connexion**|Effectue le suivi des erreurs graves qui amènent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à mettre fin à la connexion actuelle.|  
|**Erreurs d’utilisateur**|Informations relatives aux erreurs utilisateur.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  
