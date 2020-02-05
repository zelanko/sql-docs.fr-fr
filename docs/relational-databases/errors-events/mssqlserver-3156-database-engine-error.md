---
title: MSSQLSERVER_3156 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8d2c9a265e89ad6c09d89da2e813f9fffbd3379
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68001850"
---
# <a name="mssqlserver_3156"></a>MSSQLSERVER_3156
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|3156|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LDDB_CANT_WRITE|  
|Texte du message|Impossible de restaurer le fichier '%ls' en '%ls'. Pour identifier un emplacement valide pour le fichier, faites appel à WITH MOVE.|  
  
## <a name="explanation"></a>Explication  
Ce message général identifie les noms logiques ou physiques des fichiers qui n'ont pas pu être restaurés en raison d'un problème à l'emplacement spécifié.  
  
### <a name="possible-causes"></a>Causes possibles  
Les raisons peuvent être les suivantes :  
  
-   Vous devez peut-être disposer d'un accès au répertoire Windows spécifié.  
  
-   Vous avez peut-être mal tapé le chemin d'accès ou spécifié un chemin d'accès qui n'existe pas.  
  
-   Le nom du fichier est peut-être utilisé par un fichier qu'il est impossible de remplacer.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Recherchez dans les journaux des erreurs d'autres messages susceptibles de vous fournir plus de détails.  
  
Corrigez le problème à l'emplacement spécifié, notamment en octroyant un accès, ou bien utilisez l'option WITH MOVE de votre instruction RESTORE pour déplacer le fichier.  
  
## <a name="see-also"></a>Voir aussi  
[Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Restaurer des fichiers à un nouvel emplacement &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
