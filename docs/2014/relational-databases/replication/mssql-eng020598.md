---
title: MSSQL_ENG020598 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cc42ea107ac08c22e98ccc3ac15b55c5604a3784
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62938529"
---
# <a name="mssql_eng020598"></a>MSSQL_ENG020598
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|20598|  
|Source de l’événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|La ligne n'a pas été trouvée chez l'Abonné lorsque la commande répliquée est appliquée.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur est générée dans la réplication transactionnelle lorsque l'Agent de distribution tente de mettre à jour sur l'Abonné, mais que la ligne a été supprimée ou que la clé primaire de la ligne a été modifiée. Par défaut, les Abonnés à des publications transactionnelles doivent être traités en lecture seule, parce que les changements ne sont pas propagés vers le serveur de publication. Dans le cas de la réplication transactionnelle, les modifications des utilisateurs doivent être effectuées sur l'Abonné, uniquement si les abonnements devant être mis à jour ou la réplication d'égal à égal sont utilisés. Pour plus d'informations sur ces options, consultez [Updatable Subscriptions for Transactional Replication](transactional/updatable-subscriptions-for-transactional-replication.md) et [Peer-to-Peer Transactional Replication](transactional/peer-to-peer-transactional-replication.md).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 **Pour rectifier ce problème :**  
  
1.  Si la réplication doit continuer pendant que vous identifiez la source de l’erreur, spécifiez le paramètre **-SkipErrors 20598** pour l’Agent de distribution. L'agent peut alors ignorer les modifications qui provoquent l'erreur 20598, tout en permettant la réplication des autres modifications.  
  
2.  Identifiez sur l'Abonné les modifications qui ont été supprimées ou qui comportent une clé primaire différente de celle des lignes correspondantes sur le serveur de publication. Vous pouvez utiliser l' [tablediff Utility](../../tools/tablediff-utility.md) pour déterminer les lignes qui sont différentes dans les bases de données de publication et d'abonnement. Pour obtenir des informations sur l’utilisation de cet utilitaire avec des bases de données répliquées, consultez [Comparer des tables répliquées pour identifier les différences &#40;programmation de la réplication&#41;](administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
3.  Corrigez les lignes sur l'Abonné à l'aide de l'utilitaire **tablediff** ou d'une autre méthode.  
  
4.  (Facultatif) Supprimez le paramètre **-SkipErrors** .  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
