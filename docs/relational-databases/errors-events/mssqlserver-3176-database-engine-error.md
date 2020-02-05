---
title: MSSQLSERVER_3176 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3176 (Database Engine error)
ms.assetid: 4be24c64-2d52-4cb4-b4d7-36efbe4555b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc01cf250840fb42a8c29525974494a21398e1ff
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68105253"
---
# <a name="mssqlserver_3176"></a>MSSQLSERVER_3176
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|3176|  
|Source de l’événement|MSSQLSERVER|  
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
[Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
[Restaurer des fichiers à un nouvel emplacement &#40;SQL Server&#41;](~/relational-databases/backup-restore/restore-files-to-a-new-location-sql-server.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
