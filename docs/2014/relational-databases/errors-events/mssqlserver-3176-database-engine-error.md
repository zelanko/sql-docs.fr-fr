---
title: MSSQLSERVER_3176 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 4d9c0da49aaf3f2cb8d55bf63923d6f718ff26f4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36141811"
---
# <a name="mssqlserver3176"></a>MSSQLSERVER_3176
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|3176|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LDDB_FILE_CLAIM|  
|Texte du message|Le fichier '%ls' est revendiqué par '%ls'(%d) et '%ls'(%d). La clause WITH MOVE peut être utilisée pour déplacer un ou plusieurs fichiers.|  
  
## <a name="explanation"></a>Explication  
 Tentative d'utilisation d'un fichier dans plusieurs buts.  
  
### <a name="possible-causes"></a>Causes possibles  
 Une autre base de données utilise déjà le nom de fichier.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Restaurez les fichiers de la base de données à un emplacement différent. Dans une instruction RESTORE, utilisez une clause WITH MOVE pour déplacer chaque fichier. Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], modifiez les emplacements des fichiers dans la grille **Restaurer les fichiers de la base de données en tant que** de la boîte de dialogue **Options de restauration de la base de données**.  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Restaurer les fichiers vers un nouvel emplacement &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
