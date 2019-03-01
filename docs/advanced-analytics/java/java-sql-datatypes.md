---
title: Types de données Java pris en charge dans SQL Server 2019 - SQL Server Machine Learning Services
description: Mapper les types de données à partir de Java à SQL Server pour les structures de données d’entrée et de sortie et pour les paramètres d’entrée sur le sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 02/28/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 4c0f691b8bb389c2da2001d19f0684b7f928f707
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57017815"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java et SQL Server pris en charge les types de données

Cet article mappe les types de données de SQL Server aux types de données Java pour les paramètres et les structures de données sur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Types de données pour les jeux de données

Les types de données SQL et Java suivants sont actuellement pris en charge pour les jeux de données d’entrée et de sortie.

| Type de données SQL        | Type de données Java | Commentaire | |
| ------------- |-------------|-|
| bit      | boolean | |
| Tinyint      | short      | |
| Smallint | short      | |
| Int | INT      | |
| Real | FLOAT      | |
| Bigint | long      | |
| FLOAT | double      | |
| nchar(n) | String      | |
| nvarchar(n) | String  | |
| binary(n) | byte[]      | |
| varbinary(n) | byte[]      | |
| nvarchar(max) | String | |
| varbinary(max) | byte[] | |
| UNIQUEIDENTIFIER | String | |
| char(n) | String | Seules les chaînes UTF8 pris en charge |
| varchar(n) | String | Seules les chaînes UTF8 pris en charge |
| varchar(max) | String | Seules les chaînes UTF8 pris en charge |

## <a name="data-types-for-input-parameters"></a>Types de données pour les paramètres d’entrée

Les types de données SQL et Java suivants sont actuellement pris en charge pour les paramètres d’entrée.

| Type de données SQL        | Type de données Java | Commentaire | |
| ------------- |-------------|-|-|
| bit      | boolean | | |
| Tinyint      | short      | | |
| Smallint | short      | | |
| Int | INT      | | |
| Real | FLOAT      | | |
| Bigint | long      | | |
| FLOAT | double      | | |
| nchar(n) | String      | | |
| nvarchar(n) | String      | | |
| binary(n) | byte[]      | | |
| varbinary(n) | byte[]      | | |
| nvarchar(max) | String      | | |
| varbinary(max) | byte[]      | | |
| UNIQUEIDENTIFIER | String | | |
| char(n) | String | Seules les chaînes UTF8 pris en charge | |
| varchar(n) | String | Seules les chaînes UTF8 pris en charge | |
| varchar(max) | String | Seules les chaînes UTF8 pris en charge | |

## <a name="see-also"></a>Voir aussi

+ [L’appel de Java dans SQL Server](howto-call-java-from-sql.md)
+ [Exemple Java dans SQL Server](java-first-sample.md)
+ [Extension de langage Java dans SQL Server](extension-java.md)