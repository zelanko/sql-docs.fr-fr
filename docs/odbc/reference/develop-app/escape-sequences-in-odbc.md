---
title: Séquences d’échappement dans ODBC | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 17183a7eacdc5348eea0ddcd7aee4cc493249e77
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68051122"
---
# <a name="escape-sequences-in-odbc"></a>Séquences d’échappement dans ODBC
Un certain nombre de fonctionnalités de langage, telles que les jointures externes et les appels de fonction scalaires, sont généralement implémentées par des SGBD. Toutefois, les syntaxes de ces fonctionnalités ont tendance à être spécifiques au SGBD, même lorsque les syntaxes standard sont définies par les divers corps de normes. Pour cette raison, ODBC définit des séquences d’échappement qui contiennent des syntaxes standard pour les fonctionnalités de langage suivantes :  
  
-   Littéraux date, Time, timestamp et DateTime Interval  
  
-   Fonctions scalaires telles que des fonctions numériques, de chaîne et de conversion de types de données  
  
-   Caractère d’échappement de prédicat LIKE  
  
-   Jointures externes  
  
-   Appels de procédure  
  
 La séquence d’échappement utilisée par ODBC est la suivante :  
  
```  
  
(extension)  
  
```  
  
## <a name="remarks"></a>Notes  
 La séquence d’échappement est reconnue et analysée par les pilotes, qui remplacent les séquences d’échappement par une grammaire spécifique au SGBD. Pour plus d’informations sur la syntaxe de séquence d’échappement, consultez [séquences d’échappement ODBC](../../../odbc/reference/appendixes/odbc-escape-sequences.md) dans annexe C : grammaire SQL.  
  
> [!NOTE]  
>  Dans ODBC 2. *x*, il s’agit de la syntaxe standard de la séquence d’échappement : **--(\*fournisseur (**_nom du fournisseur_**),**_extension_ __**** ** \*** du produit (nom du produit))--  
>   
>  En plus de cette syntaxe, une syntaxe sténographique a été définie sous la forme : **{**_extension_**}**  
>   
>  Dans ODBC 3. *x*, la forme longue de la séquence d’échappement est dépréciée et la forme abrégée est utilisée exclusivement.  
  
 Étant donné que les séquences d’échappement sont mappées par le pilote à des syntaxes propres au SGBD, une application peut utiliser la séquence d’échappement ou la syntaxe spécifique au SGBD. Toutefois, les applications qui utilisent la syntaxe propre au SGBD ne sont pas interopérables. Lors de l’utilisation de la séquence d’échappement, les applications doivent s’assurer que l’attribut d’instruction SQL_ATTR_NOSCAN est désactivé, ce qui est le cas par défaut. Dans le cas contraire, la séquence d’échappement sera envoyée directement à la source de données, où elle provoquera généralement une erreur de syntaxe.  
  
 Les pilotes ne prennent en charge que les séquences d’échappement qu’ils peuvent mapper aux fonctionnalités du langage sous-jacent. Par exemple, si la source de données ne prend pas en charge les jointures externes, ni le pilote. Pour déterminer les séquences d’échappement prises en charge, une application appelle **SQLGetTypeInfo** et **SQLGetInfo**. Pour plus d’informations, consultez la section suivante, [date, heure et littéraux d’horodatage](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md).  
  
 Cette section contient les rubriques suivantes :  
  
-   [Littéraux de date, d’heure et d’horodatage](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)  
  
-   [Appels de fonctions scalaires](../../../odbc/reference/develop-app/scalar-function-calls.md)  
  
-   [Caractère d’échappement du prédicat LIKE](../../../odbc/reference/develop-app/like-predicate-escape-character.md)  
  
-   [Jointures externes](../../../odbc/reference/develop-app/outer-joins.md)  
  
-   [Appels de procédure](../../../odbc/reference/develop-app/procedure-calls.md)
