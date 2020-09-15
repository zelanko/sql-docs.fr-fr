---
title: Convertir les types de données SQL et Python
description: Passez en revue les conversions de types de données implicites et explicites entre Python et SQL Server dans les solutions de science des données et d’apprentissage automatique.
ms.prod: sql
ms.technology: machine-learning-services
ms.date: 06/30/2020
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: ee493ec09c5cfc8a5198239cd5cafcb2579f50d8
ms.sourcegitcommit: 9b41725d6db9957dd7928a3620fe4db41eb51c6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88178620"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Mappages de types de données entre Python et SQL Server
[!INCLUDE [SQL Server 2017 and later](../../includes/applies-to-version/sqlserver2017.md)]

Pour les solutions Python qui s’exécutent sur la fonctionnalité d’intégration Python dans SQL Server Machine Learning Services, passez en revue la liste des types de données non pris en charge, ainsi que les conversions de types de données qui peuvent être effectuées implicitement lorsque les données sont transmises entre Python et SQL Server.

## <a name="python-version"></a>Version Python

Un sous-ensemble de la fonctionnalité RevoScaleR (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees et éventuellement d’autres) est fourni à l’aide des API Python, via un nouveau package Python **revoscalepy**. Vous pouvez utiliser ce package pour travailler avec des données à l’aide de trames de données Pandas, fichiers XDF ou requêtes de données SQL.

Pour plus d’informations, consultez le [module revoscalepy dans SQL Server](ref-py-revoscalepy.md) et la [référence de fonction revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

Python prend en charge un nombre limité de types de données par rapport à SQL Server. Par conséquent, chaque fois que vous utilisez des données de SQL Server dans des scripts Python, les données peuvent être implicitement converties en un type de données compatible. Toutefois, la plupart du temps, une conversion exacte ne peut pas être effectuée automatiquement et une erreur est renvoyée.

## <a name="python-and-sql-data-types"></a>Type de données Python et SQL

Ce tableau répertorie les conversions implicites qui sont fournies. Les autres types de données ne sont pas pris en charge.

|SQLtype|Type Python|Description
|-------|-----------|---------------------------------------------------------------------------------------------|
|**bigint**|`float64`|
|**binary**|`bytes`|
|**bit**|`bool`|
|**char**|`str`|
|**date**|`datetime`|
|**datetime**|`datetime`|Pris en charge avec SQL Server 2017 CU6 et versions ultérieures (avec des tableaux **NumPy** de type `datetime.datetime` ou `pandas.Timestamp` **Pandas**). `sp_execute_external_script` gère maintenant les types `datetime` comportant des fractions de secondes.|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float64`|
|**smalldatetime**|`datetime`|
|**smallint**|`int32`|
|**tinyint**|`int32`|
|**uniqueidentifier**|`str`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|
