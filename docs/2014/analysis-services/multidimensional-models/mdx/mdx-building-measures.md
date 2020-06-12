---
title: Génération de mesures dans MDX | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
author: minewiskan
ms.author: owend
ms.openlocfilehash: ac49d37f11584bfbc5d372241056da39e7dd8c93
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546501"
---
# <a name="building-measures-in-mdx"></a>Génération de mesures dans une expression MDX
  Dans les expressions multidimensionnelles (MDX, Multidimensional Expressions), une mesure est une expression DAX nommée qui est résolue en calculant l'expression permettant de retourner une valeur dans un modèle tabulaire. Cette définition anodine couvre un vaste champ d'action. La possibilité de bâtir et d'utiliser des mesures dans une requête MDX est un élément fondamental de la manipulation des données tabulaires.  
  
> [!WARNING]  
>  Les mesures peuvent uniquement être définies dans les modèles tabulaires ; si votre base de données est définie en mode MDX, la création d'une mesure génère une erreur  
  
 Pour créer une mesure définie en tant que partie d'une requête MDX, et dont l'étendue est donc limitée à la requête, utilisez le mot clé WITH. Vous pouvez ensuite utiliser la mesure au sein d'une instruction MDX SELECT. Ainsi, vous pouvez modifier le membre calculé créé à l'aide du mot clé WITH sans porter atteinte à l'instruction SELECT. Toutefois, dans une expression MDX, vous référencez la mesure d'une manière différente de celle utilisée dans les expressions DAX ; pour référencer la mesure, vous la nommez en tant que membre de la dimension [Measures]. Consultez l'exemple d'expression MDX suivant :  
  
```  
with measure  'Sales Territory'[Total Sales Amount] = SUM('Internet Sales'[Sales Amount]) + SUM('Reseller Sales'[Sales Amount])  
select measures.[Total Sales Amount] on columns  
     ,NON EMPTY [Date].[Calendar Year].children on rows  
from [Model]  
  
```  
  
 Retourne les données suivantes lorsqu'elle est exécutée :  
  
||Total Sales Amount||  
|-|------------------------|-|  
|2001|11331808.96||  
|2002|30674773.18||  
|2003|41993729.72||  
|2004|25808962.34||  
  
## <a name="see-also"></a>Voir aussi  
 [Instruction CREATe MEMBER &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member)   
 [Référence des fonctions MDX &#40;&#41;MDX](/sql/mdx/mdx-function-reference-mdx)   
 [Instruction SELECT &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)  
  
  
