---
title: Types de données paradoxaux (en anglais seulement) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a85cf643a6d22b9b2fce15984539d74dc43c62ab
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290929"
---
# <a name="paradox-data-types"></a>Types de données Paradox
Le pilote ODBC Paradox cartographie les types de données Paradox aux types de données ODBC SQL. Le tableau suivant répertorie tous les types de données Paradox et affiche les types de données SQL ODBC qu’ils sont cartographiés.  
  
|Type de données paradoxale|Type de données ODBC|  
|-----------------------|--------------------|  
|Alphanumérique|SQL_VARCHAR|  
|AUTOINCRÉTION[1]|SQL_INTEGER|  
|BCD[1]|SQL_DOUBLE|  
|OCTETS[1]|SQL_BINARY|  
|DATE|SQL_DATE|  
|IMAGE[2]|SQL_LONGVARBINARY|  
|LOGIQUE[1]|SQL_BIT|  
|LONG[1]|SQL_INTEGER|  
|MÉMO[2]|SQL_LONGVARCHAR|  
|ARGENT[1]|SQL_DOUBLE|  
|NUMBER|SQL_DOUBLE|  
|SHORT|SQL_SMALLINT|  
|TEMPS[1]|SQL_TIMESTAMP|  
|TIMESTAMP[1]|SQL_TIMESTAMP|  
  
 [1] Valable uniquement pour les versions Paradox 5. *x*.  
  
 [2] Valable uniquement pour les versions Paradox 4. *x* et 5. *x*.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** renvoie les types de données ODBC SQL. Toutes les conversions de l’Annexe D de la *référence du programmeur ODBC* sont prises en charge pour les types de données SQL ODBC énumérés plus tôt dans ce sujet.  
  
 Le tableau suivant montre des limites sur les types de données Paradox.  
  
|Type de données|Description|  
|---------------|-----------------|  
|Alphanumérique|La création d’une colonne ALPHANUMERIC de longueur zéro ou non spécifiée renvoie en fait une colonne de 255 byte.|  
|BYTES|Si vous insérez NULL dans une colonne binaire avec le pilote Paradox5, il est changé en 0.|  
|LONG|La valeur négative maximale supportée par le pilote Paradox pour le type de données Long dans Paradox 5. *x* n’est pas -2-31 (-2147483648), comme il devrait être depuis cartes longues au type de données ODBC SQL_INTEGER. La valeur négative maximale supportée pour Long est en fait de -2 à 31 euros (-2147483647).|  
|timestamp|Lorsqu’une valeur est insérée dans une colonne TIMESTAMP par le pilote Paradox, puis récupérée par la suite dans la colonne, la valeur récupérée peut différer de la valeur insérée jusqu’à 1 seconde en raison de l’arrondissement.|  
  
 Plus de limitations sur les types de données peuvent être trouvées dans [les limites de type de données](../../odbc/microsoft/data-type-limitations.md).
