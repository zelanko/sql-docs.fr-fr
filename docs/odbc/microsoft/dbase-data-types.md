---
title: dBASE Data Types (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Jet-based ODBC drivers [ODBC], DBasedriver
- desktop database drivers [ODBC], DBasedriver
- DBase driver [ODBC], data types
- data types [ODBC], DBase driver
- dbase data types [ODBC]
- ODBC desktop database drivers [ODBC], DBasedriver
ms.assetid: a0e31e6b-d02b-4ee2-9b37-5baf6a11c0a6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 17b96ad0b6674a2d120ef46d9bfa221e8df6d140
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307690"
---
# <a name="dbase-data-types"></a>Types de données dBASE
Le tableau suivant montre comment les types de données DBASE sont cartographiés selon les types de données ODBC SQL. Notez que tous les types de données SQL ODBC ne sont pas pris en charge.  
  
|dBASE type de données|Type de données ODBC|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|Flotteur[1]|SQL_DOUBLE|  
|Logique|SQL_BIT|  
|Mémo|SQL_LONGVARCHAR|  
|NUMÉRIQUE (BCD)|SQL_DOUBLE|  
|OLEOBJECT[1]|SQL_LONGBINARY|  
  
 [1] Valable uniquement pour la version dBASE 5. *x*  
  
 La précision dans dBASE III permet des nombres avec jusqu’à deux chiffres exposants et en numéros DBASE IV avec jusqu’à trois chiffres exposants. Étant donné que les nombres sont stockés sous forme de texte, ils sont convertis en nombres. Si le nombre à convertir ne s’inscrit pas dans un champ, des résultats inexpliqués peuvent se produire.  
  
 Bien que dBASE permette de préciser une précision et une échelle avec un type de données NUMERIC, elle n’est pas prise en charge par le pilote ODBC dBASE. Le pilote ODBC dBASE renvoie toujours une précision de 15 et une échelle de 0 pour un type de données NUMERIC.  
  
 Une colonne créée avec le type de données Numeric à l’aide des cartes du pilote ODBC dBASE au SQL_DOUBLE type de données ODBC. Ainsi, les données de cette colonne sont sujettes à l’arrondissement. Ce comportement n’est pas le même que celui du type de données NUMERIC en dBASE (type N), qui est binary Codéd Decimal (BCD).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** renvoie les types de données ODBC SQL. Toutes les conversions de l’Annexe D de la *référence du programmeur ODBC* sont prises en charge pour les types de données SQL ODBC énumérés plus tôt dans ce sujet.  
  
 Le tableau suivant montre des limites sur les types de données DBASE.  
  
|Type de données|Description|  
|---------------|-----------------|  
|CHAR|La création d’une colonne CHAR de longueur zéro ou non spécifiée renvoie en fait une colonne de 254 byte.|  
|Données chiffrées|Le pilote dBASE ne prend pas en charge les tables dBASE cryptées.|  
|Logique|Le pilote dBASE ne peut pas créer un index sur une colonne LOGICAL.|  
|Mémo|La longueur maximale d’une colonne MEMO est de 65 500 octets.|  
  
 Plus de limitations sur les types de données peuvent être trouvées dans [les limites de type de données](../../odbc/microsoft/data-type-limitations.md).
