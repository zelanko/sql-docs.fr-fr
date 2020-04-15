---
title: Types de données Microsoft Access (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC], Access driver
- Jet-based ODBC drivers [ODBC], Access driver
- desktop database drivers [ODBC], Access driver
- Access driver [ODBC], data types
- access data types [ODBC]
- data types [ODBC], Access driver
ms.assetid: b537348a-bea0-4bd6-84a4-52a75292957f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 024fb65b6fdc81ae0a8e007d1cee150c6a35b91c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307728"
---
# <a name="microsoft-access-data-types"></a>Types de données Microsoft Access
Le tableau suivant montre les types de données Microsoft Access, les types de données utilisés pour créer des tableaux et les types de données ODBC SQL.  
  
|Type de données Microsoft Access|Type de données (CREATETABLE)|Type de données SQL ODBC|  
|--------------------------------|-------------------------------|------------------------|  
|BIGBINARY[1]|Longbinary|SQL_LONGVARBINARY|  
|BINARY|BINARY|SQL_BINARY|  
|BIT|BIT|SQL_BIT|  
|Counter|Counter|SQL_INTEGER|  
|Monétaire (Currency)|Monétaire (Currency)|SQL_NUMERIC|  
|Date/HEURE|DATETIME|SQL_TIMESTAMP|  
|GUID|GUID|SQL_GUID|  
|LONG BINAIRE|Longbinary|SQL_LONGVARBINARY|  
|TEXTE LONG|LONGTEXTE LONGTEXT|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|Mémo|LONGTEXTE LONGTEXT|SQL_LONGVARCHAR[2] SQL_WLONGVARCHAR[3]|  
|NUMBER (FieldSizeMD SINGLE)|Seul|SQL_REAL|  
|NUMBER (FieldSizeMD DOUBLE)|DOUBLE|SQL_DOUBLE|  
|NUMBER (FieldSize BYTE)|BYTE NON SIGNÉ|SQL_TINYINT|  
|NUMBER (FieldSizeMD INTEGER)|SHORT|SQL_SMALLINT|  
|NUMBER (FieldSizeMD LONG INTEGER)|LONG|SQL_INTEGER|  
|NUMERIC|NUMERIC|SQL_NUMERIC|  
|OLE|Longbinary|SQL_LONGVARBINARY|  
|TEXT|VARCHAR|SQL_VARCHAR[1] SQL_WVARCHAR[2]|  
|VARBINARY|VARBINARY|SQL_VARBINARY|  
  
 [1] Accédez uniquement aux applications 4.0. Longueur maximale de 4000 octets. Comportement similaire à LONGBINARY.  
  
 [2] Applications ANSI seulement.  
  
 [3] Applications Unicode et Access 4.0 uniquement.  
  
> [!NOTE]  
>  **SQLGetTypeInfo** renvoie les types de données ODBC. Il ne retournera pas tous les types de données Microsoft Access si plus d’un type Microsoft Access est cartographié selon le même type de données ODBC SQL. Toutes les conversions à l’Annexe D de la *référence du programmeur ODBC* sont prises en charge pour les types de données SQL énumérés dans le tableau précédent.  
  
 Le tableau suivant montre des limites sur les types de données Microsoft Access.  
  
|Type de données|Description|  
|---------------|-----------------|  
|BINARY, VARBINARY et VARCHAR|La création d’une colonne BINARY, VARBINARY ou VARCHAR de longueur zéro ou non spécifiée renvoie en fait une colonne de 510 byte.|  
|BYTE|Même si un champ MICROSOFT Access NUMBER avec un FieldSize égal à BYTE n’est pas signé, un nombre négatif peut être inséré dans le champ lors de l’utilisation du pilote Microsoft Access.|  
|CHAR, LONGVARCHAR et VARCHAR|Une chaîne de caractère littérale peut contenir n’importe quel personnage ANSI (1-255 décimale). Utilisez deux guillemets uniques consécutifs ('') pour représenter une seule note de cotation (').<br /><br /> Les procédures doivent être utilisées pour transmettre des données de caractère lors de l’utilisation d’un personnage spécial dans une colonne de type de données de caractère.|  
|DATE|Les valeurs de date doivent être soit délimitées selon le format de date canonique de l’ODBC, soit délimitées par le délimitant de date (« » Dans le cas contraire, Microsoft Access traitera la valeur comme une expression arithmétique et ne soulèvera pas un avertissement ou une erreur.<br /><br /> Par exemple, la date « 5 mars 1996 » doit être représentée comme « d ' 1996-03-05 ' ou #03/05/1996 ; autrement, si seulement 03/05/1993 est soumis, Microsoft Access évaluera cela comme 3 divisé par 5 divisé par 1996. Cette valeur arrondit jusqu’à l’intégrer 0, et depuis les cartes zéro jour à 1899-12-31, c’est la date utilisée.<br /><br /> Un caractère de tuyau (&#124;) ne peut pas être utilisé dans une valeur de date, même si enfermé dans des citations de dos.|  
|GUID|Type de données limité à Microsoft Access 4.0.|  
|NUMERIC|Type de données limité à Microsoft Access 4.0.|  
  
 Plus de limitations sur les types de données peuvent être trouvées dans [les limites de type de données](../../odbc/microsoft/data-type-limitations.md).
