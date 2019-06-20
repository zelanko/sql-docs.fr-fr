---
title: Membres calculés dans les sous-sélections et les sous-cubes | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e35e8f7-ae1c-4549-8432-accf036d2373
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 57a7a9597be4b7a662fddd9550fdf341be44f922
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66074791"
---
# <a name="calculated-members-in-subselects-and-subcubes"></a>Membres calculés dans les sous-sélections et les sous-cubes
  Dans les versions précédentes, les membres calculés n'étaient pas autorisés dans les sous-sélections ou les sous-cubes. Toutefois, à partir de SQL Server 2008, ils sont autorisés et activés par une propriété de connexion. De plus, un nouveau comportement pour les membres calculés, dans les sous-sélections et les sous-cubes, a été introduit dans SQL Server 2008 R2.  
  
## <a name="calculated-members-in-subselects-and-subcubes"></a>Membres calculés dans les sous-sélections et les sous-cubes  
 Le `SubQueries` propriété de chaîne de connexion dans <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A> ou `DBPROPMSMDSUBQUERIES` propriété dans [propriétés XMLA prises en charge &#40;XMLA&#41; ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties) définit le comportement ou l’autorisation des membres calculés ou calculés définit les sous-sélections ou les sous-cubes. Dans le cadre de ce document, sauf indication contraire, la sous-sélection fait référence aux sous-sélections et aux sous-cubes.  
  
 La propriété SubQueries autorise les valeurs suivantes.  
  
|||  
|-|-|  
|Value|Description|  
|0|Les membres calculés ne sont pas autorisés dans les sous-sélections ou les sous-cubes.<br /><br /> Une erreur est déclenchée lors de l'évaluation de la sous-sélection ou du sous-cube si un membre calculé est référencé.|  
|1|Les membres calculés sont autorisés dans les sous-sélections ou les sous-cubes mais aucun membre ascendant n'est introduit dans le sous-espace retourné.|  
|2|Les membres calculés sont autorisés dans les sous-sélections et les sous-cubes mais aucun membre ascendant n'est introduit dans le sous-espace retourné. Par ailleurs, la granularité mixte est autorisée dans la sélection des membres calculés.|  
  
 La définition des valeurs 1 ou 2 dans la propriété SubQueries autorise l'utilisation des membres calculés pour filtrer le sous-espace des sous-sélections retourné.  
  
 Un exemple aidera à clarifier le concept ; en premier lieu, un membre calculé doit être créé, ensuite une requête de sous-sélection doit être émise pour afficher le comportement susmentionné.  
  
 L'exemple suivant crée un membre calculé qui ajoute [Seattle Metro] comme ville à la hiérarchie [Geography].[Geography] sous l'État de Washington.  
  
 Pour exécuter l'exemple, la chaîne de connexion doit contenir la propriété SubQueries avec une valeur 1 et toutes les instructions MDX doivent être exécutées dans la même session.  
  
 En premier lieu, vous devez émettre l'expression MDX suivante :  
  
```  
//Remember to set Subqueries=1 in the connection string prior  
//to issue these commands  
//--> AS2008 behavior  
CREATE MEMBER [Adventure Works].[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]   
   AS  AGGREGATE(   
                 {   
                   [Geography].[Geography].[City].&[Bellevue]&[WA]  
                 , [Geography].[Geography].[City].&[Issaquah]&[WA]  
                 , [Geography].[Geography].[City].&[Redmond]&[WA]  
                 , [Geography].[Geography].[City].&[Seattle]&[WA]  
                 }  
                )    
```  
  
 Ensuite, émettez la requête MDX suivante pour afficher les membres calculés autorisés dans les sous-sélections.  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {[Geography].[Geography].[State-Province].&[WA]&[US].[Seattle Metro Agg]} on 0 from [Adventure Works])  
Where [Measures].[Reseller Sales Amount]  
```  
  
 Vous obtenez les résultats suivants :  
  
|||||||  
|-|-|-|-|-|-|  
||All Periods|CY 2001|CY 2002|CY 2003|CY 2004|  
|Seattle Metro Agg|2 383 545,69 $|291 248,93 $|763 557,02 $|915 832,36 $|412 907,37 $|  
  
 Comme expliqué plus haut, les ascendants de [Seattle Metro] n'existent pas dans le sous-espace retourné lorsque SubQueries=1, par conséquent [Géographie].[Géographie].allmembers contient seulement le membre calculé.  
  
 Si l'exemple est exécuté en utilisant SubQueries=2, dans la chaîne de connexion, vous obtenez les résultats suivants :  
  
|||||||  
|-|-|-|-|-|-|  
||All Periods|CY 2001|CY 2002|CY 2003|CY 2004|  
|All Geographies|(Null)|(Null)|(Null)|(Null)|(Null)|  
|United States|(Null)|(Null)|(Null)|(Null)|(Null)|  
|Washington|(Null)|(Null)|(Null)|(Null)|(Null)|  
|Seattle Metro Agg|2 383 545,69 $|291 248,93 $|763 557,02 $|915 832,36 $|412 907,37 $|  
  
 Comme expliqué plus haut, lorsqu'on utilise SubQueries=2, les ascendants de [Seattle Metro] existent dans le sous-espace retourné mais aucune valeur n'existe pour ces membres parce qu'il n'y a pas de membres standard à fournir pour les agrégations. Par conséquent, des valeurs de type Null sont fournies pour tous les membres ascendants du membre calculé dans cet exemple.  
  
 Pour comprendre le comportement ci-dessus, vous devez comprendre que les membres calculés ne contribuent pas aux agrégations de leurs parents, contrairement aux membres standard ; pour plus d'informations à ce sujet, consultez ; ce qui précède implique que filtrer par les membres calculés seuls aboutira à des ascendants vides parce qu'il n'y a pas de membres standard qui contribuent aux valeurs d'agrégation du sous-espace résultant. Si vous ajoutez des membres standard à l'expression de filtrage, les valeurs d'agrégation proviendront de ces membres standard. Pour poursuivre avec l'exemple ci-dessus, si les villes de Portland, Oregon, et la ville de Spokane, Washington, sont ajoutées au même axe où apparaît le membre calculé, comme indiqué dans l'expression MDX suivante :  
  
```  
Select [Date].[Calendar Year].members on 0,  
       [Geography].[Geography].allmembers on 1  
from (Select {  
               [Seattle Metro Agg]  
             , [Geography].[Geography].[City].&[Portland]&[OR]  
             , [Geography].[Geography].[City].&[Spokane]&[WA]  
             } on 0 from [Adventure Works]  
     )  
Where [Measures].[Reseller Sales Amount]  
```  
  
 Vous obtenez les résultats suivants.  
  
|||||||  
|-|-|-|-|-|-|  
||All Periods|CY 2001|CY 2002|CY 2003|CY 2004|  
|All Geographies|$235,171.62|$419.46|$4,996.25|$131,788.82|$97,967.09|  
|United States|$235,171.62|$419.46|$4,996.25|$131,788.82|$97,967.09|  
|Oregon|$30,968.25|$419.46|$4,996.25|$17,442.97|$8,109.56|  
|Portland|$30,968.25|$419.46|$4,996.25|$17,442.97|$8,109.56|  
|97205|$30,968.25|$419.46|$4,996.25|$17,442.97|$8,109.56|  
|Washington|$204,203.37|(Null)|(Null)|$114,345.85|$89,857.52|  
|Spokane|$204,203.37|(Null)|(Null)|$114,345.85|$89,857.52|  
|99202|$204,203.37|(Null)|(Null)|$114,345.85|$89,857.52|  
|Seattle Metro Agg|2 383 545,69 $|291 248,93 $|763 557,02 $|915 832,36 $|412 907,37 $|  
  
 Dans les résultats ci-dessus, les valeurs d'agrégation pour [All Geographies], [United States], [Oregon] et [Washington] proviennent de l'agrégation sur les descendants de &[Portland]&[OR] et &[Spokane]&[WA]. Rien ne provient du membre calculé.  
  
### <a name="remarks"></a>Notes  
 Seuls les membres calculés globaux ou de session sont autorisés dans les expressions de sous-sélection ou de sous-cube. Si des membres calculés sont demandés dans l'expression MDX, une erreur est déclenchée lorsque l'expression de sous-sélection ou de sous-cube est évaluée.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>   
 [Instructions de sous-sélection dans les requêtes](subselects-in-queries.md)   
 [Propriétés XMLA prises en charge &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/propertylist-element-supported-xmla-properties)  
  
  
