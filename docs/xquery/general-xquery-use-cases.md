---
title: Cas d’utilisation de XQuery général | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- XQuery, general usage cases
ms.assetid: 5187c97b-6866-474d-8bdb-a082634039cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 1e844425f0c512cfe7c15354bf1aeb100d6104e2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004526"
---
# <a name="general-xquery-use-cases"></a>Cas d'emploi généraux des requêtes XQuery
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Cette rubrique donne des exemples généraux d'emploi de requêtes XQuery.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-query-catalog-descriptions-to-find-products-and-weights"></a>R. Interrogation des descriptions d'un catalogue pour rechercher des produits et des poids  
 La requête suivante renvoie les ID de modèle de produit et les poids, le cas échéant, de la description du catalogue de produits. La requête construit du code XML se présentant sous la forme suivante :  
  
```  
<Product ProductModelID="...">  
  <Weight>...</Weight>  
</Product>  
```  
  
 Voici la requête :  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  <Product  ProductModelID="{ (/p1:ProductDescription/@ProductModelID)[1] }">  
     {   
       /p1:ProductDescription/p1:Specifications/Weight   
     }   
  </Product>  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription is not null  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Le **espace de noms** mot clé dans le prologue XQuery définit un préfixe d’espace de noms qui est utilisé dans le corps de requête.  
  
-   Le corps de la requête construit le code XML requis.  
  
-   Dans la clause WHERE, le **exist()** méthode est utilisée pour rechercher uniquement les lignes qui contiennent des descriptions de catalogue de produits. Autrement dit, le code XML qui contient le <`ProductDescription`> élément.  
  
 Voici le résultat obtenu :  
  
```  
<Product ProductModelID="19"/>  
<Product ProductModelID="23"/>   
<Product ProductModelID="25"/>   
<Product ProductModelID="28"><Weight>Varies with size.</Weight></Product>  
<Product ProductModelID="34"/>  
<Product ProductModelID="35"/>  
```  
  
 La requête suivante récupère les mêmes informations, mais uniquement pour les modèles de produit dont la description du catalogue mentionne le poids, le <`Weight`> élément, dans les spécifications, la <`Specifications`> élément. Cet exemple utilise WITH XMLNAMESPACES pour déclarer le préfixe pd et sa liaison d'espace de noms. De cette façon, la liaison n’est pas décrite dans les deux le **query()** (méthode) et dans le **exist()** (méthode).  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT CatalogDescription.query('  
          <Product  ProductModelID="{ (/pd:ProductDescription/@ProductModelID)[1] }">  
                 {   
                      /pd:ProductDescription/pd:Specifications/Weight   
                 }   
          </Product>  
') as x  
FROM Production.ProductModel  
WHERE CatalogDescription.exist('/pd:ProductDescription/pd:Specifications//Weight ') = 1  
```  
  
 Dans la requête précédente, la **exist()** méthode de la **xml** type de données dans la clause WHERE vérifie s’il existe un <`Weight`> élément dans le <`Specifications`> élément.  
  
### <a name="b-find-product-model-ids-for-product-models-whose-catalog-descriptions-include-front-angle-and-small-size-pictures"></a>B. Recherche des ID des modèles de produit dont les descriptions englobent des illustrations de face et de petite taille  
 La description de catalogue de produits XML inclut les images de produit, le <`Picture`> élément. Chaque illustration a plusieurs propriétés dont Ceux-ci incluent l’angle de l’image, le <`Angle`> élément et la taille, le <`Size`> élément.  
  
 Pour les modèles de produit dont les descriptions du catalogue englobent des illustrations de face et de petite taille, la requête construit le code XML sous la forme suivante :  
  
```  
< Product ProductModelID="...">  
  <Picture>  
    <Angle>front</Angle>  
    <Size>small</Size>  
  </Picture>  
</Product>  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT CatalogDescription.query('  
   <pd:Product  ProductModelID="{ (/pd:ProductDescription/@ProductModelID)[1] }">  
      <Picture>  
         {  /pd:ProductDescription/pd:Picture/pd:Angle }   
         {  /pd:ProductDescription/pd:Picture/pd:Size }   
      </Picture>  
   </pd:Product>  
') as Result  
FROM  Production.ProductModel  
WHERE CatalogDescription.exist('/pd:ProductDescription/pd:Picture') = 1  
AND   CatalogDescription.value('(/pd:ProductDescription/pd:Picture/pd:Angle)[1]', 'varchar(20)')  = 'front'  
AND   CatalogDescription.value('(/pd:ProductDescription/pd:Picture/pd:Size)[1]', 'varchar(20)')  = 'small'  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Dans la clause WHERE, le **exist()** méthode est utilisée pour récupérer uniquement les lignes qui ont produit des descriptions de catalogue avec le <`Picture`> élément.  
  
-   La clause WHERE utilise le **value()** méthode deux fois afin de comparer les valeurs de la <`Size`> et <`Angle`> éléments.  
  
 Voici un extrait du résultat :  
  
```  
<p1:Product   
  xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription"   
  ProductModelID="19">  
  <Picture>  
    <p1:Angle>front</p1:Angle>  
    <p1:Size>small</p1:Size>  
  </Picture>  
</p1:Product>  
...  
```  
  
### <a name="c-create-a-flat-list-of-the-product-model-name-and-feature-pairs-with-each-pair-enclosed-in-the-features-element"></a>C. Créer une liste plate du produit paires nom et caractéristique du modèle, chaque paire étant comprise dans le \<fonctionnalités > élément  
 Dans la description du catalogue de produits, le code XML englobe plusieurs caractéristiques du produit. Toutes ces fonctionnalités sont incluses dans le <`Features`> élément. La requête utilise [Construction XML (XQuery)](../xquery/xml-construction-xquery.md) pour construire le code XML requis. L'expression entre accolades est remplacée par le résultat.  
  
```  
SELECT CatalogDescription.query('  
declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
  for $pd in /p1:ProductDescription,  
   $f in $pd/p1:Features/*  
  return  
   <Feature>  
     <ProductModelName> { data($pd/@ProductModelName) } </ProductModelName>  
     { $f }  
  </Feature>          
') as x  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   $pd / P1 : Features / * renvoie uniquement l’élément enfants du nœud <`Features`>, mais $pd / P1 :Features/Node() renvoie tous les nœuds. notamment les nœuds d'élément et de texte, les instructions de traitement et les commentaires.  
  
-   Les deux boucles FOR génèrent un produit cartésien à partir duquel le nom du produit et ses caractéristiques sont renvoyés.  
  
-   Le **ProductName** est un attribut. La construction XML de cette requête le renvoie sous forme d'élément.  
  
 Voici un extrait du résultat :  
  
```  
<Feature>  
 <ProductModelName>Mountain 100</ProductModelName>  
 <ProductModelID>19</ProductModelID>  
 <p1:Warranty   
   xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p1:WarrantyPeriod>3 year</p1:WarrantyPeriod>  
    <p1:Description>parts and labor</p1:Description>  
 </p1:Warranty>  
</Feature>  
<Feature>  
 <ProductModelName>Mountain 100</ProductModelName>  
 <ProductModelID>19</ProductModelID>  
 <p2:Maintenance xmlns:p2="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain">  
    <p2:NoOfYears>10</p2:NoOfYears>  
    <p2:Description>maintenance contact available through your dealer   
           or any AdventureWorks retail store.</p2:Description>  
    </p2:Maintenance>  
</Feature>  
...  
...      
```  
  
### <a name="d-from-the-catalog-description-of-a-product-model-list-the-product-model-name-model-id-and-features-grouped-inside-a-product-element"></a>D. À partir de la description du catalogue d’un modèle de produit, les ID de nom, le modèle de modèle de liste du produit et de fonctionnalités regroupement à l’intérieur d’un \<produit > élément  
 En utilisant les informations stockées dans la description du catalogue du modèle de produit, la requête suivante répertorie le nom du modèle de produit, ID de modèle, et les fonctionnalités regroupées à l’intérieur d’un \<produit > élément.  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
     declare namespace pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     <Product>  
         <ProductModelName>   
           { data(/pd:ProductDescription/@ProductModelName) }   
         </ProductModelName>  
         <ProductModelID>   
           { data(/pd:ProductDescription/@ProductModelID) }   
         </ProductModelID>  
         { /pd:ProductDescription/pd:Features/* }  
     </Product>          
') as x  
FROM Production.ProductModel  
WHERE ProductModelID=19  
```  
  
 Voici un extrait du résultat :  
  
```  
<Product>  
  <ProductModelName>Mountain 100</ProductModelName>  
  <ProductModelID>19</ProductModelID>  
  <p1:Warranty>... </p1:Warranty>  
  <p2:Maintenance>...  </p2:Maintenance>  
  <p3:wheel xmlns:p3="https://www.adventure-works.com/schemas/OtherFeatures">High performance wheels.</p3:wheel>  
  <p4:saddle xmlns:p4="https://www.adventure-works.com/schemas/OtherFeatures">  
    <p5:i xmlns:p5="http://www.w3.org/1999/xhtml">Anatomic design</p5:i> and made from durable leather for a full-day of riding in comfort.</p4:saddle>  
  <p6:pedal xmlns:p6="https://www.adventure-works.com/schemas/OtherFeatures">  
    <p7:b xmlns:p7="http://www.w3.org/1999/xhtml">Top-of-the-line</p7:b> clipless pedals with adjustable tension.</p6:pedal>  
   ...  
```  
  
### <a name="e-retrieve-product-model-feature-descriptions"></a>E. Récupération de la description des caractéristiques d'un modèle de produit  
 La requête suivante construit le document XML qui comprend un <`Product`> élément qui a **ProducModelID**, **ProductModelName** attributs et les premier deux caractéristiques du produit. Plus précisément, les premier deux caractéristiques du produit sont les deux premiers éléments enfants de la <`Features`> élément. S’il existe davantage de fonctionnalités, il retourne un vide <`There-is-more/`> élément.  
  
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
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription is not NULL  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   FOR... La boucle RETURN récupère les premier deux caractéristiques du produit. Le **position()** fonction est utilisée pour rechercher la position des éléments dans la séquence.  
  
### <a name="f-find-element-names-from-the-product-catalog-description-that-end-with-ons"></a>F. Recherche de noms d'élément se terminant par « ons », d'après les descriptions du catalogue de produits  
 La requête suivante recherche dans les descriptions du catalogue et retourne tous les éléments dans le <`ProductDescription`> élément dont le nom se termine par « ons ».  
  
```  
SELECT ProductModelID, CatalogDescription.query('  
     declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
      for $pd in /p1:ProductDescription/*[substring(local-name(.),string-length(local-name(.))-2,3)="ons"]  
      return   
          <Root>  
             { $pd }  
          </Root>  
') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription is not NULL  
```  
  
 Voici un extrait du résultat :  
  
```  
ProductModelID   Result  
-----------------------------------------  
         19        <Root>         
                     <p1:Specifications xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">          
                          ...         
                     </p1:Specifications>         
                   </Root>          
```  
  
### <a name="g-find-summary-descriptions-that-contain-the-word-aerodynamic"></a>G. Recherche des descriptions résumées qui contiennent le mot « Aerodynamic »  
 La requête suivante récupère les modèles de produit dont les descriptions du catalogue contiennent le mot « Aerodynamic » dans la description résumée :  
  
```  
WITH XMLNAMESPACES ('https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription' AS pd)  
SELECT ProductModelID, CatalogDescription.query('  
          <Prod >  
             { /pd:ProductDescription/@ProductModelID }  
             { /pd:ProductDescription/pd:Summary }  
          </Prod>  
 ') as Result  
FROM Production.ProductModel  
WHERE CatalogDescription.value('  
     contains( string( (/pd:ProductDescription/pd:Summary)[1] ),"Aerodynamic")','bit') = 1  
```  
  
 Notez que la requête SELECT spécifie **query()** et **value()** méthodes de la **xml** type de données. Par conséquent, au lieu de répéter deux fois la déclaration des espaces de noms dans deux prologues de requête différents, le préfixe pd est utilisé dans la requête, puis défini une seule fois à l'aide de WITH XMLNAMESPACES.  
  
 Notez les points suivants dans la requête précédente :  
  
-   La clause WHERE est utilisée pour récupérer uniquement les lignes où la description du catalogue contient le mot « Aerodynamic » dans le <`Summary`> élément.  
  
-   Le **contains()** fonction sert à déterminer si le mot est inclus dans le texte.  
  
-   Le **value()** méthode de la **xml** type de données compare la valeur retournée par **contains()** à 1.  
  
 Voici le résultat obtenu :  
  
```  
ProductModelID Result        
-------------- ------------------------------------------  
28     <Prod ProductModelID="28">  
        <pd:Summary xmlns:pd="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
       <p1:p xmlns:p1="http://www.w3.org/1999/xhtml">  
         A TRUE multi-sport bike that offers streamlined riding and a  
         revolutionary design. Aerodynamic design lets you ride with the   
         pros, and the gearing will conquer hilly roads.</p1:p>  
       </pd:Summary>  
      </Prod>    
```  
  
### <a name="h-find-product-models-whose-catalog-descriptions-do-not-include-product-model-pictures"></a>H. Recherche de modèles de produit dont les descriptions du catalogue ne s'accompagnent pas d'illustrations  
 La requête suivante extrait ProductModelIDs modèles de produit dont descriptions du catalogue ne pas inclure un <`Picture`> élément.  
  
```  
SELECT  ProductModelID  
FROM    Production.ProductModel  
WHERE   CatalogDescription is not NULL  
AND     CatalogDescription.exist('declare namespace p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription";  
     /p1:ProductDescription/p1:Picture  
') = 0  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   Si le **exist()** méthode dans la clause WHERE renvoie False (0), l’ID de modèle de produit est retourné. Dans le cas contraire, aucune donnée n'est renvoyée.  
  
-   Étant donné que toutes les descriptions de produit incluent un <`Picture`> élément, le jeu de résultats est vide dans ce cas.  
  
## <a name="see-also"></a>Voir aussi  
 [Requêtes XQuery impliquant une hiérarchie](../xquery/xqueries-involving-hierarchy.md)   
 [Requêtes XQuery impliquant un ordre](../xquery/xqueries-involving-order.md)   
 [Requêtes XQuery pour la gestion des données relationnelles](../xquery/xqueries-handling-relational-data.md)   
 [Recherche de chaînes dans XQuery](../xquery/string-search-in-xquery.md)   
 [Gestion des espaces de noms dans XQuery](../xquery/handling-namespaces-in-xquery.md)   
 [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Données XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Références relatives au langage Xquery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)  
  
  
