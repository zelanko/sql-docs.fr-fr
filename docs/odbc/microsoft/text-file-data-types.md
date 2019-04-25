---
title: Types de données de fichier texte | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 23416cb067507d821701e57255fdc6f81ee607c4
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62633004"
---
# <a name="text-file-data-types"></a>Types de données des fichiers texte
Le tableau suivant montre comment les types de données texte sont mappés aux types de données ODBC SQL. Notez que pas tous les types de données SQL ODBC sont prises en charge par le pilote ODBC texte.  
  
|Type de données de texte|Type de données ODBC|  
|--------------------|--------------------|  
|CHAR|SQL_VARCHAR|  
|DATETIME|SQL_TIMESTAMP|  
|FLOAT|SQL_DOUBLE|  
|INTEGER|SQL_INTEGER|  
|LONGCHAR|SQL_LONGVARCHAR|  
  
> [!NOTE]  
>  **SQLGetTypeInfo** retourne des types de données ODBC. Toutes les conversions dans l’annexe D de la *de référence du programmeur ODBC* sont pris en charge pour les types de données SQL répertoriés dans le tableau précédent.  
  
 Le tableau suivant présente des limitations sur les types de données de texte.  
  
|Type de données|Description|  
|---------------|-----------------|  
|CHAR|Création d’une colonne de type CHAR égale à zéro ou de longueur non spécifiée retourne en fait une colonne 255 bits.<br /><br /> Dans les fichiers délimités, une colonne de type CHAR peut ou ne dispose pas de délimiteurs de guillemet double au début et à la fin ; dans les fichiers de longueur fixe, des guillemets doubles ne sont pas utilisés comme délimiteurs.|  
|DATETIME|MM-JJ-AA (par exemple, 01-17-92)<br /><br /> JJ-MMM-AA (par exemple, janvier-17-92)<br /><br /> JJ-MMM-AA (par exemple, 17-Jan-92)<br /><br /> AAAA-MM-JJ (par exemple, 1992-01-17)<br /><br /> JJ-MMM-AAAA (par exemple, 1992-janvier-17)<br /><br /> Séparateurs de date mixtes ne sont pas autorisés dans une table.<br /><br /> Le texte ISAM met en forme un champ de date/heure dans le format des États-Unis ou en Europe, selon le paramètre International dans le panneau de configuration Windows.|  
|FLOAT|La largeur maximale inclut le signe et la virgule décimale. Dans Schema.ini, la largeur est indiquée comme suit :<br /><br /> 14.083 est FLOAT de 6 de la largeur<br /><br /> -14.083 est FLOAT de 7 de la largeur<br /><br /> +14.083 est FLOAT de 7 de la largeur<br /><br /> 14083. est FLOAT largeur 6<br /><br /> ODBC retourne toujours 8 pour les colonnes de type FLOAT.<br /><br /> Colonnes de type FLOAT peuvent également être en notation scientifique, par exemple :<br /><br /> -3.04E + 2 est Float de 8 de la largeur<br /><br /> 25E4 est Float de 4 de la largeur<br /><br /> **Remarque** notation décimale et scientifique ne peuvent pas être combinée dans une colonne.<br /><br /> Les valeurs NULL sont représentées par une chaîne vide remplie dans les fichiers de longueur fixe et sont omis dans les fichiers délimités.<br /><br /> Données float peuvent être remplies avec des espaces à droite.|  
|INTEGER|Les valeurs valides pour les colonnes d’entiers sont 32 767 pour -32766.<br /><br /> Dans Schema.ini, la largeur est indiquée comme suit :<br /><br /> 14083 est 5 de la largeur entière<br /><br /> 0 est 1 de la largeur entière<br /><br /> ODBC retourne toujours 4 pour les colonnes de type entier.<br /><br /> La largeur maximale inclut un signe. La largeur maximale d’une colonne d’entiers est 11, bien que la largeur peut être supérieure en raison des espaces sont autorisés dans les tables de format fixe.|  
|LONGCHAR|Théoriques limitent sur la largeur d’une colonne LONGCHAR dans soit de longueur fixe ou délimité table est 65500K. Le texte ISAM est plus probable fournir une prise en charge fiable jusqu'à environ 32 Ko.|  
  
 Vous trouverez davantage de limites sur les types de données dans [Limitations des types de données](../../odbc/microsoft/data-type-limitations.md).
