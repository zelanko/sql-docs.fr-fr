---
title: sys.external_library_files (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external_library_files
- external_library_files_TSQL
- sys.external_library_files
- sys.external_library_files_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_library_files catalog view
author: jeannt
ms.author: jeannt
manager: craigg
ms.openlocfilehash: cf8a1b59827c53bc4ae04f76dbe7084a4ad828d4
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2018
---
# <a name="sysexternallibraryfiles-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Répertorie une ligne pour chaque fichier qui compose une bibliothèque externe.

|Nom de colonne |Type de données | Description|
|------|------|-----|
|external_library_id | int |ID de l’objet de bibliothèque externe. |
|content |varbinary(max) |Contenu de l’artefact de fichier de bibliothèque externe. |
|Plateforme |tinyint |ID de la plateforme hôte sur lequel SQL Server est installé. |
|platform_desc | nvarchar(60) |Nom de la plateforme de l’ordinateur hôte. Les valeurs valides sont 'WINDOWS', 'LINUX'. |

### <a name="see-also"></a>Voir aussi  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CRÉER UNE BIBLIOTHÈQUE EXTERNE](../../t-sql/statements/create-external-library-transact-sql.md)  
[Gestion des packages pour le Service SQL Server Machine Learning](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
