---
title: "numéro de fonction (XQuery) | Documents Microsoft"
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
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: dc0ea3abeb06377819bfae2486b5ddd44734123b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="functions-on-nodes---number"></a>Fonctions sur les nœuds - nombre
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Retourne la valeur numérique du nœud qui est indiqué par *$arg*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn:number() as xs:double?   
fn:number($arg as node()?) as xs:double?  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 Nœud dont vous voulez renvoyer la valeur sous forme numérique.  
  
## <a name="remarks"></a>Notes  
 Si *$arg* est ne pas spécifié, la valeur numérique du nœud de contexte, convertie en valeur double, est retournée. Dans SQL Server, **fn :number()** sans argument peut uniquement être utilisé dans le contexte d’un prédicat dépendant du contexte. Autrement dit, elle ne peut être utilisée qu'à l'intérieur de crochets ([ ]). Par exemple, l'expression suivante renvoie l'élément <`ROOT`>.  
  
```  
declare @x xml  
set @x='<ROOT>111</ROOT>'  
select @x.query('/ROOT[number()=111]')  
```  
  
 Si la valeur du nœud n’est pas une représentation lexicale correcte d’un type simple numérique, tel que défini dans **XML Schema Part 2 : Datatypes, recommandation du W3C**, la fonction retourne une séquence vide. Les valeurs NaN ne sont pas prises en charge.  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
### <a name="a-using-the-number-xquery-function-to-retrieve-the-numeric-value-of-an-attribute"></a>A. Utilisation de la fonction XQuery number() pour récupérer la valeur numérique d'un attribut  
 La requête suivante récupère la valeur numérique de l'attribut taille de lot à partir du premier poste de travail du processus de fabrication du modèle de produit 7.  
  
```  
SELECT ProductModelID, Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     for $i in (//AWMI:root//AWMI:Location)[1]  
     return   
       <Location LocationID="{ ($i/@LocationID) }"   
                   LotSizeA="{  $i/@LotSize }"  
                   LotSizeB="{  number($i/@LotSize) }"  
                   LotSizeC="{ number($i/@LotSize) + 1 }" >  
  
       </Location>  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Le **number()** fonction n’est pas requise, comme indiqué par la requête pour le **LotSizeA** attribut. Il s'agit d'une fonction XPath 1.0 qui est incluse pour garantir la compatibilité ascendante.  
  
-   La requête XQuery **LotSizeB** spécifie la fonction number et est redondant.  
  
-   La requête pour **LotSizeD** illustre l’utilisation d’une valeur numérique dans une opération arithmétique.  
  
 Voici le résultat obtenu :  
  
```  
ProductModelID   Result  
----------------------------------------------  
7              <Location LocationID="10"   
                         LotSizeA="100"   
                         LotSizeB="100"   
                         LotSizeC="101" />  
```  
  
### <a name="implementation-limitations"></a>Limites de mise en œuvre  
 Les limitations suivantes s'appliquent :  
  
-   Le **number()** fonction accepte uniquement les nœuds. Elle n'accepte pas de valeurs atomiques.  
  
-   Lorsque les valeurs ne peuvent pas être retournés sous forme de nombre, la **number()** fonction retourne la séquence vide au lieu de la valeur NaN.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions XQuery impliquant le type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  

