---
title: Spécification de l’axe dans une étape d’Expression de chemin d’accès | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- attribute axis [SQL Server]
- axis step [XQuery]
- descendant axis
- self axis
- path expressions [XQuery]
- child axis
- descendant-or-self axis
- parent axis
ms.assetid: c44fb843-0626-4496-bde0-52ca0bac0a9e
author: rothja
ms.author: jroth
ms.openlocfilehash: 07058816406ef6ac0d5a3356423e231a10ce6165
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946482"
---
# <a name="path-expressions---specifying-axis"></a>Expressions de chemin : spécification de l’axe
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Une étape d'axe dans une expression de chemin d'accès inclut les composants suivants :  
  
-   Axe  
  
-   Un [test de nœud](../xquery/path-expressions-specifying-node-test.md)  
  
-   [Zéro ou plusieurs qualificateurs d’étape (facultatifs)](../xquery/path-expressions-specifying-predicates.md)  
  
 Pour plus d’informations, consultez [Expressions de chemin &#40;XQuery&#41;](../xquery/path-expressions-xquery.md).  
  
 L'implémentation de XQuery dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prend en charge les étapes d'axe suivantes :  
  
|Axis|Description|  
|----------|-----------------|  
|**child**|Retourne l'enfant du nœud du contexte.|  
|**descendant**|Retourne tous les descendants du nœud du contexte.|  
|**parent**|Retourne le parent du nœud du contexte.|  
|**attribute**|Retourne les attributs du nœud du contexte.|  
|**self**|Retourne le nœud du contexte lui-même.|  
|**descendant-or-self**|Retourne le nœud du contexte et tous ses descendants.|  
  
 Tous ces axes, sauf le **parent** axe, sont des axes vers l’avant. Le **parent** axe est un axe vers l’arrière, parce qu’il recherche vers l’arrière dans la hiérarchie du document. Par exemple, l'expression de chemin d'accès relative `child::ProductDescription/child::Summary` comprend deux étapes, chacune spécifiant un axe `child`. La première étape extrait le \<ProductDescription > éléments enfants du nœud de contexte. Pour chaque \<ProductDescription > nœud d’élément, la seconde étape extrait le \<Résumé > enfants du nœud élément.  
  
 L'expression de chemin d'accès relative `child::root/child::Location/attribute::LocationID` comporte quant à elle trois étapes. Les deux premières définissent un axe `child`, et la troisième, un axe `attribute`. Lorsque les instructions de fabrication exécutée des documents XML dans le **Production.ProductModel** table, l’expression retourne la `LocationID` attribut de la \<emplacement > enfant de nœud d’élément de la \<racine > élément.  
  
## <a name="examples"></a>Exemples  
 Les exemples de requête dans cette rubrique sont définis sur **xml** colonnes de type le **AdventureWorks** base de données.  
  
### <a name="a-specifying-a-child-axis"></a>R. Spécification de l'axe enfant  
 Pour un modèle de produit spécifique, la requête suivante extrait le \<fonctionnalités > enfants de nœud d’élément de la \<ProductDescription > nœud d’élément à partir de la description du catalogue de produits stockée dans le `Production.ProductModel` table.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features')  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Le `query()` méthode de la **xml** type de données spécifie l’expression de chemin d’accès.  
  
-   Les deux étapes de cette expression définissent un axe `child` et les noms des nœuds, `ProductDescription` et `Features` en tant que tests de nœuds. Pour plus d’informations sur les tests de nœud, consultez [spécification de Test de nœud dans une étape d’Expression de chemin d’accès](../xquery/path-expressions-specifying-node-test.md).  
  
### <a name="b-specifying-descendant-and-descendant-or-self-axes"></a>B. Définition des axes descendant et descendant-or-self  
 L'exemple ci-dessous utilise des axes descendant et descendant-or-self. La requête dans cet exemple est spécifiée par rapport à un **xml** variable de type. L'instance XML est simplifiée pour illustrer facilement la différence dans les résultats générés.  
  
```  
declare @x xml  
set @x='  
<a>  
 <b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
 </b>  
</a>'  
declare @y xml  
set @y = @x.query('  
  /child::a/child::b  
')  
select @y  
```  
  
 Dans le résultat suivant, l'expression retourne l'enfant `<b>` du nœud d'élément `<a>` :  
  
```  
<b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
</b>  
```  
  
 Dans cette expression, si vous spécifiez un axe descendant pour l'expression de chemin d'accès,  
  
 `/child::a/child::b/descendant::*`, vous demandez tous les descendants de le <`b`> nœud d’élément.  
  
 L'astérisque (*) dans le test de nœud représente le nom du nœud comme un test de nœud. Par conséquent, le type de nœud principal de l'axe descendant, le nœud d'élément, détermine les types de nœuds retournés. En d'autres termes, l'expression retourne tous les nœuds d'élément. Les nœuds de texte sont retournés. Pour plus d’informations sur le type de nœud principal et sa relation avec le test de nœud, consultez [spécifiant des Test de nœud dans une étape d’Expression de chemin d’accès](../xquery/path-expressions-specifying-node-test.md) rubrique.  
  
 Les nœuds d’élément <`c`> et <`d`> sont retournés, comme indiqué dans le résultat suivant :  
  
```  
<c>text2  
     <d>text3</d>  
</c>  
<d>text3</d>  
```  
  
 Si vous spécifiez un axe descendant-or-self au lieu de l’axe descendant, `/child::a/child::b/descendant-or-self::*` renvoie le nœud de contexte, élément <`b`> et de ses descendants.  
  
 Voici le résultat obtenu :  
  
```  
<b>text1  
   <c>text2  
     <d>text3</d>  
   </c>  
</b>  
  
<c>text2  
     <d>text3</d>  
</c>  
  
<d>text3</d>   
```  
  
 L’exemple de requête suivant sur le **AdventureWorks** base de données récupère tous les nœuds éléments descendants de le <`Features`> élément enfant de la <`ProductDescription`> élément :  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  /child::PD:ProductDescription/child::PD:Features/descendant::*  
')  
FROM  Production.ProductModel  
WHERE ProductModelID=19  
```  
  
### <a name="c-specifying-a-parent-axis"></a>C. Spécification de l'axe parent  
 La requête suivante retourne le <`Summary`> élément enfant de la <`ProductDescription`> élément dans le document XML de catalogue produit stockées dans le `Production.ProductModel` table.  
  
 Cet exemple utilise l’axe parent pour retourner au parent de la <`Feature`> élément et récupérer le <`Summary`> élément enfant de la <`ProductDescription`> élément.  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  
/child::PD:ProductDescription/child::PD:Features/parent::PD:ProductDescription/child::PD:Summary  
')  
FROM   Production.ProductModel  
WHERE  ProductModelID=19  
  
```  
  
 Dans cette requête, l'expression de chemin d'accès utilise l'axe `parent`. Vous pouvez la réécrire sans l'axe parent, comme ceci :  
  
```  
/child::PD:ProductDescription[child::PD:Features]/child::PD:Summary  
```  
  
 L'exemple ci-dessous illustre un emploi plus utile de l'axe parent.  
  
 Chaque description de catalogue de modèles de produits stockée dans le **CatalogDescription** colonne de la **ProductModel** table a un `<ProductDescription>` élément qui possède le `ProductModelID` attribut et `<Features>`élément enfant, comme indiqué dans le fragment suivant :  
  
```  
<ProductDescription ProductModelID="..." >  
  ...  
  <Features>  
    <Feature1>...</Feature1>  
    <Feature2>...</Feature2>  
   ...  
</ProductDescription>  
```  
  
 La requête définit une variable itérateur, `$f`, dans l'instruction FLWOR afin de retourner l'enfant de l'élément `<Features>`. Pour plus d’informations, consultez [instruction et itération FLWOR &#40;XQuery&#41;](../xquery/flwor-statement-and-iteration-xquery.md). Pour chaque fonctionnalité, la clause `return` construit du code XML au format suivant :  
  
```  
<Feature ProductModelID="...">...</Feature>  
<Feature ProductModelID="...">...</Feature>  
```  
  
 Pour ajouter le `ProductModelID` pour chaque `<Feature`> élément, le `parent` axe est spécifié :  
  
```  
SELECT CatalogDescription.query('  
declare namespace PD="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
declare namespace wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain";  
  for $f in /child::PD:ProductDescription/child::PD:Features/child::*  
  return  
   <Feature  
     ProductModelID="{ ($f/parent::PD:Features/parent::PD:ProductDescription/attribute::ProductModelID)[1]}" >  
          { $f }  
   </Feature>  
')  
FROM  Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Voici le résultat partiel :  
  
```  
<Feature ProductModelID="19">  
  <wm:Warranty   
   xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <wm:WarrantyPeriod>3 years</wm:WarrantyPeriod>  
    <wm:Description>parts and labor</wm:Description>  
  </wm:Warranty>  
</Feature>  
<Feature ProductModelID="19">  
  <wm:Maintenance   
   xmlns:wm="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <wm:NoOfYears>10 years</wm:NoOfYears>  
    <wm:Description>maintenance contract available through your dealer   
                  or any AdventureWorks retail store.</wm:Description>  
  </wm:Maintenance>  
</Feature>  
<Feature ProductModelID="19">  
  <p1:wheel   
   xmlns:p1="https://www.adventure-works.com/schemas/OtherFeatures">  
      High performance wheels.  
  </p1:wheel>  
</Feature>  
```  
  
 Notez que le prédicat `[1]` dans l'expression de chemin d'accès est ajouté pour garantir qu'une valeur singleton est retournée.  
  
  
