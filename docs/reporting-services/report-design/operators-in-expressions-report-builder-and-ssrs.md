---
title: Opérateurs dans les expressions (Générateur de rapports) | Microsoft Docs
description: Choisissez parmi les catégories d’opérateurs pris en charge dans une expression pour représenter les actions appliquées aux termes d’une expression dans le Générateur de rapports.
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: d22dc8b6-4353-40e7-91a1-65e8dae6325d
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c310b902889b8dc78b81609439f09ba2d6e4beb7
ms.sourcegitcommit: fe59f8dc27fd633f5dfce54519d6f5dcea577f56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91934894"
---
# <a name="operators-in-expressions-report-builder-and-ssrs"></a>Opérateurs dans les expressions (Générateur de rapports et SSRS)
  Un opérateur est un symbole qui représente des actions exécutées sur un ou plusieurs termes d'une expression. Les catégories d'opérateurs suivantes sont prises en charge dans une expression : arithmétique, de comparaison, de concaténation, logique ou au niveau du bit, et de décalage de bits.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="arithmetic"></a>Arithmétique  
 Les opérateurs arithmétiques effectuent des opérations mathématiques sur deux termes numériques d'une expression.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|^|Élève un nombre à la puissance d'un autre nombre.|  
|*|Multiplie deux nombres.|  
|/|Effectue la division entre deux nombres et retourne un résultat à virgule flottante.|  
|\|Effectue la division entre deux nombres et retourne un résultat sous forme d'entier.|  
|Mod|Retourne le reste entier d'une division. Par exemple, 7 Mod 5 = 2 parce que le reste de 7 divisé par 5 est 2.|  
|+|Additionne deux nombres.|  
|-|Retourne la différence entre deux nombres ou indique la valeur négative d'un terme numérique.|  
  
### <a name="comparison"></a>Comparaison  
 Les opérateurs de comparaison testent si deux expressions sont identiques.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|<|Inférieur à.|  
|\<=|Inférieur ou égal à.|  
|>|Supérieur à.|  
|>=|Supérieur ou égal à.|  
|=|Égal à.|  
|<>|Non égal à.|  
|Correspond à|Détermine si une chaîne de caractères donnée correspond à un modèle spécifié. Une chaîne peut comprendre des caractères normaux ainsi que des caractères génériques. Au cours de l'analyse, les caractères normaux doivent correspondre exactement aux caractères spécifiés dans la chaîne de caractères. Toutefois, les caractères génériques peuvent être associés à des portions aléatoires de la chaîne de caractères. L'utilisation de caractères génériques rend l'opérateur LIKE plus flexible que lorsque les opérateurs de comparaison des chaînes = et != sont utilisés.<br /><br /> Le tableau suivant répertorie les caractères qui peuvent être utilisés comme caractères génériques :<br /><br /> % : Toute chaîne de zéro caractère ou plus.<br /><br /> _ : N'importe quel caractère.<br /><br /> [ ] : Tout caractère de la plage spécifiée (par exemple, [a-f]) ou de l’ensemble spécifié (par exemple, [aeiou]).<br /><br /> [^] : Tout caractère hors de la plage spécifiée (par exemple, [^a-f]) ou de l’ensemble spécifié (par exemple, [^aeiou]).|  
|Is|Compare deux références d'objet.|  
  
### <a name="string-concatenation"></a>Concaténation de chaînes  
 La concaténation de chaînes ajoute la seconde chaîne à la fin de la première dans une expression. Pour d'autres opérations sur les chaînes, utilisez les fonctions intégrées.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|&|Concatène deux chaînes.|  
|+|Concatène deux chaînes.|  
  
### <a name="logical-and-bitwise"></a>Logique et au niveau du bit  
 Les opérateurs logique et au niveau du bit effectuent des manipulations logiques entre deux termes entiers dans une expression.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|and|Effectue une conjonction logique sur deux expressions booléennes ou une conjonction au niveau du bit sur deux expressions numériques.|  
|Not|Effectue une négation logique sur une expression booléenne ou une négation au niveau du bit sur une expression numérique.|  
|ou|Effectue une disjonction logique sur deux expressions booléennes ou une disjonction au niveau du bit sur deux valeurs numériques.|  
|Xor|Effectue une exclusion logique sur deux expressions booléennes ou une exclusion au niveau du bit sur deux expressions numériques.|  
|AndAlso|Effectue une conjonction logique sur deux expressions.|  
|OrElse|Effectue une disjonction logique sur deux expressions.|  
  
### <a name="bit-shift"></a>Décalage de bits  
 Les opérateurs de décalage de bits effectuent des manipulations de bits entre deux termes entiers dans une expression.  
  
|Opérateur|Description|  
|--------------|-----------------|  
|<\<|Effectue un décalage arithmétique vers la gauche sur un modèle binaire.|  
|>>|Effectue un décalage arithmétique vers la droite sur un modèle binaire.|  
  
## <a name="see-also"></a>Voir aussi  
 [Boîte de dialogue Expression](/previous-versions/sql/)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Boîte de dialogue Expression &#40;Générateur de rapports&#41;](./expressions-report-builder-and-ssrs.md)  
  
