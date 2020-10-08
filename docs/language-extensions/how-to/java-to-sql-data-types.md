---
title: Types de données Java
titleSuffix: SQL Server Language Extensions
description: Mappez les types de données de Java à SQL Server pour les structures de données d’entrée et de sortie ainsi que pour les paramètres d’entrée du script sp_execute_external_script.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 742eeac8d1255f02571f6a1e77d20cb0d8084fe3
ms.sourcegitcommit: 346a37242f889d76cd783f55aeed98023c693610
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765756"
---
# <a name="java-and-sql-server-supported-data-types"></a>Types de données pris en charge par Java et SQL Server
[!INCLUDE [SQL Server 2019 and later](../../includes/applies-to-version/sqlserver2019.md)]

Cet article mappe les types de données SQL Server aux types de données Java pour les structures de données et les paramètres dans [sp_execute_external_script](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md).

Les types de données SQL et Java suivants sont pris en charge pour les jeux de données d’entrée/de sortie ainsi que pour les paramètres d’entrée/de sortie.

| Type de données SQL        | Type de données Java | Commentaire |
| ------------- |-------------|-|
| bit      | boolean | |
| Tinyint      | short      | |
| Smallint | short      | |
| Int | int      | |
| Real | float      | |
| Bigint | long      | |
| float | double      | |
| nchar(n) | String      | |
| nvarchar(n) | String      | |
| binary(n) | byte[]      | |
| varbinary(n) | byte[]      | |
| nvarchar(max) | String      | |
| varbinary(max) | byte[]      | |
| UNIQUEIDENTIFIER | String | |
| char(n) | String | Seules les chaînes UTF8 sont prises en charge |
| varchar(n) | String | Seules les chaînes UTF8 sont prises en charge |
| varchar(max) | String | Seules les chaînes UTF8 sont prises en charge |
| Date | java.sql.date  | |
| numeric | java.math.BigDecimal  | |
| Décimal | java.math.BigDecimal  | |
| money | java.math.BigDecimal  | |
| SMALLMONEY | java.math.BigDecimal  | |
| smalldatetime | java.sql.timestamp  | |
| DATETIME | java.sql.timestamp  | |
| datetime2 | java.sql.timestamp  | |


## <a name="next-steps"></a>Étapes suivantes

+ [Guide pratique pour appeler Java dans SQL Server](../how-to/call-java-from-sql.md)