---
title: MSSQLSERVER_2527 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: errors-events
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4bdf98e0beaed65cac6cd792646bf7441ee5d4fd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="mssqlserver2527"></a>MSSQLSERVER_2527
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|2527|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_INDEX_FILEGROUP_IS_OFFLINE|  
|Texte du message|Impossible de traiter l'index I_NAME de la table O_NAME car le groupe de fichiers F_NAME est hors connexion.|  
  
## <a name="explanation"></a>Explication  
Ce message d'information indique qu'il est impossible de vérifier l'index, car l'un des groupes de fichiers qui stocke les données de l'index n'est pas connecté. L'état des fichiers dans un groupe de fichiers détermine la disponibilité du groupe de fichiers tout entier. Pour qu'un groupe de fichiers soit disponible, tous ses fichiers doivent être en ligne. S’il n’y a pas d’autre problème, tous les autres index du même objet seront vérifiés.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Pour afficher l’état des fichiers du groupe de fichiers spécifié, interrogez l’affichage catalogue **sys.database_files** ou **sys.master_files**.  
  
Restaurez le fichier hors connexion à partir d'une sauvegarde.  
  
## <a name="see-also"></a> Voir aussi  
[sys.database_files &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[sys.master_files &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
