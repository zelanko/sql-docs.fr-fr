---
title: MSSQL_ENG021385 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG021385 error
ms.assetid: a2c0444f-d97b-4760-8905-3574791c2e26
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ecee28d25ede6e64dcd94d184f01ede60783009a
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqleng021385"></a>MSSQL_ENG021385
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21385|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|L'instantané n'a pas réussi à traiter la publication '%1!'. L'incident peut être dû à une activité de changement de schéma actif ou à l'ajout de nouveaux articles.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur est générée si l'Agent d'instantané démarre au moment où des modifications de la base de données de publication sont en cours, par exemple l'ajout ou la suppression d'articles ou des modifications de schéma sur des objets publiés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Redémarrez l'Agent d'instantané au terme de la modification de la base de données de publication. Pour plus d’informations, consultez [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) et [Concepts des exécutables de l’agent de réplication](../../relational-databases/replication/concepts/replication-agent-executables-concepts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
