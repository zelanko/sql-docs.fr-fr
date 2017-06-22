---
title: MSSQL_ENG014144 | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014144 error
ms.assetid: fdc744d5-530e-48c4-9420-cca032fd482b
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8254c13af6bbdf7843b9c25bf5d1292041478e4e
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng014144"></a>MSSQL_ENG014144
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|14144|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de supprimer l’Abonné '%s'. La base de données de publication '%s' comporte des abonnements qui lui sont associés.|  
  
## <a name="explanation"></a>Explication  
 Une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui est configurée en tant qu'Abonné ne peut pas être supprimée du rôle Abonné tant qu'il y a des abonnements actifs configurés pour l'instance.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Supprimez tous les abonnements associés avant d'essayer de modifier l'état de l'Abonné de l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
1.  Exécutez [sp_helpsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md) dans la base de données de publication sur le serveur de publication pour rechercher des abonnements.  
  
2.  Exécutez [sp_dropsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md) dans la base de données de publication pour supprimer des abonnements.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [S’abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
