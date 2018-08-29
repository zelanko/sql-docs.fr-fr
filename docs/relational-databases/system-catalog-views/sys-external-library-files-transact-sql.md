---
title: Sys.external_library_files (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/05/2017
ms.prod: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4ef3ef80905277660af98597cca77132c39222b1
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43085162"
---
# <a name="sysexternallibraryfiles-transact-sql"></a>Sys.external_library_files (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Répertorie une ligne pour chaque fichier qui compose une bibliothèque externe.

|Nom de colonne |Type de données |Description|
|------|------|-----|
|external_library_id | INT |ID de l’objet de bibliothèque externe. |
|content |varbinary(max) |Contenu de l’artefact de fichier de bibliothèque externe. |
|Plateforme |TINYINT |ID de la plateforme hôte sur lequel SQL Server est installé. |
|platform_desc | nvarchar(60) |Nom de la plateforme hôte. Les valeurs valides sont « WINDOWS », « LINUX ». |

### <a name="see-also"></a>Voir aussi  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CRÉER UNE BIBLIOTHÈQUE EXTERNE](../../t-sql/statements/create-external-library-transact-sql.md)  
[Gestion des packages pour le Service SQL Server Machine Learning](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
