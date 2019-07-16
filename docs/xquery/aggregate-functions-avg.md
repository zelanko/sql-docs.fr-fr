---
title: AVG, fonction (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:avg function
- avg function [XQuery]
ms.assetid: 0cc60267-3c56-4a88-8ad7-bb07f0255d56
author: rothja
ms.author: jroth
ms.openlocfilehash: b659aa13a8704a060be12bb015bd0de0fd126562
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985993"
---
# <a name="aggregate-functions---avg"></a>Fonctions d’agrégation : avg
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la moyenne d'une série de nombres.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn:avg($arg as xdt:anyAtomicType*) as xdt:anyAtomicType?  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 Série de valeurs atomiques dont la moyenne est calculée.  
  
## <a name="remarks"></a>Notes  
 Tous les types de valeurs atomisées transmises à **avg()** doivent être un sous-type d’exactement un des trois types de base numériques intégrés ou xdt : untypedAtomic. Ils ne peuvent pas être un mélange. Les valeurs de type xdt:untypedAtomic sont traitées comme valeurs xs:double. Le résultat de **avg()** reçoit le type de base des types transmis, tels que xs : double dans le cas de xdt : untypedAtomic.  
  
 Si l'entrée est vide (valeur empty) de façon statique, « empty » est alors implicite et une erreur statique est émise.  
  
 Le **avg()** fonction retourne la moyenne des nombres calculés. Exemple :  
  
 **Somme (** *$arg* **) div count (** *$arg* **)**  
  
 Si *$arg* est une séquence vide, la séquence vide est retournée.  
  
 Si une valeur xdt : untypedAtomic ne peut pas être convertie en xs : double, la valeur est ignorée dans la séquence d’entrée, *$arg*.  
  
 Dans tous les autres cas, la fonction retourne une erreur statique.  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
### <a name="a-using-the-avg-xquery-function-to-find-work-center-locations-in-the-manufacturing-process-in-which-labor-hours-are-greater-than-the-average-for-all-work-center-locations"></a>R. Utilisation de la fonction XQuery avg() pour rechercher les ateliers dans le processus de fabrication, dans lesquels le nombre d'heures de travail est supérieur à la moyenne de tous les ateliers.  
 Vous pouvez réécrire la requête fournie dans [fonction min (XQuery)](../xquery/aggregate-functions-min.md) à utiliser le **avg()** (fonction).  
  
## <a name="implementation-limitations"></a>Limites de mise en œuvre  
 Les limitations suivantes s'appliquent :  
  
-   Le **avg()** fonction mappe tous les entiers à xs : decimal.  
  
-   Le **avg()** fonction sur les valeurs de type xs : Duration n’est pas pris en charge.  
  
-   Les séquences faisant intervenir plusieurs types dérivés de différents types de base ne sont pas prises en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions XQuery impliquant le type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
