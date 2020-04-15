---
title: Types de données Microsoft Excel (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], Excel driver
- Excel data types [ODBC]
- Jet-based ODBC drivers [ODBC], Excel driver
- desktop database drivers [ODBC], Excel driver
- ODBC desktop database drivers [ODBC], Excel driver
- Excel driver [ODBC], data types
ms.assetid: 7b44c8e5-0bc3-4912-8a5d-56f4d5562fe6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8574985e10e5aaa3ae5431af7ee1245643e20b60
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81283769"
---
# <a name="microsoft-excel-data-types"></a>Types de données Microsoft Excel
Le tableau suivant montre comment les types de données du pilote Microsoft Excel sont cartographiés selon les types de données ODBC SQL. Le pilote Microsoft Excel attribue ces types de données à des colonnes dans les tableaux Microsoft Excel en fonction des données de la colonne.  
  
|Type de données Microsoft Excel|Type de données ODBC|  
|-------------------------------|--------------------|  
|Monétaire (Currency)|SQL_NUMERIC|  
|DATETIME|SQL_TIMESTAMP|  
|Logique|SQL_BIT|  
|NUMBER|SQL_DOUBLE|  
|TEXT|SQL_VARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** renvoie les types de données ODBC SQL. Toutes les conversions de l’Annexe D de la *référence du programmeur ODBC* sont prises en charge pour les types de données SQL ODBC énumérés plus tôt dans ce sujet.  
  
 Le tableau suivant montre des limites sur les types de données Microsoft Excel.  
  
|Type de données|Description|  
|---------------|-----------------|  
|Données chiffrées|Le pilote Microsoft Excel ne peut pas lire les données chiffrées.|  
|Cordes d’erreur|Le pilote Microsoft Excel ne peut pas retourner une chaîne de caractères pour les valeurs d’erreur Microsoft Excel (#N/A!, #VALUE!, #REF!, #DIV/0!, #NUM!, #NAME?, et #NULL!), mais retourne un NULL à la place.|  
|Logique|La valeur d’une colonne LOGICAL est retournée dans un tampon SQL_C_CHAR comme 0 ou 1.|  
|NUMBER|Si une colonne d’intégrer est créée, des nombres trop grands pour le type de données integer peuvent être saisis, et des données contenant des valeurs non-integer peuvent être insérées, de sorte que la colonne peut être convertie en SQL_DOUBLE.|  
|TEXT|Lorsque les lignes d’une colonne contiennent plus d’un type de données Microsoft Excel, le pilote ODBC Microsoft Excel attribue le type de données SQL_VARCHAR à la colonne. Il y a une exception à cette règle : si la colonne ne contient que deux ou trois des types de données de date (DATE, TIME et DATETIME), le pilote ODBC Microsoft Excel attribue le type de données SQL_TIMESTAMP à la colonne.<br /><br /> La création d’une colonne TEXT de longueur zéro ou non spécifiée renvoie en fait une colonne de 255 byte.<br /><br /> Une chaîne de caractère littérale peut contenir n’importe quel personnage ANSI (1-255 décimale). Utilisez deux guillemets uniques consécutifs («) pour représenter une seule marque de cotation («).<br /><br /> L’insertion d’un NULL dans une colonne avec un type de données autre que SQL_VARCHAR entraînera le changement de type de données de la colonne pour SQL_VARCHAR.|  
  
 Plus de limitations sur les types de données peuvent être trouvées dans [les limites de type de données](../../odbc/microsoft/data-type-limitations.md).
