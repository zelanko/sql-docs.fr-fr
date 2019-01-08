---
title: MSSQL_ENG021286 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 54e5d7b496affcd6d9ead2c50f50e807e7e920a7
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52793571"
---
# <a name="mssqleng021286"></a>MSSQL_ENG021286
    
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
 Cette erreur est générée si la table de conflits d’un article répertorié dans [sysmergearticles &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/sysmergearticles-transact-sql) n’existe pas. Cette erreur peut se produire lorsque vous tentez d'ajouter ou de supprimer une colonne d'une table publiée pour la réplication de fusion.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Exécutez [DBCC CHECKDB &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) sur la base de données avec la table de conflits manquante pour vérifier qu’il n’existe pas de problèmes de cohérence des données.  
  
 Si la table de conflits n'existe pas sur un Abonné, supprimez l'abonnement puis recréez-le. Si la table des conflits n'existe pas sur un serveur de publication, supprimez tous les abonnement, supprimez la publication puis recréez la publication et tous les abonnements. Pour plus d’informations, consultez [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md) et [S’abonner à des publications](subscribe-to-publications.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des événements &#40;réplication&#41;](errors-and-events-reference-replication.md)  
  
  
