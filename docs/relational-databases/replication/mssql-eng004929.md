---
title: MSSQL_ENG004929 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
caps.latest.revision: 14
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b5c41d3ecacd2cb24f6f85cf932e4eca1c1b9b28
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqleng004929"></a>MSSQL_ENG004929
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|4929|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|Impossible de modifier %S_MSG '%.*ls' parce qu’elle est en cours d’édition pour la réplication.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur se produit généralement lorsque vous tentez de supprimer la contrainte de clé primaire d'une table publiée pour la réplication transactionnelle. Comme la réplication transactionnelle nécessite une clé primaire pour chaque table publiée, la contrainte ne peut pas être supprimée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour supprimer la contrainte, commencez par supprimer l'article associé à la table. Pour plus d’informations, consultez [Ajouter et supprimer des articles de publications existantes](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md). Si cette erreur se produit dans une base de données qui n’est pas répliquée, exécutez [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md) pour vérifier que les objets de la base de données ne sont pas marqués comme étant répliqués.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
