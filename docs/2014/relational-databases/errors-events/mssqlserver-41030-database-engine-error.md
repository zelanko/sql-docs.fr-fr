---
title: MSSQLSERVER_41030 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 015a01f849bb00dd0db4c2f060447d63a2f96bc6
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62914071"
---
# <a name="mssqlserver_41030"></a>MSSQLSERVER_41030
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|41030|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|OPEN_CLUSTER_SUB_KEY|  
|Texte du message|Échec de l'ouverture de la sous-clé de Registre de clustering de basculement Windows Server « %.*ls » (code d'erreur %d).  La clé parente est la clé racine de cluster.  Le service WSFC n'est peut-être pas en cours d'exécution ou n'est pas disponible dans son état actuel, ou les arguments spécifiés ne sont pas valides. Si le groupe de disponibilité correspondant a été supprimé, cette erreur est attendue. Pour plus d'informations sur ce code d'erreur, consultez « codes d'erreur système » dans la documentation relative au développement Windows.|  
  
## <a name="explanation"></a>Explication  
 Si un cluster WSFC est détruit, toutes les clés de Registre associées à [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] sont supprimées.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Après recréation d'un cluster WSFC, désactivez et réactivez ensuite AlwaysOn sur chaque nœud de cluster sur lequel une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est activée pour AlwaysOn. Vous pouvez utiliser le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour cette tâche.  
  
## <a name="see-also"></a>Voir aussi  
 [Activer et désactiver les groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)   
 [Clustering de basculement Windows Server &#40;WSFC&#41; avec SQL Server](../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
  
