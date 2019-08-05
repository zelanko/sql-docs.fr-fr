---
title: MSSQL_ENG021286 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021286 error
ms.assetid: b63620b7-1c6d-46f7-90ea-3a8e99af8de4
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 3c19dee32a305bdd41e2918ba35f246fef558926
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770330"
---
# <a name="mssqleng021286"></a>MSSQL_ENG021286
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
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
  
  
