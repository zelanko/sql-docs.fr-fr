---
title: Sys.external_libraries (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 10/05/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.external_libraries catalog view
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.openlocfilehash: bb229022bcccfb9cdc8c419844d30335337575d4
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="sysexternallibraries-transact-sql"></a>Sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]


Prend en charge la gestion des bibliothèques de package liés à des runtimes externes tels que R ou Python.

## <a name="sysexternallibraries"></a>Sys.external_libraries

Le sys.external_libraries de vue de catalogue répertorie une ligne pour chaque bibliothèque externe qui a été téléchargé dans la base de données.

|Nom de colonne |Type de données |  Description|
|------|------|------|
|external_library_id |int | ID de l’objet de bibliothèque externe. |
|name |sysname |Nom de la bibliothèque externe. Est unique dans la base de données par le propriétaire.|
|principal_id |int |ID du principal qui possède cette bibliothèque externe. |
|langue | sysname | Nom de la langue ou le runtime qui prend en charge de la bibliothèque externe. Les valeurs valides sont « R ». Les runtimes supplémentaires peuvent être ajoutées dans les futures.|
|portée |int |0 pour une portée publique ; 1 pour la portée privée |  
|scope_desc |varchar(7) |Indique si le package est public ou privé|


## <a name="see-also"></a>Voir aussi  
[sys.external_library_files](sys-external-library-files-transact-sql.md)  
[CRÉER UNE BIBLIOTHÈQUE EXTERNE](../../t-sql/statements/create-external-library-transact-sql.md)  
[Gestion des packages pour SQL Server R Services](../../advanced-analytics/r/installing-and-managing-r-packages.md)  
