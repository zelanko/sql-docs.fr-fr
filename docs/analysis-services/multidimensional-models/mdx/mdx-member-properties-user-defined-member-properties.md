---
title: "Propriétés de membre (MDX) défini par l’utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 12bc5ca42588d81e99490a4ed836c5e71dac49e2
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="mdx-member-properties---user-defined-member-properties"></a>Propriétés de membre MDX - propriétés de membre définies par l’utilisateur
  Les propriétés de membre définies par l'utilisateur peuvent être ajoutées à un niveau spécifique dans une dimension en tant que relations d'attributs. Elles ne peuvent pas être ajoutées au niveau **(Tout)** d’une hiérarchie ou à la hiérarchie proprement dite.  
  
## <a name="creating-user-defined-member-properties"></a>Création de propriétés de membre définies par l'utilisateur  
 Les propriétés de membre définies par l'utilisateur peuvent être ajoutées à des dimensions ou à des cubes basés sur le serveur par l'intermédiaire de l'interface utilisateur ou par programmation :  
  
-   Pour ajouter des propriétés de membre définies par l’utilisateur à l'aide de l’interface utilisateur, utilisez le Concepteur de dimensions disponible dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Définir des relations d’attributs](../../../analysis-services/multidimensional-models/attribute-relationships-define.md).  
  
-   Pour ajouter des propriétés de membre définies par l'utilisateur par programmation, votre application peut utiliser des objets AMO (Analysis Manager Object) ou une combinaison du langage XMLA (XML for Analysis) et du langage ASSL (Analysis Services Scripting Language). Pour plus d’informations, consultez [Relations d’attributs](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## <a name="retrieving-user-defined-member-properties"></a>Récupération de propriétés de membre définies par l'utilisateur  
 Vous pouvez récupérer des propriétés de membre définies par l’utilisateur à l’aide du mot clé **PROPERTIES** ou de la fonction [Properties](../../../mdx/properties-mdx.md) .  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>Utilisation du mot clé PROPERTIES pour récupérer des propriétés de membre définies par l'utilisateur  
 La syntaxe permettant de récupérer des propriétés de membre définies par l'utilisateur ressemble à celle utilisée pour faire référence aux propriétés de membre intrinsèques relatives à un niveau, comme le montre la syntaxe suivante :  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 Le mot clé **PROPERTIES** s’affiche après l’expression de jeu de la spécification de l’axe. Par exemple, la requête MDX suivante utilise le mot clé **PROPERTIES** , récupère les propriétés de membre définies par l’utilisateur `List Price` et `Dealer Price` , puis apparaît après l’expression de jeu qui identifie les produits vendus en janvier :  
  
```  
SELECT   
   CROSSJOIN([Ship Date].[Calendar].[Calendar Year].Members,   
             [Measures].[Sales Amount]) ON COLUMNS,  
   NON EMPTY Product.Product.MEMBERS  
   DIMENSION PROPERTIES   
              Product.Product.[List Price],  
              Product.Product.[Dealer Price]  ON ROWS  
FROM [Adventure Works]  
WHERE ([Date].[Month of Year].[January])   
```  
  
### <a name="using-the-properties-function-to-retrieve-user-defined-member-properties"></a>Utilisation de la fonction Properties pour récupérer des propriétés de membre définies par l'utilisateur  
 Vous pouvez également accéder à des propriétés de membre définies par l’utilisateur à l’aide de la fonction **Properties** . Par exemple, la requête MDX suivante utilise le mot clé **WITH** pour créer un membre calculé composé de la propriété de membre `List Price` :  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 Pour plus d’informations sur la création de membres calculés, consultez [Création de membres calculés dans MDX &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-calculated-members-building-calculated-members.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des propriétés de membre &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-member-properties.md)   
 [Propriétés &#40; MDX &#41;](../../../mdx/properties-mdx.md)  
  
  

