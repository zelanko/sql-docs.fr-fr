---
title: Conversions de types de données Python en SQL
description: Passez en revue le type de données implicite et explicite converstions entre Python et SQL Server dans les solutions de science des données et de Machine Learning.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 8aea7e67f6560aa750e67601b5b6a41f7d68b47d
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68470337"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Mappages de types de données entre Python et SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Pour les solutions Python qui s’exécutent sur la fonctionnalité d’intégration python dans SQL Server Machine Learning Services, passez en revue la liste des types de données non pris en charge, ainsi que les conversions de types de données qui peuvent être effectuées implicitement lorsque les données sont transmises entre Python et SQL Server.

## <a name="python-version"></a>Version de Python

SQL Server 2017 Anaconda 4,2 distribution et Python 3,6.

Un sous-ensemble de la fonctionnalité RevoScaleR (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees, peut-être quelques autres) est fourni à l’aide des API Python, à l’aide d’un nouveau package Python **revoscalepy**. Vous pouvez utiliser ce package pour travailler avec des données à l’aide de pandas Data frames, de fichiers XDF ou de requêtes de données SQL.

Pour plus d’informations, consultez [module revoscalepy dans SQL Server](ref-py-revoscalepy.md) et [référence des fonctions revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

Python prend en charge un nombre limité de types de données par rapport à SQL Server. Par conséquent, chaque fois que vous utilisez des données de SQL Server dans des scripts Python, les données peuvent être implicitement converties en un type de données compatible. Toutefois, souvent, une conversion exacte ne peut pas être effectuée automatiquement, et une erreur est retournée.

## <a name="python-and-sql-data-types"></a>Types de données python et SQL

Ce tableau répertorie les conversions implicites qui sont fournies. Les autres types de données ne sont pas pris en charge.

|SQLtype|Type python|
|-------|-----------|
|**bigint**|`numeric`|
|**binaire**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float32`|
|**smallint**|`int16`|
|**tinyint**|`uint8`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|

## <a name="see-also"></a>Voir aussi

