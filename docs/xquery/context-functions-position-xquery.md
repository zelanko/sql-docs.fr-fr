---
title: Fonction position (XQuery) | Microsoft Docs
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
- position function
- fn:position function
ms.assetid: f1bab9e4-1715-4c06-9cb0-06c7e0c9c97f
author: rothja
ms.author: jroth
ms.openlocfilehash: de9f30c3c63030aa956366c222b7cbda94e2becb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68038983"
---
# <a name="context-functions---position-xquery"></a>Fonctions relatives au contexte : position (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Renvoie une valeur entière indiquant la position de l'élément contextuel dans la séquence d'éléments en cours de traitement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
fn:position() as xs:integer  
```  
  
## <a name="remarks"></a>Notes  
 Dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], **:position()** peut uniquement être utilisé dans le contexte d’un prédicat dépendant du contexte. Plus précisément, elle ne peut être utilisée qu'entre crochets ([ ]).Toute comparaison à cette fonction ne réduit pas la cardinalité lors de l'inférence de type statique.  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type le [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] base de données.  
  
### <a name="a-using-the-position-xquery-function-to-retrieve-the-first-two-product-features"></a>R. Utilisation de la fonction XQuery position() pour récupérer les deux premières caractéristiques de produits  
 La requête suivante récupère les deux premiers composants, les deux premiers éléments enfants de la <`Features`> élément, à partir de la description du catalogue de produits. S’il existe davantage de fonctionnalités, il ajoute un <`there-is-more/`> élément au résultat.  
  
```  
SELECT CatalogDescription.query('  
     declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>   
          { /pd:ProductDescription/@ProductModelID }  
          { /pd:ProductDescription/@ProductModelName }   
          {  
            for $f in /pd:ProductDescription/pd:Features/*[position()<=2]  
            return  
            $f   
          }  
          {  
            if (count(/pd:ProductDescription/pd:Features/*) > 2)  
            then <there-is-more/>  
            else ()  
          }   
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE CatalogDescription is not null  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Le **espace de noms** mot clé dans le [prologue XQuery](../xquery/modules-and-prologs-xquery-prolog.md) définit un préfixe d’espace de noms qui est utilisé dans le corps de requête.  
  
-   Le corps de la requête construit du code XML qui a un \<produit > élément avec **ProductModelID** et **ProductModelName** des attributs et possède des fonctionnalités de produit retournées en tant qu’éléments enfants.  
  
-   Le **position()** fonction est utilisée dans le prédicat pour déterminer la position de la \<fonctionnalités > élément enfant dans le contexte. Si l'élément correspond à la première ou à la deuxième caractéristique, il est renvoyé dans les résultats.  
  
-   L’instruction IF ajoute un \<là-is-more / > élément au résultat s’il existe plus de deux fonctionnalités dans le catalogue de produits.  
  
-   Puisque les modèles de produits n'ont pas tous leur description de catalogue stockée dans la table, la clause WHERE permet de passer outre les lignes où CatalogDescriptions correspond à NULL.  
  
 Voici un extrait du résultat :  
  
```  
<Product ProductModelID="19" ProductModelName="Mountain 100">  
  <p1:Warranty xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
  </p1:Warranty>  
  <p2:Maintenance xmlns:p2="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p2:NoOfYears>10</p2:NoOfYears>  
    <p2:Description>maintenance contact available through your dealer or  
                    any AdventureWorks retail store.</p2:Description>  
  </p2:Maintenance>  
  <there-is-more/>  
</Product>   
...  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions XQuery impliquant le type de données xml](../xquery/xquery-functions-against-the-xml-data-type.md)  
  
  
