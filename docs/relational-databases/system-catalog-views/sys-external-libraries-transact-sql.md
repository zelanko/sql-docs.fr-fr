---
title: sys. external_libraries (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
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
ms.openlocfilehash: 6b1bfc00b403fa76f692db78593ed4c0e6b53ce8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "80664435"
---
# <a name="sysexternal_libraries-transact-sql"></a>sys.external_libraries (Transact-SQL)  
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

Prend en charge la gestion des bibliothèques de packages relatives aux runtimes externes tels que R, Python et Java.

> [!NOTE]
> Dans SQL Server 2017, le langage R et la plateforme Windows sont pris en charge. R, Python et Java sur les plateformes Windows et Linux sont pris en charge dans SQL Server 2019 et ultérieur.

## <a name="sysexternal_libraries"></a>sys.external_libraries

L’affichage catalogue sys. external_libraries répertorie une ligne pour chaque bibliothèque externe qui a été chargée dans la base de données.

|Nom de la colonne |Type de données | Description|
|------|------|------|
|external_library_id |int | ID de l’objet de bibliothèque externe. |
|name |sysname |Nom de la bibliothèque externe. Est unique dans la base de données par propriétaire.|
|principal_id |int |ID du principal propriétaire de cette bibliothèque externe. |
|langage | sysname | Nom de la langue ou du runtime qui prend en charge la bibliothèque externe. Les valeurs valides sont « R », « Python » et « Java ». Des runtimes supplémentaires peuvent être ajoutés à l’avenir.|
|scope |int |0 pour l’étendue publique ; 1 pour l’étendue privée |  
|scope_desc |varchar (7) |Indique si le package est public ou privé|

## <a name="see-also"></a>Voir aussi  

+ [sys.external_library_files](sys-external-library-files-transact-sql.md)  
+ [CRÉER UNE BIBLIOTHÈQUE EXTERNE](../../t-sql/statements/create-external-library-transact-sql.md)  
+ [Installer de nouveaux packages R sur SQL Server](../../machine-learning/package-management/install-additional-r-packages-on-sql-server.md)  
+ [Installer de nouveaux packages Python sur SQL Server](../../machine-learning/package-management/install-additional-python-packages-on-sql-server.md)  