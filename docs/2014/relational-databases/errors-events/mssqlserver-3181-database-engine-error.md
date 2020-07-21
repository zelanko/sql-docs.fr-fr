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
ms.openlocfilehash: 3aca70f5f13ba81ae240abcc1e63fdf60b31e72d
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551764"
---
# <a name="mssqlserver_3181"></a>MSSQLSERVER_3181
    
## <a name="details"></a>Détails  
  
|Attribut|Valeur|  
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
  
  
