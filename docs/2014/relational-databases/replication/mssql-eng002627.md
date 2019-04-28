---
title: MSSQL_ENG002627 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG002627 error
ms.assetid: 7f4136ac-3784-4a41-a98c-8a02308e4883
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a102991d08085f093e08a068a3d3127c9d7f7fc6
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62666695"
---
# <a name="mssqleng002627"></a>MSSQL_ENG002627
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2627|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique|N/A|  
|Texte du message|Violation de la contrainte '%.*ls'. Impossible d’insérer une clé en double dans l’objet '%.\*ls'.|  
  
## <a name="explanation"></a>Explication  
 C'est une erreur générale qui peut être déclenchée qu'une base de données soit répliquée ou non. Dans les bases de données répliquées, l'erreur est généralement déclenchée car les clés primaires n'ont pas été gérés de manière appropriée à travers la topologie. Dans un environnement distribué, il est primordial de s'assurer que la même valeur n'est pas insérée dans une colonne de clé primaire ou toute autre colonne unique sur plus d'un seul nœud. Les raisons peuvent être les suivantes :  
  
-   Les insertions et mises à jour sur une ligne se produisent sur plus d'un seul nœud. La réplication de fusion et les abonnements pouvant être mis à jour pour la réplication transactionnelle permettent tous deux la détection et la résolution des conflits, mais il est quand même préférable de n'insérer ou de ne mettre à jour une ligne donnée que sur un seul nœud. La réplication transactionnelle d'égal à égal ne permet pas la détection et la résolution des conflits, elle nécessite que les insertions et mises à jour soient partitionnées.  
  
-   Une ligne a été insérée sur un abonné qui devrait être en lecture seule. Les abonnés aux publications d'instantanés, ainsi que les abonnés au publications transactionnelles devraient être traités comme étant en lecture seule à moins d'utiliser des abonnements pouvant être mis à jour ou la réplication transactionnelle d'égal à égal.  
  
-   Une table avec une colonne d'identité est utilisée, mais la colonne n'est par gérée de façon appropriée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 L'action requise dépend de la raison du déclenchement de l'erreur :  
  
-   Les insertions et mises à jour sur une ligne se produisent sur plus d'un seul nœud.  
  
     Quel que soit le type de réplication utilisé, il est recommandé de partitionner les insertions et mises à jour chaque fois que cela est possible, car cela réduit le traitement nécessaire pour la détection et la résolution des conflits. Pour la réplication transactionnelle d'égal à égal, le partitionnement d'insertions et de mises à jour est nécessaire. Pour plus d'informations, consultez [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).  
  
-   Une ligne a été insérée sur un abonné qui devrait être en lecture seule.  
  
     N'insérez pas ou ne mettez pas à jour de lignes sur l'Abonné à moins d'utiliser la réplication de fusion, la réplication transactionnelle avec abonnements pouvant être mis à jour ou la réplication transactionnelle d'égal à égal.  
  
-   Une table avec une colonne d'identité est utilisée, mais la colonne n'est par gérée de façon appropriée.  
  
     Pour la réplication de fusion et la réplication transactionnelle avec abonnements pouvant être mis à jour, les colonnes d'identité doivent être gérées automatiquement par la réplication. Pour la réplication transactionnelle d'égal à égal, elles doivent être gérées manuellement. Pour plus d’informations, consultez [ Répliquer des colonnes d’identité](publish/replicate-identity-columns.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)   
 [Réplication de fusion](merge/merge-replication.md)   
 [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md)   
 [Abonnements pouvant être mis à jour pour la réplication transactionnelle](transactional/updatable-subscriptions-for-transactional-replication.md)  
  
  
