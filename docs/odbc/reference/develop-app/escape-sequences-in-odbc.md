---
title: Séquences d’évasion à ODBC ( Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC]
- SQL statements [ODBC], escape sequences
- escape sequences [ODBC], about escape sequences
ms.assetid: cf229f21-6c38-4b5b-aca8-f1be0dfeb3d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4d41b0c03ecbe6de63cba1a28a1f39f12a42dc86
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300419"
---
# <a name="escape-sequences-in-odbc"></a>Séquences d’échappement dans ODBC
Un certain nombre de caractéristiques linguistiques, telles que les jointures extérieures et les appels de fonction scalaire, sont généralement mises en œuvre par les DBMS. Cependant, les syntaxes pour ces caractéristiques ont tendance à être DBMS-spécifiques, même lorsque les syntaxes standard sont définies par les différents organismes de normalisation. Pour cette raison, ODBC définit les séquences d’évasion qui contiennent des syntaxes standard pour les caractéristiques de la langue suivantes:  
  
-   Date, heure, timetamp, et les littérals d’intervalle de date  
  
-   Fonctions scalaires telles que les fonctions de conversion numérique, de chaîne et de type de données  
  
-   LIKE prédicate caractère d’évasion  
  
-   Jointures externes  
  
-   Appels de procédure  
  
 La séquence d’évacuation utilisée par ODBC est la suivante :  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>Notes  
 La séquence d’évacuation est reconnue et analysée par les pilotes, qui remplacent les séquences d’évacuation par une grammaire spécifique à DBMS. Pour plus d’informations sur la syntaxe de séquence d’évasion, voir [ODBC Escape Sequences](../../../odbc/reference/appendixes/odbc-escape-sequences.md) à l’annexe C: SQL Grammar.  
  
> [!NOTE]  
>  À ODBC 2. *x*, c’était la syntaxe standard de la séquence d’évasion: **\*---((vendeur (nom**_du vendeur),_**produit (nom**_du produit)_**)**_extension_ ** \*)--**  
>   
>  En plus de cette syntaxe, une syntaxe a été définie de la forme **:**_extension_**}**  
>   
>  À ODBC 3. *x*, la forme longue de la séquence d’évasion a été dépréciée, et la forme de raccourci est utilisée exclusivement.  
  
 Étant donné que les séquences d’évacuation sont cartographiées par le conducteur vers des syntaxes spécifiques à DBMS, une application peut utiliser soit la séquence d’évacuation, soit la syntaxe spécifique à DBMS. Toutefois, les applications qui utilisent la syntaxe spécifique à DBMS ne seront pas interopérables. Lors de l’utilisation de la séquence d’évacuation, les applications doivent s’assurer que l’attribut de l’SQL_ATTR_NOSCAN déclaration est désactivé, ce qui est par défaut. Dans le cas contraire, la séquence d’évacuation sera envoyée directement à la source de données, où elle provoquera généralement une erreur de syntaxe.  
  
 Les conducteurs ne prennent en charge que les séquences d’évasion qu’ils peuvent cartographier vers les caractéristiques du langage sous-jacent. Par exemple, si la source de données ne prend pas en charge les jointures extérieures, le conducteur non plus. Pour déterminer quelles séquences d’évacuation sont prises en charge, une application appelle **SQLGetTypeInfo** et **SQLGetInfo**. Pour plus d’informations, voir la section suivante, [Date, Temps, et Timestamp Literals](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Littéraux de date, d’heure et d’horodatage](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [Appels de fonctions scalaires](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [Caractère d’échappement du prédicat LIKE](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [Jointures externes](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [Appels de procédure](../../../odbc/reference/develop-app/procedure-calls.md)
