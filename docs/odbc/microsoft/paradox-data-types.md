---
title: Types de données Paradox | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Paradox driver
- desktop database drivers [ODBC], Paradox driver
- Paradox data types [ODBC]
- Jet-based ODBC drivers [ODBC], Paradox driver
- data types [ODBC], Paradox driver
- Paradox driver [ODBC], data types
ms.assetid: 0c9e5d21-9321-49f8-a055-69459e1c9c85
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8e2f3b1e63578af7c0b42f00113fbb9e87cb8003
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63208414"
---
# <a name="paradox-data-types"></a>Types de données Paradox
Le pilote ODBC Paradox mappe les types de données Paradox aux types de données ODBC SQL. Le tableau suivant répertorie tous les types de données Paradox et montre le SQL ODBC qu’ils sont mappés à des types de données.  
  
|Type de données Paradox|Type de données ODBC|  
|-----------------------|--------------------|  
|ALPHANUMÉRIQUE|SQL_VARCHAR|  
|AUTOINCREMENT[1]|SQL_INTEGER|  
|BCD[1]|SQL_DOUBLE|  
|BYTES[1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|IMAGE [2]|SQL_LONGVARBINARY|  
|LOGIQUE [1]|SQL_BIT|  
|LONG [1]|SQL_INTEGER|  
|MEMO[2]|SQL_LONGVARCHAR|  
|MONEY [1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|COURT|SQL_SMALLINT|  
|TIME[1]|SQL_TIMESTAMP|  
|TIMESTAMP[1]|SQL_TIMESTAMP|  
  
 Valide [1] uniquement pour les versions de Paradox 5. *x*.  
  
 [2] de valide uniquement pour les versions de Paradox 4. *x* et 5. *x*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** retourne des types de données ODBC SQL. Toutes les conversions dans l’annexe D de la *de référence du programmeur ODBC* sont pris en charge pour les types de données ODBC SQL répertoriées plus haut dans cette rubrique.  
  
 Le tableau suivant présente des limitations sur les types de données Paradox.  
  
|Type de données|Description|  
|---------------|-----------------|  
|ALPHANUMÉRIQUE|Création d’une colonne d’alphanumériques de zéro ou de longueur non spécifiée retourne en fait une colonne de 255 octets.|  
|BYTES|Si vous insérez NULL dans une colonne binaire avec le pilote Paradox5, il est modifié en 0.|  
|LONG|La valeur négative maximale prise en charge par le pilote Paradox pour le type de données de type Long dans Paradox 5. *x* n’est pas -2 ^ 31 (-2147483648), comme il convient depuis Long maps pour les données ODBC tapez SQL_INTEGER. La valeur négative maximale prise en charge pour Long est réellement -2 ^ 31 + 1 (-2147483647).|  
|timestamp|Lorsqu’une valeur est insérée dans une colonne TIMESTAMP par le pilote Paradox, puis extraites par la suite de la colonne, la valeur récupérée peut être différente de la valeur insérée autant que de 1 seconde en raison de l’arrondi.|  
  
 Vous trouverez davantage de limites sur les types de données dans [Limitations des types de données](../../odbc/microsoft/data-type-limitations.md).
