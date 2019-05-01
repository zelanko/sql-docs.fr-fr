---
title: Types de données Java pris en charge dans SQL Server 2019 - Extensions de langage SQL Server
description: Mapper les types de données à partir de Java à SQL Server pour les structures de données d’entrée et de sortie et pour les paramètres d’entrée sur le sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/23/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 14a2bc5594b16610dfb8278ab82a9e7b8b22fea6
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473595"
---
# <a name="java-and-sql-server-supported-data-types"></a>Java et SQL Server pris en charge les types de données

Cet article mappe les types de données de SQL Server aux types de données Java pour les paramètres et les structures de données sur [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

## <a name="data-types-for-data-sets"></a>Types de données pour les jeux de données

Les types de données SQL et Java suivants sont actuellement pris en charge pour les jeux de données d’entrée et de sortie.


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

## <a name="next-steps"></a>Étapes suivantes

+ [L’appel de Java dans SQL Server](howto-call-java-from-sql.md)
+ [Exemple Java dans SQL Server](java-first-sample.md)
+ [Extension de langage Java dans SQL Server](extension-java.md)
