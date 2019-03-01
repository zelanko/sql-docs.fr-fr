---
title: sys.external_libraries (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- external_libraries
- external_libraries_TSQL
- sys.external_libraries
- sys.external_libraries_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.external_libraries catalog view
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3a2f83d703566ae5a60fd027ff7f186205a0c404
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017535"
---
# <a name="sysexternallibraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

Prend en charge la gestion des bibliothèques de package liés aux runtimes externes tels que R, Python et Java.

> [!NOTE]
> Dans SQL Server 2017, le langage R et la plateforme de Windows sont prises en charge. R, Python et Java sur la plateforme Windows sont prises en charge dans SQL Server 2019 CTP 2.3. Prise en charge pour Linux est prévue pour une version ultérieure.

## <a name="sysexternallibraries"></a>sys.external_libraries

Le sys.external_libraries de vue de catalogue répertorie une ligne pour chaque bibliothèque externe qui a été téléchargé dans la base de données.

|Nom de colonne |Type de données | Description|
|------|------|------|
|external_library_id |INT | ID de l’objet de bibliothèque externe. |
|NAME |sysname |Nom de la bibliothèque externe. Est unique au sein de la base de données par le propriétaire.|
|principal_id |INT |ID du principal qui possède cette bibliothèque externe. |
|langue | sysname | Nom de la langue ou le runtime qui prend en charge de la bibliothèque externe. Les valeurs valides sont « R », « Python » et « Java ». Runtimes supplémentaires peuvent être ajoutées dans les futures.|
|portée |INT |0 pour une étendue publique ; 1 pour l’étendue privée |  
|scope_desc |varchar(7) |Indique si le package est public ou privé|

## <a name="see-also"></a>Voir aussi  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [CRÉER UNE BIBLIOTHÈQUE EXTERNE](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Installer de nouveaux packages R sur SQL Server](../../advanced-analytics/r/install-additional-r-packages-on-sql-server.md)  
+ [Installer de nouveaux packages Python sur SQL Server](../../advanced-analytics/python/install-additional-python-packages-on-sql-server.md)  