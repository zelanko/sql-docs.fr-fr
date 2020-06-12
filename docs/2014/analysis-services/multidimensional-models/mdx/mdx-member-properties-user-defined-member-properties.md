---
title: Propriétés de membre définies par l’utilisateur (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
ms.openlocfilehash: 75e5df5a0677ee205b5517f4c7ca89a390426971
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84546291"
---
# <a name="user-defined-member-properties-mdx"></a>Propriétés de membre définies par l'utilisateur (MDX)
  Les propriétés de membre définies par l'utilisateur peuvent être ajoutées à un niveau spécifique dans une dimension en tant que relations d'attributs. Elles ne peuvent pas être ajoutées au niveau `(All)` d'une hiérarchie ou à la hiérarchie proprement dite.  
  
## <a name="creating-user-defined-member-properties"></a>Création de propriétés de membre définies par l'utilisateur  
 Les propriétés de membre définies par l'utilisateur peuvent être ajoutées à des dimensions ou à des cubes basés sur le serveur par l'intermédiaire de l'interface utilisateur ou par programmation :  
  
-   Pour ajouter des propriétés de membre définies par l’utilisateur à l'aide de l’interface utilisateur, utilisez le Concepteur de dimensions disponible dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Définir des relations d’attributs](../attribute-relationships-define.md).  
  
-   Pour ajouter des propriétés de membre définies par l'utilisateur par programmation, votre application peut utiliser des objets AMO (Analysis Manager Object) ou une combinaison du langage XMLA (XML for Analysis) et du langage ASSL (Analysis Services Scripting Language). Pour plus d’informations, consultez [Relations d’attributs](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## <a name="retrieving-user-defined-member-properties"></a>Récupération de propriétés de membre définies par l'utilisateur  
 Vous pouvez récupérer des propriétés de membre définies par l’utilisateur à l’aide du `PROPERTIES` mot clé ou de la fonction [Properties](/sql/mdx/properties-mdx) .  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>Utilisation du mot clé PROPERTIES pour récupérer des propriétés de membre définies par l'utilisateur  
 La syntaxe permettant de récupérer des propriétés de membre définies par l'utilisateur ressemble à celle utilisée pour faire référence aux propriétés de membre intrinsèques relatives à un niveau, comme le montre la syntaxe suivante :  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 Le mot clé `PROPERTIES` s'affiche après l'expression de jeu de la spécification de l'axe. Par exemple, la requête MDX suivante utilise le mot clé `PROPERTIES`, récupère les propriétés de membre définies par l'utilisateur `List Price` et `Dealer Price`, puis apparaît après l'expression de jeu qui identifie les produits vendus en janvier :  
  
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
 Vous pouvez également accéder à des propriétés de membre définies par l'utilisateur à l'aide de la fonction `Properties`. Par exemple, la requête MDX suivante utilise le mot clé `WITH` pour créer un membre calculé composé de la propriété de membre `List Price` :  
  
```  
WITH   
   MEMBER [Measures].[Product List Price] AS  
   [Product].[Product].CurrentMember.Properties("List Price")  
SELECT   
   [Measures].[Product List Price] on COLUMNS,  
   [Product].[Product].MEMBERS  ON Rows  
FROM [Adventure Works]  
```  
  
 Pour plus d’informations sur la création de membres calculés, consultez [Création de membres calculés dans MDX &#40;MDX&#41;](mdx-calculated-members-building-calculated-members.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des propriétés de membre &#40;MDX&#41;](mdx-member-properties.md)   
 [Propriétés &#40;MDX&#41;](/sql/mdx/properties-mdx)  
  
  
