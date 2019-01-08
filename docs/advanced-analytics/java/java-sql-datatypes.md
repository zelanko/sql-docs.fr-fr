---
title: Types de données Java pris en charge dans SQL Server 2019 - SQL Server Machine Learning Services
description: Mapper les types de données à partir de Java à SQL Server pour les structures de données d’entrée et de sortie et pour les paramètres d’entrée sur le sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/24/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 6921a40efc9af3ef94c0a53f8409891fee16127e
ms.sourcegitcommit: 85bfaa5bac737253a6740f1f402be87788d691ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2018
ms.locfileid: "53432532"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java et SQL Server pris en charge les types de données

Cet article mappe les types de données de SQL Server aux types de données Java pour les paramètres et les structures de données sur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Types de données pour les jeux de données

Les types de données SQL et Java suivants sont actuellement pris en charge pour les jeux de données d’entrée et de sortie.

| Type SQL        | Type de Java | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | INT      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | Chaîne (unicode)      | | |
| nvarchar (n) | Chaîne (unicode)      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |

## <a name="data-types-for-input-parameters"></a>Types de données pour les paramètres d’entrée

Les types de données SQL et Java suivants sont actuellement pris en charge pour les paramètres d’entrée.

| Type SQL        | Type de Java | | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | INT      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | Chaîne (unicode)      | | |
| nvarchar (n) | Chaîne (unicode)      | | |
| binary(n) | byte[]      | | |
| varbinary (n) | byte[]      | | |
| nvarchar(max) | Chaîne (unicode)      | | |
| varbinary(max) | byte[]      | | |

## <a name="see-also"></a>Voir aussi

+ [L’appel de Java dans SQL Server](howto-call-java-from-sql.md)
+ [Exemple Java dans SQL Server](java-first-sample.md)
+ [Extension de langage Java dans SQL Server](extension-java.md)