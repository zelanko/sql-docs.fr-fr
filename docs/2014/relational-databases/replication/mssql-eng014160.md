---
title: MSSQL_ENG014160 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014160 error
ms.assetid: d0f3855e-d095-4a81-a5bd-9d7ad51f2c77
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 42f0b6894bac639d287eb62f9870d7bfd6daba3a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62864844"
---
# <a name="mssqleng014160"></a>MSSQL_ENG014160
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14160|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Le seuil [%s:%s] de la publication [%s] a été défini. Un ou plusieurs abonnements à cette publication ont expiré.|  
  
## <a name="explanation"></a>Explication  
 La réplication vous permet d'activer des avertissements pour plusieurs situations. Vous pouvez, entre autres, signaler l'expiration imminente d'un abonnement. Les abonnements peuvent expirer s'ils ne sont pas synchronisés durant une certaine *période de rétention*. Pour plus d’informations, consultez [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
 Lorsque vous activez un avertissement à l'aide du moniteur de réplication ou de la procédure stockée [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), vous spécifiez un seuil qui détermine à quel moment l'avertissement sera déclenché. Quand ce seuil est atteint ou dépassé, un avertissement s'affiche dans le moniteur de réplication et un événement est enregistré dans le journal des événements Windows. Le franchissement d'un seuil peut également déclencher une alerte de l'Agent SQL Server. Pour plus d’informations, consultez [Définir des seuils et des avertissements dans le moniteur de réplication](monitor/set-thresholds-and-warnings-in-replication-monitor.md) et [Surveiller la réplication par programme](monitoring-replication.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 La résolution de ce problème dépend de la raison pour laquelle l'avertissement s'est déclenché :  
  
-   Si le seuil a été dépassé mais que l'abonnement n'a pas encore expiré, synchronisez l'abonnement. Pour plus d’informations, consultez [Synchroniser les données](synchronize-data.md).  
  
-   Si l'agent s'exécute mais qu'il ne réplique pas correctement les modifications, l'abonnement peut expirer. Pour la réplication transactionnelle, assurez-vous que l'Agent de distribution et l'Agent de lecture du journal sont en cours d'exécution. Pour la réplication de fusion, assurez-vous que l'Agent de fusion est en cours d'exécution. Pour plus d’informations sur le démarrage de ces agents, consultez [Démarrer et arrêter un agent de réplication&#40;SQL Server Management Studio&#41;](agents/start-and-stop-a-replication-agent-sql-server-management-studio.md) ou [Concepts des exécutables de l’agent de réplication](concepts/replication-agent-executables-concepts.md).  
  
-   Si l'abonnement a expiré, il doit soit être réinitialisé, soit être supprimé et recréé, suivant le type de l'abonnement et le moment où il a expiré. Pour plus d’informations, consultez [Subscription Expiration and Deactivation](subscription-expiration-and-deactivation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
