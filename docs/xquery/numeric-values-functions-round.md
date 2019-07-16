---
title: Round, fonction (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:round function
- round function [XQuery]
ms.assetid: 320b572f-bd5b-4055-95a6-dec5718c0041
author: rothja
ms.author: jroth
ms.openlocfilehash: 1927d6e483683699196cfc7e87928f27bf23446a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946543"
---
# <a name="numeric-values-functions---round"></a>Fonctions de valeurs numériques : round
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne le nombre n'ayant pas de partie décimale qui est le plus proche de l'argument. S'il y a plusieurs nombres qui correspondent, le plus proche de l'infini positif est retourné. Exemple :  
  
 Si l’argument est 2.5, **round()** retourne 3.  
  
 Si l’argument est 2.4999, **round()** retourne 2.  
  
 Si l’argument est de -2,5, **round()** retourne -2.  
  
 Si l’argument est une séquence vide, **round()** renvoie la séquence vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn:round ( $arg as numeric?) as numeric?  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 Nombre à laquelle s'applique la fonction.  
  
## <a name="remarks"></a>Notes  
 Si le type de *$arg* est un des trois types numériques de base, **xs : float**, **xs : double**, ou **xs : decimal**, le type de retour est identique à la *$arg* type. Si le type de *$arg* est un type qui est dérivé d’un des types numériques, le type de retour est le type de base numérique.  
  
 Si d’entrée pour le **valeur**, **fn : Ceiling**, ou **fn : Round** functions est **xdt : untypedAtomic**, données non typées, il est implicitement converti dans **xs : double**.  
  
 Tout autre type génère une erreur statique.  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
 Vous pouvez utiliser l’exemple fonctionnel de la [fonction ceiling (XQuery)](../xquery/numeric-values-functions-ceiling.md) pour le **round()** fonction XQuery. Il vous suffit de remplacer le **ceiling()** (fonction) dans la requête avec le **round()** (fonction).  
  
## <a name="implementation-limitations"></a>Limites de mise en œuvre  
 Les limitations suivantes s'appliquent :  
  
-   Le **round()** fonction mappe les valeurs entières à xs : decimal.  
  
-   Le **round()** fonction des valeurs xs : double et comprise entre - 0.5e0 et - 0e0 sont mappées à 0e0 au lieu de - 0e0.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction FLOOR &#40;XQuery&#41;](../xquery/numeric-values-functions-floor.md)   
 [Fonction CEILING &#40;XQuery&#41;](../xquery/numeric-values-functions-ceiling.md)  
  
  
