---
description: sys.external_library_files (Transact-SQL)
title: sys. external_library_files (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2020
ms.prod: sql
ms.technology: machine-learning
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
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-mi-current||=sqlallproducts-allversions'
ms.openlocfilehash: f0d4ef2a22c2d84030686f13304528c6e7980fc7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88486314"
---
# <a name="sysexternal_library_files-transact-sql"></a>sys.external_library_files (Transact-SQL)  
[!INCLUDE [SQL Server 2017 SQL MI](../../includes/applies-to-version/sqlserver2017-asdbmi.md)]

Répertorie une ligne pour chaque fichier qui compose une bibliothèque externe.

|Nom de la colonne |Type de données |Description|
|------|------|-----|
|external_library_id | int |ID de l’objet de bibliothèque externe. |
|contenu |varbinary(max) |Contenu de l’artefact du fichier de bibliothèque externe. |
|plateforme |TINYINT |ID de la plateforme hôte sur laquelle SQL Server est installé. |
|platform_desc | nvarchar(60) |Nom de la plateforme hôte. Les valeurs valides sont « WINDOWS », « LINUX ». |

### <a name="see-also"></a>Voir aussi  

[sys.external_libraries](sys-external-libraries-transact-sql.md)  
[CRÉER UNE BIBLIOTHÈQUE EXTERNE](../../t-sql/statements/create-external-library-transact-sql.md)  
