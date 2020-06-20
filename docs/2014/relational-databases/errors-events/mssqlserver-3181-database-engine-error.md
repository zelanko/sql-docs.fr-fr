---
title: MSSQLSERVER_3181 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3181 (Database Engine error)
ms.assetid: e6d2e716-5263-477c-ad0e-7bcbfef4c1f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f18509d9a18ba8be1f4e40c93bff5abfcae3d69c
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053990"
---
# <a name="mssqlserver_3181"></a>MSSQLSERVER_3181
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID de l’événement|3181|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|LDDB_STORAGE_VERIFY|  
|Texte du message|La restauration de cette sauvegarde risque de rencontrer des problèmes d'espace de stockage. D'autres messages fourniront des détails.|  
  
## <a name="explanation"></a>Explication  
 L'instruction RESTORE VERIFYONLY vérifie l'espace de stockage disponible sur le disque sur lequel la base de données doit être restaurée.  
  
### <a name="possible-causes"></a>Causes possibles  
 L'espace disque disponible est peut-être insuffisant pour restaurer la sauvegarde en cours de vérification.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Restaurez la sauvegarde à un emplacement doté de suffisamment d'espace disque ou prévoyez plus d'espace sur le disque.  
  
## <a name="see-also"></a>Voir aussi  
 [Restaurer une base de données à un nouvel emplacement &#40;SQL Server&#41;](../backup-restore/restore-a-database-to-a-new-location-sql-server.md)   
 [Restaurer les fichiers à un nouvel emplacement &#40;SQL Server&#41;](../backup-restore/restore-files-to-a-new-location-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql)  
  
  
