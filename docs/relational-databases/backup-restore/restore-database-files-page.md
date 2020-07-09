---
title: Restaurer la base de données (page Fichiers) | Microsoft Docs
description: Lors de la restauration d’une base de données dans SQL Server, utilisez la boîte de dialogue Restaurer la base de données pour gérer les fichiers à restaurer au sein de la base de données.
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.restoredb.files.f1
- sql13.swb.restoredb.files.f1 in the code
ms.assetid: 714c36ea-a9f9-43a4-99f9-a6f73d1baf8e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ab1cedc6960052ec8a9007b72d9062b8fc818ab7
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737727"
---
# <a name="restore-database-files-page"></a>Restaurer la base de données (page Fichiers)
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  Utilisez la page **Fichiers** de la boîte de dialogue **Restaurer la base de données** pour gérer les fichiers spécifiques que vous avez choisi de restaurer dans la base de données.  
  
## <a name="options"></a>Options  
  
### <a name="restore-database-files-as"></a>Restaurer les fichiers de la base de données en tant que  
 Utilisez cette option pour affecter et gérer le nouveau chemin d'accès relatif aux fichiers restaurés.  
  
 **Déplacer tous les fichiers dans le dossier**  
 Déplace des fichiers restaurés.  
  
|Option|Description|  
|------------|-----------------|  
|**Dossier des fichiers de données**|Entrez ou recherchez le nom du dossier des fichiers de données vers lequel le fichier de données restauré ou les fichiers doivent être déplacés.|  
|**Dossier des fichiers journaux**|Entrez ou recherchez le fichier journal ou le dossier de fichiers vers lequel le fichier journal restauré doit être déplacé.|  
  
 **Nom du fichier logique**  
 Affichages une ligne pour chaque fichier de base de données à restaurer.  
  
 **Type de fichier**  
 Affiche le type de fichier.  
  
 **Nom du fichier d'origine**  
 Affiche le chemin d'accès de fichier d'origine pour le fichier restauré.  
  
 **Restaurer sous**  
 Répertorie les noms de fichier sous lesquels les fichiers restaurés seront enregistrés. Entrez ou recherchez le nom de fichier approprié.  
  
## <a name="see-also"></a> Voir aussi  
 [Restaurer la base de données &#40;page Général&#41;](../../relational-databases/backup-restore/restore-database-general-page.md)   
 [Restaurer la base de données &#40;page Options&#41;](../../relational-databases/backup-restore/restore-database-options-page.md)   
 [Arguments RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-arguments-transact-sql.md)   
 [Définir une unité de sauvegarde logique pour un lecteur de bande &#40;SQL Server&#41;](../../relational-databases/backup-restore/define-a-logical-backup-device-for-a-tape-drive-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
