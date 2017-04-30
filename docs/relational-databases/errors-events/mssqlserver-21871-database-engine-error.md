---
title: MSSQLSERVER_21871 | Microsoft Docs
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
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1538eba494fcad374dd0454ed519777466317b0f
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21871|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|SQLErrorNum21871|  
|Texte du message|Le serveur de publication %s de la base de données %s n'a pas été redirigé.|  
  
## <a name="explanation"></a>Explication  
**sp_validate_replica_hosts_as_publishers** recherche dans la table MSredirected_publishers de la base de données de distribution une entrée pour le serveur de publication et la base de données du serveur de publication identifiés.  **sp_validate_replica_hosts_as_publishers** retourne l’erreur 21871 quand aucune entrée n’est trouvée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
**sp_validate_replica_hosts_as_publishers** est applicable uniquement aux serveurs de publication redirigés. Si la base de données du serveur de publication est membre d’un groupe de disponibilité, utilisez la procédure stockée **sp_redirect_publisher** pour associer le serveur de publication et la base de données du serveur de publication au nom de l’écouteur du groupe de disponibilité.  
  

