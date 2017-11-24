---
title: MSSQL_ENG021286 | Microsoft Docs
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
caps.latest.revision: "12"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3e5b8c5b4f737d0abe9f8c250bdba72d791c2788
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="mssqleng021286"></a>MSSQL_ENG021286
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Détails du message  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|21286|  
|Source de l'événement|MSSQLSERVER|  
|Composant|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Nom symbolique||  
|Texte du message|La table de conflits '%1!' n'existe pas.|  
  
## <a name="explanation"></a>Explication  
 Cette erreur est générée si la table de conflits d’un article répertorié dans [sysmergearticles &#40;Transact-SQL&#41;](../../relational-databases/system-tables/sysmergearticles-transact-sql.md) n’existe pas. Cette erreur peut se produire lorsque vous tentez d'ajouter ou de supprimer une colonne d'une table publiée pour la réplication de fusion.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) sur la base de données avec la table de conflits manquante pour vérifier qu’il n’existe pas de problèmes de cohérence des données.  
  
 Si la table de conflits n'existe pas sur un Abonné, supprimez l'abonnement puis recréez-le. Si la table des conflits n'existe pas sur un serveur de publication, supprimez tous les abonnement, supprimez la publication puis recréez la publication et tous les abonnements. Pour plus d’informations, consultez [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md) et [S’abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
