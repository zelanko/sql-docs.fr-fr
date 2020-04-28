---
title: Types de données dans Analysis Services | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 910be4f4-3010-41cd-9fdc-f0a79a0ce823
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4ecdc64918e582f25f0e017d263c66e78c0d1bee
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62725383"
---
# <a name="data-types-in-analysis-services"></a>Types de données dans Analysis Services
  Pour tous <xref:Microsoft.AnalysisServices.DataItem> les objets [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , prend en charge le `System.Data.OleDb.OleDbType`sous-ensemble suivant de. Pour définir ou lire le type de données, utilisez le [type de données DataItem &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/data-type/dataitem-data-type-assl).  
  
## <a name="supported-data-types"></a>Types de données pris en charge  
  
|||  
|-|-|  
|BigInt|Entier signé de 64 bits. Le type valeur *bigint* représente des entiers dont les valeurs sont comprises entre un 9223372036854775808 négatif et un 9 223 372 036 854 775 807 positif.|  
|Binary|Flux de données binaires de type **Byte** . **Byte** est un type valeur qui représente des entiers non signés dont les valeurs sont comprises entre 0 et 255.|  
|Boolean|Les instances de ce type ont des valeurs `true` ou `false`.|  
|Devise|Valeur *monétaire* comprise entre-922 337 203 685 477,5808 et + 922 337 203 685 477,5807, avec une précision au dix-millième d’une unité monétaire (quatre décimales).|  
|Date|Date et données de temps, stockées comme un double. La partie entière correspond au nombre de jours depuis le 30 décembre 1899 tandis que la partie fractionnaire désigne une fraction d'un jour ou l'heure.|  
|Double|Nombre à virgule flottante compris entre -1,79769313486232E +308 et 1,79769313486232E +308. Une valeur Double stocke les informations de nombre jusqu'à 15 chiffres décimaux de précision.|  
|Integer|Entier signé 32 bits représentant des entiers signés avec des valeurs qui varient entre 2 147 483 648 (négatif) et 2 147 483 647 (positif).|  
|Unique|Nombre à virgule flottante compris entre - 3,4028235E +38 et 3,4028235E +38. Une valeur Single stocke les informations de nombre jusqu'à 7 chiffres décimaux de précision.|  
|Smallint|Entier signé 16 bits. Le type de valeur *smallint* représente des entiers signés dont les valeurs sont comprises entre le 32768 négatif et le 32767 positif.|  
|Tinyint|Entier signé 8 bits. Le type de valeur Tinyint représente des entiers dont la valeur varie entre 128 (négatif) et 127 (positif).|  
|UnsignedBigInt|Entier non signé 64 bits. Le type valeur *UnsignedBigInt* représente des entiers non signés dont la valeur est comprise entre 0 et 18446744073709551615.|  
|UnsignedInt|Entier non signé 32 bits. Le type valeur *unsignedInt* représente des entiers non signés dont la valeur est comprise entre 0 et 4 294 967 295.|  
|UnsignedSmallInt|Entier non signé 16 bits. Le type valeur *UnsignedSmallInt* représente des entiers non signés dont la valeur est comprise entre 0 et 65535.|  
|UnsignedTinyInt|Entier non signé 8 bits. Le type valeur *UnsignedTinyInt* représente des entiers non signés dont les valeurs sont comprises entre 0 et 255|  
|WChar|Flux de caractères Unicode terminé par le caractère NULL. Un *WCHAR* est une collection séquentielle de caractères Unicode utilisée pour représenter du texte.|  
  
## <a name="amo-validations-on-data-types"></a>Validations AMO sur les types Data  
 Le tableau suivant contient les validations supplémentaires effectuées par AMO (Analysis Management Objects) pour certaines liaisons :  
  
|Object|Liaison|Types de données autorisés|  
|------------|-------------|------------------------|  
|DimensionAttribute|KeyColumns|Tous à l'exception de Binary|  
||NameColumn|WChar uniquement|  
||SkippedLevelsColumn|Types entiers uniquement : BigInt, Integer, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
||CustomRollupColumn|WChar uniquement|  
||CustomRollupPropertiesColumn|WChar uniquement|  
||UnaryOperatorColumn|WChar uniquement|  
||ValueColumn|Tous|  
|AttributeTranslation|CaptionColumn|WChar uniquement|  
|ScalarMiningStructureColumn|KeyColumns|Tous à l'exception de Binary|  
||NameColumn|WChar uniquement|  
|TableMiningStructureColumn|ForeignKeyColumns|Tous à l'exception de Binary|  
|MeasureGroupAttribute|KeyColumns|Tous à l'exception de Binary|  
|Mesure de comptage de valeurs|Source|BigInt, Currency, Double, Integer, Single, SmallInt, TinyInt, UnsignedBigInt, UnsignedInt, UnsignedSmallInt, UnsignedTinyInt|  
  
  
