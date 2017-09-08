---
title: Fonction FLOOR (XQuery) | Documents Microsoft
ms.custom: 
ms.date: 03/09/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
dev_langs:
- XML
helpviewer_keywords:
- floor function [XQuery]
- fn:floor function
ms.assetid: 4ace57dd-b66e-4b60-a2b9-a1b0f1a0831d
caps.latest.revision: 27
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4ebc7cd706986a4be284a0788b1976898fb5d313
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="numeric-values-functions---floor"></a>Fonctions de valeurs numériques - floor
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Renvoie le nombre le plus élevé sans portion décimale qui ne dépasse pas la valeur de cet argument. Si l'argument est une séquence vide, la fonction renvoie la séquence vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn:floor ($arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 Nombre à laquelle s'applique la fonction.  
  
## <a name="remarks"></a>Notes  
 Si le type de *$arg* est un des trois types numériques de base, **xs : float**, **xs : double**, ou **xs : decimal**, le type de retour est identique à celui du *$arg* type. Si le type de *$arg* est un type qui est dérivé de l’un des types numériques, le type de retour est le type numérique de base.  
  
 Si l’entrée pour les fonctions fn : Floor, fn : Ceiling ou fn : Round est **xdt : untypedAtomic**, les données non typées, elle est implicitement convertie en **xs : double**. Tout autre type génère une erreur statique.  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
 Vous pouvez utiliser l’exemple fonctionnel de la [fonction ceiling (XQuery)](../xquery/numeric-values-functions-ceiling.md) pour le **floor()** fonction XQuery. Il vous suffit de remplacer le **ceiling()** fonction dans la requête avec la **floor()** (fonction).  
  
## <a name="implementation-limitations"></a>Limites de mise en œuvre  
 Les limitations suivantes s'appliquent :  
  
-   Le **floor()** fonction mappe toutes les valeurs entières à xs : decimal.  
  
## <a name="see-also"></a>Voir aussi  
 [Ceiling, fonction &#40; XQuery &#41;](../xquery/numeric-values-functions-ceiling.md)   
 [Round (fonction) &#40; XQuery &#41;](../xquery/numeric-values-functions-round.md)   
 [Fonctions XQuery impliquant le type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
