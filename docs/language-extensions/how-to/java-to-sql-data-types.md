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
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15'
ms.openlocfilehash: d5703470849f627cca87c471ea666b7c1b0e7e85
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97471740"
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