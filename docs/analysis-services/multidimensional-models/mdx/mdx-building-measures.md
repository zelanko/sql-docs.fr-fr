---
title: "Création de mesures dans la syntaxe MDX | Documents Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0347835-4983-4d26-acbb-6c8fae7992bd
caps.latest.revision: "6"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: d7c10b66d6ba27d406c2682b2aea3b8858c8fd12
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-building-measures"></a>Mesures de MDX
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]Dans MDX (Multidimensional Expressions), une mesure est une expression DAX nommée qui est résolue en calculant l’expression pour retourner une valeur dans un modèle tabulaire. Cette définition anodine couvre un vaste champ d'action. La possibilité de bâtir et d'utiliser des mesures dans une requête MDX est un élément fondamental de la manipulation des données tabulaires.  
  
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
 [Instruction CREATE MEMBER &#40;MDX&#41;](../../../mdx/mdx-data-definition-create-member.md)   
 [Informations de référence sur les fonctions MDX &#40;MDX&#41;](../../../mdx/mdx-function-reference-mdx.md)   
 [Instruction SELECT &#40; MDX &#41;](../../../mdx/mdx-data-manipulation-select.md)  
  
  
