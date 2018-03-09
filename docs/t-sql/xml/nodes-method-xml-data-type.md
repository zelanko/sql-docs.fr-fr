---
title: "Méthode (Type de données xml) Nodes() | Documents Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|xml
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- nodes() method
- nodes method
ms.assetid: 7267fe1b-2e34-4213-8bbf-1c953822446c
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: f75f08164b84e803a6a54d039a09cf481a1886e9
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="nodes-method-xml-data-type"></a>Méthode nodes() (type de données xml)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Le **nodes()** méthode est utile lorsque vous souhaitez fragmenter un **xml** instance de type de données en données relationnelles. Elle vous permet d'identifier les nœuds à mapper dans une nouvelle ligne.  
  
 Chaque **xml** instance de type de données possède un nœud de contexte fourni implicitement. Pour l'instance XML stockée dans une colonne ou variable, il s'agit du nœud de document. Le nœud du document est le nœud implicite situé en haut de chaque **xml** instance de type de données.  
  
 Le résultat de la **nodes()** méthode est un ensemble de lignes qui contient des copies logiques des instances XML d’origine. Dans ces copies logiques, le nœud de contexte de chaque instance de ligne correspond à l'un des nœuds identifiés avec l'expression de requête, ce qui permet aux requêtes ultérieures de naviguer par rapport à ces nœuds de contexte.  
  
 Vous pouvez extraire plusieurs valeurs de l'ensemble de lignes. Par exemple, vous pouvez appliquer la **value()** méthode à l’ensemble de lignes retourné par **nodes()** et récupérer plusieurs valeurs à partir de l’instance XML d’origine. Notez que la **value()** lorsqu’elle est appliquée à l’instance XML, méthode retourne une seule valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
nodes (XQuery) as Table(Column)  
```  
  
## <a name="arguments"></a>Arguments  
 *XQuery*  
 Littéral de chaîne, représentant une expression XQuery. Si l'expression de requête construit des nœuds, ceux-ci sont exposés dans l'ensemble de lignes obtenu. Si l'expression de requête aboutit à une séquence vide, l'ensemble de lignes est vide. Si l'expression de requête aboutit de façon statique à une séquence qui contient des valeurs atomiques au lieu de nœuds, une erreur statique est déclenchée.  
  
 *Table*(*Column*)  
 Nom de table et nom de colonne de l'ensemble de lignes obtenu.  
  
## <a name="remarks"></a>Notes  
 Prenons par exemple la table suivante :  
  
```  
T (ProductModelID int, Instructions xml)  
```  
  
 Le document des instructions de fabrication suivant est stocké dans la table. Seule une partie de celui-ci est montrée. Le document indique trois sites de fabrication.  
  
```  
<root>  
  <Location LocationID="10"...>  
     <step>...</step>  
     <step>...</step>  
      ...  
  </Location>  
  <Location LocationID="20" ...>  
       ...  
  </Location>  
  <Location LocationID="30" ...>  
       ...  
  </Location>  
</root>  
```  
  
 Un appel de la méthode `nodes()` avec l'expression de requête `/root/Location` renverrait un ensemble de lignes composé de trois lignes, contenant chacune une copie logique du document XML d'origine et associant l'élément de contexte à l'un des nœuds `<Location>` :  
  
```  
Product  
ModelID      Instructions  
----------------------------------  
1       <root>  
             <Location LocationID="20" ... />  
             <Location LocationID="30" .../></root>  
1      <root><Location LocationID="10" ... />  
  
             <Location LocationID="30" .../></root>  
1      <root><Location LocationID="10" ... />  
             <Location LocationID="20" ... />  
             </root>  
```  
  
 Vous pouvez alors interroger cet ensemble de lignes à l’aide de **xml** méthodes du type de données. La requête suivante extrait la sous-arborescence de l'élément de contexte pour chaque ligne générée :  
  
```  
SELECT T2.Loc.query('.')  
FROM   T  
CROSS APPLY Instructions.nodes('/root/Location') as T2(Loc)   
```  
  
 Voici le résultat obtenu :  
  
```  
ProductModelID  Instructions  
----------------------------------  
1        <Location LocationID="10" ... />  
1        <Location LocationID="20" ... />  
1        <Location LocationID="30" .../>  
```  
  
 L'ensemble de lignes renvoyé a conservé les informations de type. Vous pouvez appliquer **xml** de type de données méthodes, telles que **query()**, **value()**, **exist()**, et **nodes()**, le résultat d’une **nodes()** (méthode). Toutefois, vous ne pouvez pas appliquer le **modify()** méthode permettant de modifier l’instance XML.  
  
 En outre, le nœud de contexte figurant dans l'ensemble de lignes ne peut pas être matérialisé. Vous ne pouvez donc pas l'utiliser dans une instruction SELECT. Toutefois, vous pouvez l'utiliser dans IS NULL et COUNT(*).  
  
 Scénarios d’utilisation de la **nodes()** méthode sont les mêmes que ceux [OPENXML &#40; Transact-SQL &#41; ](../../t-sql/functions/openxml-transact-sql.md). qui fournit une vue d'ensemble de lignes du document XML. Toutefois, il est inutile d’utiliser les curseurs lorsque vous utilisez la **nodes()** méthode sur une table qui contient plusieurs lignes de documents XML.  
  
 Notez que l’ensemble de lignes retourné par la **nodes()** méthode est un ensemble de lignes sans nom. Par conséquent, il doit être explicitement nommé à l'aide d'alias.  
  
 Le **nodes()** fonction ne peut pas être appliquée directement aux résultats d’une fonction définie par l’utilisateur. Pour utiliser le **nodes()** fonction avec le résultat d’une fonction scalaire définie par l’utilisateur, vous pouvez assigner le résultat de la fonction définie par l’utilisateur à une variable ou utiliser une table dérivée pour assigner une colonne un alias à la valeur de retour de fonction définie par l’utilisateur puis utiliser CROSS APPLY pour sélectionner à partir de l’alias.  
  
 L'exemple suivant illustre une utilisation de `CROSS APPLY` permettant d'opérer une sélection à partir du résultat d'une fonction définie par l'utilisateur.  
  
```  
USE AdventureWorks;  
GO  
  
CREATE FUNCTION XTest()  
RETURNS xml  
AS  
BEGIN  
RETURN '<document/>';  
END;  
GO  
  
SELECT A2.B.query('.')  
FROM  
(SELECT dbo.XTest()) AS A1(X)   
CROSS APPLY X.nodes('.') A2(B);  
GO  
  
DROP FUNCTION XTest;  
GO  
```  
  
## <a name="examples"></a>Exemples  
  
### <a name="using-nodes-method-against-a-variable-of-xml-type"></a>Utilisation de la méthode nodes() par rapport à une variable de type xml  
 Dans l'exemple suivant figure un document XML qui possède un élément de niveau supérieur <`Root`> et trois éléments enfants <`row`>. La requête utilise la méthode `nodes()` pour définir un nœud de contexte distinct par élément <`row`>. La méthode `nodes()` renvoie un ensemble de lignes composé de trois lignes. Chaque ligne possède une copie logique du document XML d'origine et chaque nœud de contexte identifie un élément <`row`> distinct de ce document.  
  
 La requête renvoie ensuite le nœud de contexte depuis chaque ligne :  
  
```  
DECLARE @x xml   
SET @x='<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>'  
SELECT T.c.query('.') AS result  
FROM   @x.nodes('/Root/row') T(c)  
GO  
```  
  
 Le résultat est le suivant. dans cet exemple, la méthode query renvoie l'élément de contexte et son contenu :  
  
```  
<row id="1"><name>Larry</name><oflw>some text</oflw></row>  
<row id="2"><name>moe</name></row>  
<row id="3"/>  
```  
  
 L'application de l'accesseur parent aux nœuds de contexte renvoie l'élément <`Root`> pour les trois lignes :  
  
```  
SELECT T.c.query('..') AS result  
FROM   @x.nodes('/Root/row') T(c)  
go  
```  
  
 Voici le résultat obtenu :  
  
```  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
<Root>  
    <row id="1"><name>Larry</name><oflw>some text</oflw></row>  
    <row id="2"><name>moe</name></row>  
    <row id="3" />  
</Root>  
```  
  
### <a name="specifying-the-nodes-method-against-a-column-of-xml-type"></a>Spécification de la méthode nodes() par rapport à une colonne de type xml  
 Les instructions de fabrication des bicyclettes sont utilisées dans cet exemple et sont stockées dans les Instructions **xml** colonne de type de la **ProductModel** table.  
  
 Dans l’exemple suivant, la `nodes()` méthode est spécifiée sur le `Instructions` colonne de **xml** de type dans le `ProductModel` table.  
  
 La méthode `nodes()` définit les éléments <`Location`> en tant que nœuds de contexte en spécifiant le chemin d'accès `/MI:root/MI:Location`. L'ensemble de lignes obtenu comprend une copie logique du document d'origine par nœud <`Location`> du document et le nœud de contexte a pour valeur l'élément <`Location`>. Par conséquent, la fonction `nodes()` fournit un ensemble de nœuds de contexte <`Location`>.  
  
 La méthode `query()` appliquée à cet ensemble de lignes demande `self::node` et, par conséquent, renvoie l'élément `<Location>` de chaque ligne.  
  
 Dans cet exemple, la requête définit chaque élément <`Location`> en tant que nœud de contexte du document d'instructions de fabrication d'un modèle de produit spécifique. Ces nœuds de contexte vous permettent d'effectuer les opérations d'extraction suivantes :  
  
-   Rechercher les codes d’emplacement de chaque <`Location`>  
  
-   Récupérer les étapes de fabrication (<`step`> des éléments enfants) dans chaque <`Location`>  
  
 Cette requête renvoie l'élément de contexte, dans lequel est spécifiée la syntaxe abrégée `'.'` de `self::node()`, dans la méthode `query()`.  
  
 Notez les points suivants :  
  
-   La méthode `nodes()` est appliquée à la colonne Instructions et renvoie l'ensemble de lignes `T (C)`. Cet ensemble de lignes contient des copies logiques du document d'origine des instructions de fabrication et indique `/root/Location` en guise d'élément de contexte.  
  
-   CROSS APPLY applique `nodes()` à chaque ligne de la table `Instructions` et renvoie uniquement les lignes qui génèrent un ensemble de résultats.  
  
    ```  
    SELECT C.query('.') as result  
    FROM Production.ProductModel  
    CROSS APPLY Instructions.nodes('  
    declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
    /MI:root/MI:Location') as T(C)  
    WHERE ProductModelID=7  
    ```  
  
     Voici le résultat partiel :  
  
    ```  
    <MI:Location LocationID="10"  ...>  
       <MI:step ... />  
          ...  
    </MI:Location>  
    <MI:Location LocationID="20"  ... >  
        <MI:step ... />  
          ...  
    </MI:Location>  
    ...  
    ```  
  
### <a name="applying-nodes-to-the-rowset-returned-by-another-nodes-method"></a>Application de la méthode nodes() à l'ensemble de lignes renvoyé par une autre méthode nodes()  
 Le code suivant interroge les documents XML des instructions de fabrication stockés dans la colonne `Instructions` de la table `ProductModel`. La requête renvoie un ensemble de lignes qui contient l'ID du modèle de produit, ainsi que les sites et les étapes de fabrication.  
  
 Notez les points suivants :  
  
-   La méthode `nodes()` est appliquée à la colonne `Instructions` et renvoie l'ensemble de lignes `T1 (Locations)`. Cet ensemble de lignes contient des copies logiques du document d'origine des instructions de fabrication et indique `/root/Location` en guise de contexte d'élément.  
  
-   `nodes()` est appliqué à l'ensemble de lignes `T1 (Locations)` et renvoie l'ensemble de lignes `T2 (steps)`. Cet ensemble de lignes contient des copies logiques du document d'origine des instructions de fabrication et indique `/root/Location/step` en guise de contexte d'élément.  
  
```  
SELECT ProductModelID, Locations.value('./@LocationID','int') as LocID,  
steps.query('.') as Step         
FROM Production.ProductModel         
CROSS APPLY Instructions.nodes('         
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
/MI:root/MI:Location') as T1(Locations)         
CROSS APPLY T1.Locations.nodes('         
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";         
./MI:step ') as T2(steps)         
WHERE ProductModelID=7         
GO         
```  
  
 Voici le résultat obtenu :  
  
```  
ProductModelID LocID Step         
----------------------------         
7      10   <step ... />         
7      10   <step ... />         
...         
7      20   <step ... />         
7      20   <step ... />         
7      20   <step ... />         
...         
```  
  
 La requête déclare le préfixe `MI` deux fois. À la place, vous pouvez recourir à `WITH XMLNAMESPACES` pour déclarer le préfixe une fois et l'utiliser dans la requête :  
  
```  
WITH XMLNAMESPACES (  
   'http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions'  AS MI)  
  
SELECT ProductModelID, Locations.value('./@LocationID','int') as LocID,  
steps.query('.') as Step         
FROM Production.ProductModel         
CROSS APPLY Instructions.nodes('         
/MI:root/MI:Location') as T1(Locations)         
CROSS APPLY T1.Locations.nodes('         
./MI:step ') as T2(steps)         
WHERE ProductModelID=7         
GO    
```  
  
## <a name="see-also"></a>Voir aussi  
 [Ajouter des espaces de noms aux requêtes avec WITH XMLNAMESPACES](../../relational-databases/xml/add-namespaces-to-queries-with-with-xmlnamespaces.md)   
 [Créer des instances de données XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [Méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)  
  
  
