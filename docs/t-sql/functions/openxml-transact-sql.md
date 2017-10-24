---
title: OPENXML (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- OPENXML_TSQL
- OPENXML
dev_langs:
- TSQL
helpviewer_keywords:
- OPENXML statement
- rowsets [SQL Server], XML documents
- XML [SQL Server], rowset views
ms.assetid: 8088b114-7d01-435a-8e0d-b81abacc86d6
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ff4578d88cdb76468d261843c36043ef4696d92c
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="openxml-transact-sql"></a>OPENXML (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  OPENXML fournit une vue de l'ensemble des lignes d'un document XML. En tant que fournisseur d'ensembles de lignes, OPENXML peut être inclus dans les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] dans lesquelles certains fournisseurs d'ensembles de lignes peuvent apparaître (notamment une table, une vue ou la fonction OPENROWSET).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
OPENXML( idoc int [ in] , rowpattern nvarchar [ in ] , [ flags byte [ in ] ] )   
[ WITH ( SchemaDeclaration | TableName ) ]  
```  
  
## <a name="arguments"></a>Arguments  
 *IDOC*  
 Descripteur de document utilisé pour la représentation interne d'un document XML. La représentation interne d’un document XML est créée en appelant **sp_xml_preparedocument**.  
  
 *rowpattern*  
 Correspond au modèle XPath utilisé pour identifier les nœuds (dans le document XML dont le descripteur est transmis dans le *idoc* paramètre) à traiter comme des lignes.  
  
 *indicateurs*  
 Indique le mappage qui doit être utilisé entre les données XML et l'ensemble de lignes relationnel, ainsi que le mode de remplissage de la colonne de débordement. *indicateurs* est un paramètre d’entrée facultatif et peut prendre l’une des valeurs suivantes.  
  
|Valeur d'octet| Description|  
|----------------|-----------------|  
|**0**|Valeur par défaut est **centré** mappage.|  
|**1**|Utilisez le **centré** mappage. Peut être combiné avec XML_ELEMENTS. Dans ce cas, **centré** est appliqué en premier lieu, puis **centré sur l’élément** est appliqué pour toutes les colonnes qui ne sont pas encore été traitées avec.|  
|**2**|Utilisez le **centré** mappage. Peut être combiné avec XML_ATTRIBUTES. Dans ce cas, **centré** est appliqué en premier lieu, puis **centré sur l’élément** est appliqué pour toutes les colonnes non encore traitées.|  
|**8**|Peut être combiné (à l'aide de l'opérateur logique OR) avec XML_ATTRIBUTES ou XML_ELEMENTS. Dans le contexte d’extraction, cet indicateur indique que les données consommées ne doivent pas être copiées vers la propriété de dépassement de capacité  **@mp:xmltext** .|  
  
 *SchemaDeclaration*  
 Définition de schéma du formulaire : *ColName**ColType* [*ColPattern* | *métapropriété*] [**,***ColNameColType* [*ColPattern* | *métapropriété*]...]  
  
 *Nom de colonne*  
 Nom de la colonne dans l'ensemble de lignes.  
  
 *ColType*  
 Type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de la colonne dans l'ensemble de lignes. Si les types de colonnes diffèrent sous-jacent **xml** type de données de l’attribut, le forçage de type se produit.  
  
 *ColPattern*  
 Modèle XPath général et optionnel, qui décrit les modalités de mappage des nœuds XML vers les colonnes. Si *ColPattern* n’est pas spécifié, le mappage par défaut (**centré** ou **centré sur l’élément** par *indicateurs*) a lieu.  
  
 Le modèle XPath spécifié en tant que *ColPattern* est utilisée pour spécifier la nature particulière du mappage (dans le cas de **centré** et **centré sur l’élément** mappage) qui remplace ou améliore le mappage par défaut indiqué par *indicateurs*.  
  
 Le modèle XPath général spécifié en tant que *ColPattern* prend également en charge les métapropriétés.  
  
 *Métapropriétés*  
 L'une des métapropriétés fournies par OPENXML. Si *métapropriété* est spécifié, la colonne contienne des informations fournies par cette dernière. Les métapropriétés vous permettent d'extraire des informations (telles que la position relative et les informations sur l'espace de noms) concernant les nœuds XML. Vous disposez ainsi de plus d'informations que n'en propose la représentation textuelle.  
  
 *TableName*  
 Le nom de table qui peut être donné (au lieu de *SchemaDeclaration*) si une table comportant le schéma souhaité existe déjà et qu’aucun modèle de colonne est requis.  
  
## <a name="remarks"></a>Notes  
 La clause WITH fournit un format d’ensemble de lignes (et autres informations de mappage en fonction des besoins) à l’aide *SchemaDeclaration* ou en spécifiant un existant *TableName*. Si la clause WITH facultative n’est pas spécifiée, les résultats sont retournés dans un **bord** format de table. Les tables edge représentent la structure à granularité fine des documents XML (par exemple, les noms d'élément/d'attribut, la hiérarchie du document, les espaces de noms, les instructions de traitement, etc.) dans une seule table.  
  
 Le tableau suivant décrit la structure de la **bord** table.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**bigint**|ID unique du nœud du document.<br /><br /> L’élément racine a une valeur d’ID 0. Les valeurs négatives d'ID sont réservées.|  
|**parentid**|**bigint**|Identifie le parent du nœud. Le parent identifié par cet ID n'est pas nécessairement l'élément parent mais il dépend du type du nœud dont le parent est identifié par cet ID. Par exemple, si le nœud est un nœud texte, son parent peut être un nœud d'attribut.<br /><br /> Si le nœud se situe au niveau supérieur du document XML, son **ParentID** a pour valeur NULL.|  
|**NodeType**|**int**|Identifie le type de nœud. Il s'agit d'un entier qui correspond à la numérotation des types de nœud XML DOM.<br /><br /> Les types de nœuds sont :<br /><br /> 1 = Nœud d'élément<br /><br /> 2 = Nœud d'attribut<br /><br /> 3 = Nœud de texte|  
|**localname**|**nvarchar**|Fournit le nom local de l'élément ou de l'attribut. A pour valeur NULL si l'objet DOM est dépourvu de nom.|  
|**prefix**|**nvarchar**|Préfixe de l'espace de noms du nom de nœud.|  
|**namespaceuri**|**nvarchar**|URI de l'espace de noms du nœud. Si la valeur est NULL, aucun espace de noms n'est présent.|  
|**datatype**|**nvarchar**|Type de données réel de la ligne d'éléments ou d'attributs, sinon NULL. Le type de données est déduit de la DTD en ligne ou du schéma en ligne.|  
|**prev**|**bigint**|ID XML de l'élément frère précédent. Vaut NULL en l'absence de frère précédent direct.|  
|**texte**|**ntext**|Contient la valeur d’attribut ou le contenu de l’élément sous forme de texte (ou NULL si le **bord** entrée de la table ne requiert pas de valeur).|  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-using-a-simple-select-statement-with-openxml"></a>A. Utilisation d'une instruction SELECT simple avec OPENXML  
 Cet exemple crée une représentation interne de l'image XML à l'aide de `sp_xml_preparedocument`. Une instruction `SELECT` est alors exécutée sur la représentation interne du document XML, en utilisant un fournisseur d'ensembles de lignes `OPENXML`.  
  
 Le *indicateur* a la valeur `1`. Cela indique **centré** mappage. Par conséquent, les attributs XML sont mappés sur les colonnes de l'ensemble de lignes. Le *rowpattern* spécifié en tant que `/ROOT/Customer` identifie les `<Customers>` nœuds à traiter.  
  
 Le paramètre facultatif *ColPattern* (modèle de colonne) n’est pas spécifié, car le nom de colonne correspond aux noms des attributs XML.  
  
 Le fournisseur de l'ensemble de lignes `OPENXML` crée un ensemble de lignes sur deux colonnes (`CustomerID` et `ContactName`), à partir desquelles l'instruction `SELECT` extrait les colonnes nécessaires (toutes les colonnes dans le cas présent).  
  
```  
DECLARE @idoc int, @doc varchar(1000);  
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order CustomerID="VINET" EmployeeID="5" OrderDate="1996-07-04T00:00:00">  
      <OrderDetail OrderID="10248" ProductID="11" Quantity="12"/>  
      <OrderDetail OrderID="10248" ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Order CustomerID="LILAS" EmployeeID="3" OrderDate="1996-08-16T00:00:00">  
      <OrderDetail OrderID="10283" ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;  
-- Execute a SELECT statement that uses the OPENXML rowset provider.  
SELECT    *  
FROM       OPENXML (@idoc, '/ROOT/Customer',1)  
            WITH (CustomerID  varchar(10),  
                  ContactName varchar(20));  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CustomerID ContactName            
---------- --------------------   
VINET      Paul Henriot  
LILAS      Carlos Gonzlez  
```  
  
 Si le même `SELECT` instruction est exécutée avec *indicateurs* la valeur `2`, qui indique **centré sur l’élément** mappage, les valeurs de `CustomerID` et `ContactName` pour les deux clients dans le document XML sont retournées comme NULL, car il n’existe pas d’éléments nommés `CustomerID` ou `ContactName` dans le document XML.  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
CustomerID ContactName  
---------- -----------  
NULL       NULL  
NULL       NULL  
```  
  
### <a name="b-specifying-colpattern-for-mapping-between-columns-and-the-xml-attributes"></a>B. Spécification de ColPattern pour le mappage des colonnes aux attributs XML  
 La requête suivante retourne l'identificateur du client, la date de commande, la référence du produit et les attributs de quantité à partir du document XML. Le *rowpattern* identifie les `<OrderDetails>` éléments. `ProductID` et `Quantity` sont les attributs de l'élément `<OrderDetails>`. Toutefois, `OrderID`, `CustomerID` et `OrderDate` sont les attributs de l'élément parent (`<Orders>`).  
  
 Le paramètre facultatif *ColPattern* est spécifié. Cela signifie que :  
  
-   Le `OrderID`, `CustomerID`, et `OrderDate` dans l’Explorateur de l’ensemble de lignes pour les attributs du parent des nœuds identifiés par *rowpattern* dans le document XML.  
  
-   Le `ProdID` colonne dans l’ensemble de lignes est mappée à la `ProductID` attribut et le `Qty` colonne dans l’ensemble de lignes est mappée à la `Quantity` des nœuds identifiés dans *rowpattern*.  
  
 Bien que le **centré sur l’élément** mappage spécifié par le *indicateurs* paramètre, le mappage spécifié dans *ColPattern* remplace ce dernier.  
  
```  
DECLARE @idoc int, @doc varchar(1000);   
SET @doc ='  
<ROOT>  
<Customer CustomerID="VINET" ContactName="Paul Henriot">  
   <Order OrderID="10248" CustomerID="VINET" EmployeeID="5"   
           OrderDate="1996-07-04T00:00:00">  
      <OrderDetail ProductID="11" Quantity="12"/>  
      <OrderDetail ProductID="42" Quantity="10"/>  
   </Order>  
</Customer>  
<Customer CustomerID="LILAS" ContactName="Carlos Gonzlez">v  
   <Order OrderID="10283" CustomerID="LILAS" EmployeeID="3"   
           OrderDate="1996-08-16T00:00:00">  
      <OrderDetail ProductID="72" Quantity="3"/>  
   </Order>  
</Customer>  
</ROOT>';   
  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;   
  
-- SELECT stmt using OPENXML rowset provider  
SELECT *  
FROM   OPENXML (@idoc, '/ROOT/Customer/Order/OrderDetail',2)   
         WITH (OrderID       int         '../@OrderID',   
               CustomerID  varchar(10) '../@CustomerID',   
               OrderDate   datetime    '../@OrderDate',   
               ProdID      int         '@ProductID',   
               Qty         int         '@Quantity');  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
OrderID CustomerID           OrderDate                 ProdID    Qty  
------------------------------------------------------------------------  
10248      VINET       1996-07-04 00:00:00.000   11      12  
10248      VINET       1996-07-04 00:00:00.000   42      10  
10283      LILAS       1996-08-16 00:00:00.000   72      3  
```  
  
### <a name="c-obtaining-results-in-an-edge-table-format"></a>C. Obtention des résultats dans un format de table edge  
 Le document XML de cet exemple comporte les éléments `<Customers>`, `<Orders>` et `<Order_0020_Details>`. Tout d’abord, **sp_xml_preparedocument** est appelée pour obtenir un descripteur de document. Ce descripteur de document est transmis à `OPENXML`.  
  
 Dans le `OPENXML` instruction, le *rowpattern* (`/ROOT/Customers`) identifie le `<Customers>` nœuds à traiter. Étant donné que la clause WITH n’est pas fournie, `OPENXML` retourne l’ensemble de lignes dans une **bord** format de table.  
  
 Enfin le `SELECT` instruction extrait toutes les colonnes dans le **bord** table.  
  
```  
DECLARE @idoc int, @doc varchar(1000);   
SET @doc ='  
<ROOT>  
<Customers CustomerID="VINET" ContactName="Paul Henriot">  
   <Orders CustomerID="VINET" EmployeeID="5" OrderDate=  
           "1996-07-04T00:00:00">  
      <Order_x0020_Details OrderID="10248" ProductID="11" Quantity="12"/>  
      <Order_x0020_Details OrderID="10248" ProductID="42" Quantity="10"/>  
   </Orders>  
</Customers>  
<Customers CustomerID="LILAS" ContactName="Carlos Gonzlez">  
   <Orders CustomerID="LILAS" EmployeeID="3" OrderDate=  
           "1996-08-16T00:00:00">  
      <Order_x0020_Details OrderID="10283" ProductID="72" Quantity="3"/>  
   </Orders>  
</Customers>  
</ROOT>';  
  
--Create an internal representation of the XML document.  
EXEC sp_xml_preparedocument @idoc OUTPUT, @doc;   
  
-- SELECT statement that uses the OPENXML rowset provider.  
SELECT    *  
FROM       OPENXML (@idoc, '/ROOT/Customers')   
EXEC sp_xml_removedocument @idoc;  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples : utilisation de OPENXML](../../relational-databases/xml/examples-using-openxml.md)  
  
  

