---
title: Types de données de fichiers texte (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- text file driver [ODBC], data types
- ODBC desktop database drivers [ODBC], text file driver
- desktop database drivers [ODBC], text file driver
- text file data types [ODBC]
- Jet-based ODBC drivers [ODBC], text file driver
ms.assetid: e113112e-ae42-469e-8e4b-a365a10d9071
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7864dc81eaa3dd37f3d0053b2329c8842e445c8d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302657"
---
# <a name="text-file-data-types"></a>Types de données des fichiers texte
Le tableau suivant montre comment les types de données textuelles sont cartographiés selon les types de données ODBC SQL. Notez que tous les types de données SQL ODBC ne sont pas pris en charge par le pilote de texte ODBC.  
  
|Type de données textuelles|Type de données ODBC|  
|--------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATETIME|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_INTEGER|  
|LONGCHAR (EN)|SQL_LONGVARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** renvoie les types de données ODBC. Toutes les conversions à l’Annexe D de la *référence du programmeur ODBC* sont prises en charge pour les types de données SQL énumérés dans le tableau précédent.  
  
 Le tableau suivant montre des limites sur les types de données textuelles.  
  
|Type de données|Description|  
|---------------|-----------------|  
|CHAR|La création d’une colonne CHAR de longueur zéro ou non spécifiée renvoie en fait une colonne 255 bits.<br /><br /> Dans les fichiers délimités, une colonne CHAR peut ou non avoir des délimitations de double guillemets au début et à la fin; dans les fichiers à durée fixe, les doubles guillemets ne sont pas utilisés comme délimitants.|  
|DATETIME|MM-DD-YY (par exemple, 01-17-92)<br /><br /> MMM-DD-YY (par exemple, 17-92 janvier)<br /><br /> DD-MMM-YY (par exemple, 17-Jan-92)<br /><br /> YYYY-MM-DD (par exemple, 1992-01-17)<br /><br /> YYYY-MMM-DD (par exemple, 1992-janvier-17)<br /><br /> Les séparateurs de dates mixtes ne sont pas autorisés à l’intérieur d’une table.<br /><br /> Le text ISAM formate un champ DATETIME aux États-Unis ou en format européen, selon le paramètre international dans le panneau de contrôle Windows.|  
|FLOAT|La largeur maximale comprend le signe et le point décimal. Dans Schema.ini, la largeur est indiquée comme suit :<br /><br /> 14.083 est FLOAT Width 6<br /><br /> -14.083 est FLOAT Width 7<br /><br /> 14.083 est FLOAT Width 7<br /><br /> 14083. est FLOAT Width 6<br /><br /> ODBC retourne toujours 8 pour les colonnes FLOAT.<br /><br /> Les colonnes FLOAT peuvent également être dans la notation scientifique, par exemple :<br /><br /> -3.04E-2 est Flotteur Largeur 8<br /><br /> 25E4 est Float Width 4<br /><br /> **Note** La notation décimale et scientifique ne peut pas être mélangée dans une colonne.<br /><br /> Les valeurs NULL sont représentées par une chaîne rembourrée vierge dans les fichiers à durée fixe et sont omises dans les fichiers délimités.<br /><br /> Les données de flotteur peuvent être rembourrées avec des blancs de tête.|  
|INTEGER|Les valeurs valides pour les colonnes INTEGER sont de 32767 à -32766.<br /><br /> Dans Schema.ini, la largeur est indiquée comme suit :<br /><br /> 14083 est INTEGER Width 5<br /><br /> 0 est INTEGER Width 1<br /><br /> ODBC retourne toujours 4 pour les colonnes INTEGER.<br /><br /> La largeur maximale comprend un signe. La largeur maximale d’une colonne INTEGER est de 11, bien que la largeur puisse être plus grande en raison des blancs qui sont autorisés dans les tables à format fixe.|  
|LONGCHAR (EN)|La limite théorique sur la largeur d’une colonne LONGCHAR dans une table de longueur fixe ou délimitée est de 65500K. Le texte ISAM est plus susceptible de fournir un soutien fiable jusqu’à environ 32K.|  
  
 Plus de limitations sur les types de données peuvent être trouvées dans [les limites de type de données](../../odbc/microsoft/data-type-limitations.md).
