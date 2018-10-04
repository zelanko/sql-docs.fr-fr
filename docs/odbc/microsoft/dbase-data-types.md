---
title: Types de données dBASE | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc4b4c7a5c1074a62bf0e84d265840109f65ea55
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47626267"
---
# <a name="dbase-data-types"></a>Types de données dBASE
Le tableau suivant montre comment les types de données dBASE sont mappés aux types de données ODBC SQL. Notez que pas tous les types de données SQL ODBC sont prises en charge.  
  
|type de données dBASE|Type de données ODBC|  
|---------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATE|SQL_DATE|  
|FLOAT [1]|SQL_DOUBLE|  
|LOGIQUE|SQL_BIT|  
|MÉMO|SQL_LONGVARCHAR|  
|NUMÉRIQUE (BCD)|SQL_DOUBLE|  
|CLASSES OLEOBJECT [1]|SQL_LONGBINARY|  
  
 Valide [1] uniquement pour la version de dBASE 5. *x*  
  
 Précision en dBASE III permet de nombres avec des exposants à deux chiffres et des nombres de dBASE IV avec jusqu'à exposants à trois chiffres. Étant donné que les nombres sont stockés sous forme de texte, elles sont converties en nombres. Si le nombre à convertir ne tient pas dans un champ, les résultats inexpliquées peuvent se produire.  
  
 DBASE permet une précision et une échelle doit être spécifiée avec un type de données numérique, il n'est pas prise en charge par le pilote dBASE ODBC. Le pilote dBASE ODBC retourne toujours une précision de 15 et une échelle de 0 pour un type de données numérique.  
  
 Une colonne créée avec le type de données numériques en utilisant les mappages de pilote dBASE ODBC SQL_DOUBLE ODBC type de données. Par conséquent, les données dans cet article sont susceptibles d’être arrondi. Ce comportement n’est pas le même comme que les données numériques de type dans dBASE (type N), qui est Binary Coded Decimal (BCD).  
  
> [!NOTE]  
>  **SQLGetTypeInfo** retourne des types de données ODBC SQL. Toutes les conversions dans l’annexe D de la *de référence du programmeur ODBC* sont pris en charge pour les types de données ODBC SQL répertoriées plus haut dans cette rubrique.  
  
 Le tableau suivant présente des limitations sur dBASE types de données.  
  
|Type de données|Description|  
|---------------|-----------------|  
|CHAR|Création d’une colonne de type CHAR égale à zéro ou de longueur non spécifiée retourne en fait une colonne de 254 octets.|  
|Données chiffrées|Le pilote dBASE ne prend pas en charge les tables dBASE chiffré.|  
|LOGIQUE|Le pilote dBASE ne peut pas créer un index sur une colonne logique.|  
|MÉMO|La longueur maximale d’une colonne Mémo est 65 500 octets.|  
  
 Vous trouverez davantage de limites sur les types de données dans [Limitations des types de données](../../odbc/microsoft/data-type-limitations.md).
