---
title: MSSQLSERVER_3156 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3156 (Database Engine error)
ms.assetid: 345d8ed4-177e-4ec3-bab3-25d30000e323
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2b1c972481b7c4cf614cf0a91b29247c643696d2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62868921"
---
# <a name="mssqlserver_3156"></a>MSSQLSERVER_3156
    
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
 [Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Restaurer les fichiers à un nouvel emplacement &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
