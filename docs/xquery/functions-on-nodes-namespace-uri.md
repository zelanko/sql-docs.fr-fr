---
title: Fonction namespace-uri (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:namespace-uri function
- namespace-uri function
ms.assetid: 9b48d216-26c8-431d-9ab4-20ab187917f4
author: rothja
ms.author: jroth
ms.openlocfilehash: 05412c69aa121b9de14f2bab16555db2a8a4fdb4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67929940"
---
# <a name="functions-on-nodes---namespace-uri"></a>Fonctions sur les nœuds : namespace-uri
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne l’espace de noms URI du nom qualifié spécifié dans *$arg* comme un xs : String.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
fn:namespace-uri() as xs:string  
fn:namespace-uri($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 Nom de nœud dont la partie URI d'espace de noms doit être extraite.  
  
## <a name="remarks"></a>Notes  
  
-   Si l'argument est omis, la valeur par défaut est le nœud de contexte.  
  
-   Dans SQL Server, **fn :namespace-URI()** sans argument peut uniquement être utilisé dans le contexte d’un prédicat dépendant du contexte. Autrement dit, elle ne peut être utilisée qu'à l'intérieur de crochets ([ ]).  
  
-   Si *$arg* est la séquence vide, la chaîne de longueur nulle est retournée.  
  
-   Si *$arg* est un élément ou nœud d’attribut dont le QName étendu n’est pas dans un espace de noms, la fonction retourne la chaîne de longueur nulle  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
### <a name="a-retrieve-namespace-uri-of-a-specific-node"></a>R. Extraction de l'URI d'espace de noms d'un nœud spécifique  
 La requête suivante est spécifiée sur une instance XML non typée. L'expression de requête, `namespace-uri(/ROOT[1])`, extrait la partie URI d'espace de noms du nœud spécifié.  
  
```  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('namespace-uri(/ROOT[1])')  
```  
  
 Étant donné que le QName spécifié ne possède pas la partie URI d'espace de noms mais uniquement la partie nom local, le résultat est une chaîne nulle.  
  
 La requête suivante porte sur les Instructions tapées **xml** colonne. L’expression, `namespace-uri(/AWMI:root[1]/AWMI:Location[1])`, retourne l’URI de la première de l’espace de noms <`Location`> élément enfant de la <`root`> élément.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     namespace-uri(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 Voici le résultat obtenu :  
  
```  
https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions  
```  
  
### <a name="b-using-namespace-uri-without-argument-in-a-predicate"></a>B. Utilisation de namespace-uri() sans argument dans un prédicat  
 La requête suivante porte sur la colonne xml typée CatalogDescription. L'expression renvoie tous les nœuds d'élément dont l'URI d'espace de noms est `https://www.adventure-works.com/schemas/OtherFeatures`. L’espace de noms -**uri()** est spécifiée sans argument de fonction et utilise le nœud de contexte.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
   /p1:ProductDescription//*[namespace-uri() = "https://www.adventure-works.com/schemas/OtherFeatures"]  
') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Le résultat partiel est :  
  
```  
<p1:wheel xmlns:p1="https://www.adventure-works.com/schemas/OtherFeatures">High performance wheels.</p1:wheel>  
<p2:saddle xmlns:p2="https://www.adventure-works.com/schemas/OtherFeatures">  
  <p3:i xmlns:p3="http://www.w3.org/1999/xhtml">Anatomic design</p3:i> and made from durable leather for a full-day of riding in comfort.</p2:saddle>  
...  
```  
  
 Vous pouvez remplacer l'URI d'espace de noms dans la requête précédente par `https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain`. Vous allez ensuite recevoir tous les enfants de nœud d’élément de la <`ProductDescription`> élément dont la partie URI espace de noms du nom qualifié développé est `https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain`.  
  
### <a name="implementation-limitations"></a>Limites de mise en œuvre  
 Les limitations suivantes s'appliquent :  
  
-   Le **namespace-uri()** fonction retourne des instances de type xs : String au lieu de xs : anyURI.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions sur les nœuds](https://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [Fonction local-name &#40;XQuery&#41;](../xquery/functions-on-nodes-local-name.md)  
  
  
