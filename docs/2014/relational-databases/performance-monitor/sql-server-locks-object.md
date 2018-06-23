---
title: SQL Server, objet Locks | Microsoft Docs
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
- Locks object
- SQLServer:Locks
ms.assetid: ace04f0d-3993-4444-8317-ca39d7087e49
caps.latest.revision: 22
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 93de00e5129d77379b1575772b20d9c74912660f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36043837"
---
# <a name="sql-server-locks-object"></a>SQL Server, objet Locks
  L'objet **SQLServer:Locks** dans Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit des informations sur les verrous [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans les types de ressources individuels. Des verrous sont placés sur les ressources [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , telles que les lignes lues ou modifiées lors d'une transaction, pour empêcher d'autres transactions d'utiliser simultanément les ressources. Par exemple, si un verrou exclusif (X) est mis en place dans une ligne de table par une transaction, aucune autre transaction ne peut modifier cette ligne jusqu'à ce que le verrou soit débloqué. Un nombre minimal de verrous favorise la concurrence, ce qui peut améliorer les performances. Plusieurs instances de l'objet **Verrous** peuvent être surveillées simultanément, chaque instance représentant un verrou sur un type de ressource.  
  
 Le tableau ci-dessous décrit les compteurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **verrous** .  
  
|Compteurs de verrous de SQL Server|Description|  
|-------------------------------|-----------------|  
|**Temps d'attente moyen (ms)**|Durée d'attente moyenne (en millisecondes) pour chaque demande de verrou qui se termine par une attente.|  
|**Requêtes de verrous/seconde**|Nombre de nouveaux verrous et de conversions de verrous par seconde demandés par le gestionnaire de verrous.|  
|**Expirations de verrouillage (expiration > 0)/s**|Nombre de demandes de verrous par seconde ayant expiré, demandes de verrous NOWAIT exclues.|  
|**Dépassement de l'attente des verrous/seconde**|Nombre de demandes de verrous par seconde ayant expiré, demandes de verrous NOWAIT incluses|  
|**Temps d'attente des verrous (ms)**|Temps d'attente total (en millisecondes) pour les verrous lors de la dernière seconde|  
|**Attente de verrous/seconde**|Nombre de requêtes de verrous par seconde qui ont exigé une attente de l'utilisateur.|  
|**Nombre de blocages/seconde**|Nombre de requêtes de verrous par seconde qui se sont terminées par un blocage.|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut verrouiller ces ressources.  
  
|Élément|Description|  
|----------|-----------------|  
|**_Total**|Informations pour tous les verrous.|  
|**AllocUnit**|Verrou sur une unité d'allocation.|  
|**Application**|Verrou appliqué à une ressource d'application.|  
|**Sauvegarde de la base de données**|Verrou sur une base de données, y compris tous ses objets.|  
|**Extension**|Verrou sur un groupe contigu de 8 pages.|  
|**Fichier**|Verrou sur un fichier de base de données|  
|**Segment de mémoire/BTree**|Segment de mémoire ou BTree (HOBT) Verrou sur un segment de mémoire de pages de données ou sur la structure BTree d'un index|  
|**Clé**|Verrou sur une ligne d'index|  
|**Métadonnées**|Verrou sur une partie des informations de catalogue (appelée également métadonnées).|  
|**Objet**|Verrou sur une table, une procédure stockée, une vue, etc. y compris toutes les données et tous les index. L’objet peut correspondre à tout élément ayant une entrée dans **sys.all_objects**.|  
|**Radiomessagerie**|Verrou sur une page de 8 kilo-octets (Ko) dans une base de données.|  
|**RID**|ID de ligne. Verrou sur une seule ligne dans un segment de mémoire.|  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](monitor-resource-usage-system-monitor.md)  
  
  