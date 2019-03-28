---
title: Python-to-SQL des types de données - SQL Server Machine Learning
description: Passez en revue les type de données implicites et explicites converstions entre Python et SQL Server dans la science des données et des solutions d’apprentissage.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 6a7cb7e8f93489bb52c1457fbf25bf7206026914
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58509646"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Mappages de types de données entre Python et SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Pour les solutions de Python qui s’exécutent sur la fonctionnalité d’intégration de Python dans SQL Server Machine Learning Services, passez en revue la liste des types de données non pris en charge et les conversions de types de données qui peuvent être effectuées implicitement lorsque les données sont transmises entre Python et SQL Server.

## <a name="python-version"></a>Version de Python

Distribution de SQL Server 2017 Anaconda 4.2 et en Python 3.6.

Un sous-ensemble des fonctionnalités de RevoScaleR (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees, peut-être quelques autres) est fourni à l’aide des API Python, à l’aide d’un nouveau package Python **revoscalepy**. Vous pouvez utiliser ce package fonctionne avec les données à l’aide des trames de données Pandas, les fichiers XDF ou les requêtes de données SQL.

Pour plus d’informations, consultez [module revoscalepy dans SQL Server](ref-py-revoscalepy.md) et [revoscalepy de référence des fonctions](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

Python prend en charge un nombre limité de types de données par rapport à SQL Server. Par conséquent, chaque fois que vous utilisez des données à partir de SQL Server dans les scripts Python, données peuvent être converties implicitement en un type de données compatible. Toutefois, souvent une conversion exacte ne peut pas être effectuée automatiquement, et une erreur est retournée.

## <a name="python-and-sql-data-types"></a>Python et les Types de données SQL

Ce tableau répertorie les conversions implicites qui sont fournies. Autres types de données ne sont pas pris en charge.

|SQLtype|Type de Python|
|-------|-----------|
|**bigint**|`numeric`|
|**binaire**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**Int**|`int32`|
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

