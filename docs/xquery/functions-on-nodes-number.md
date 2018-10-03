---
title: numéro de fonction (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- number function
- fn:number function
ms.assetid: dff6d19b-765c-4df9-afff-9a0e7be9b91b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: dbe1476f9b05d6ebaf3e919244fb759137cb2402
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47650937"
---
# <a name="functions-on-nodes---number"></a>Fonctions sur les nœuds : number
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

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
  
 Si la valeur du nœud n’est pas une représentation lexicale correcte d’un type numérique simple, tel que défini dans **XML Schema Part 2 : Datatypes, recommandation du W3C**, la fonction retourne une séquence vide. Les valeurs NaN ne sont pas prises en charge.  
  
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
  
-   Le **number()** fonction n’est pas obligatoire, comme indiqué par la requête pour le **LotSizeA** attribut. Il s'agit d'une fonction XPath 1.0 qui est incluse pour garantir la compatibilité ascendante.  
  
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
  
-   Lorsque les valeurs ne peuvent pas être retournées en tant que nombre, le **number()** fonction retourne la séquence vide au lieu de NaN.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions XQuery impliquant le type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
