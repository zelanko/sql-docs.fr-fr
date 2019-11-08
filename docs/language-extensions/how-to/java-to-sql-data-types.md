---
title: Types de données Java pris en charge dans SQL Server 2019
titleSuffix: SQL Server Language Extensions
description: Mappez les types de données de Java à SQL Server pour les structures de données d’entrée et de sortie ainsi que pour les paramètres d’entrée du script sp_execute_external_script.
author: dphansen
ms.author: davidph
ms.date: 09/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 9daca9c607befe077fcccec20385a36c82b04c6f
ms.sourcegitcommit: a97d551b252b76a33606348082068ebd6f2c4c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "73588833"
---
# <a name="java-and-sql-server-supported-data-types"></a>Types de données pris en charge par Java et SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cet article mappe les types de données SQL Server aux types de données Java pour les structures de données et les paramètres dans [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql).

Les types de données SQL et Java suivants sont pris en charge pour les jeux de données d’entrée/de sortie ainsi que pour les paramètres d’entrée/de sortie.

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
| char(n) | String | Seules les chaînes UTF8 sont prises en charge | |
| varchar(n) | String | Seules les chaînes UTF8 sont prises en charge | |
| varchar(max) | String | Seules les chaînes UTF8 sont prises en charge | |
| Date | java.sql.date  | | |
| NUMERIC | java.math.BigDecimal  | | |
| Décimal | java.math.BigDecimal  | | |
| money | java.math.BigDecimal  | | |
| SMALLMONEY | java.math.BigDecimal  | | |
| smalldatetime | java.sql.timestamp  | | |
| DATETIME | java.sql.timestamp  | | |
| datetime2 | java.sql.timestamp  | | |


## <a name="next-steps"></a>Étapes suivantes

+ [Guide pratique pour appeler Java dans SQL Server](../how-to/call-java-from-sql.md)
