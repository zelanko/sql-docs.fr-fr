---
title: Propriétés de membre (MDX) défini par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- custom member properties [MDX]
ms.assetid: b64cc581-e784-42c4-bec8-932abd687423
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f7a61772b93c78173f3eca8ad38fca1ade671a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48114309"
---
# <a name="user-defined-member-properties-mdx"></a>Propriétés de membre définies par l'utilisateur (MDX)
  Les propriétés de membre définies par l'utilisateur peuvent être ajoutées à un niveau spécifique dans une dimension en tant que relations d'attributs. Propriétés de membre définies par l’utilisateur ne peut pas être ajoutées à la `(All)` au niveau d’une hiérarchie, ou à la hiérarchie elle-même.  
  
## <a name="creating-user-defined-member-properties"></a>Création de propriétés de membre définies par l'utilisateur  
 Les propriétés de membre définies par l'utilisateur peuvent être ajoutées à des dimensions ou à des cubes basés sur le serveur par l'intermédiaire de l'interface utilisateur ou par programmation :  
  
-   Pour ajouter des propriétés de membre définies par l’utilisateur à l'aide de l’interface utilisateur, utilisez le Concepteur de dimensions disponible dans [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. Pour plus d’informations, consultez [Définir des relations d’attributs](../attribute-relationships-define.md).  
  
-   Pour ajouter des propriétés de membre définies par l'utilisateur par programmation, votre application peut utiliser des objets AMO (Analysis Manager Object) ou une combinaison du langage XMLA (XML for Analysis) et du langage ASSL (Analysis Services Scripting Language). Pour plus d’informations, consultez [Relations d’attributs](../../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
## <a name="retrieving-user-defined-member-properties"></a>Récupération de propriétés de membre définies par l'utilisateur  
 Vous pouvez récupérer les propriétés de membre définies par l’utilisateur à l’aide du `PROPERTIES` mot clé ou le [propriétés](/sql/mdx/properties-mdx) (fonction).  
  
### <a name="using-the-properties-keyword-to-retrieve-user-defined-member-properties"></a>Utilisation du mot clé PROPERTIES pour récupérer des propriétés de membre définies par l'utilisateur  
 La syntaxe permettant de récupérer des propriétés de membre définies par l'utilisateur ressemble à celle utilisée pour faire référence aux propriétés de membre intrinsèques relatives à un niveau, comme le montre la syntaxe suivante :  
  
 `DIMENSION PROPERTIES [Dimension.]Level.<Custom_Member_Property>`  
  
 Le `PROPERTIES` mot clé apparaît après l’expression d’ensemble de la spécification de l’axe. Par exemple, la requête MDX suivante le `PROPERTIES` mot clé récupère le `List Price` et `Dealer Price` des propriétés de membre définies par l’utilisateur et apparaît une fois que l’expression d’ensemble qui identifie les produits vendus en janvier :  
  
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
 Vous pouvez également accéder à des propriétés de membre définies par l'utilisateur à l'aide de la fonction `Properties`. Par exemple, la requête MDX suivante utilise le `WITH` mot clé pour créer un membre calculé composé de la `List Price` propriété de membre :  
  
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
 [À l’aide des propriétés de membre &#40;MDX&#41;](mdx-member-properties.md)   
 [Propriétés &#40;MDX&#41;](/sql/mdx/properties-mdx)  
  
  
