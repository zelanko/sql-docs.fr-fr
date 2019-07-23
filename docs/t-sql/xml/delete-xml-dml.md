---
title: delete (DML XML) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- XML DML [SQL Server]
- delete keyword
- delete statement [XML DML]
- deleting nodes
ms.assetid: b22c93a4-b84d-4356-af4c-6013322a4b71
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8cf804f934a08db335c55b15ab23b9e42a7ee9c5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68051319"
---
# <a name="delete-xml-dml"></a>delete (DML XML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Supprime des nœuds d'une instance XML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
delete Expression  
```  
  
## <a name="arguments"></a>Arguments  
 *Expression*  
 Expression XQuery qui identifie les nœuds à supprimer. Tous les nœuds sélectionnés par l'expression, ainsi que la totalité des nœuds ou des valeurs contenus dans les nœuds sélectionnés, sont supprimés. Comme l’indique l’article [insert (DML XML)](../../t-sql/xml/insert-xml-dml.md), cette instruction doit être une référence à un nœud existant dans le document. Ce ne peut pas être un nœud construit. L'expression ne peut pas être le nœud racine (/). Si l'expression renvoie une séquence vide, aucune suppression ne se produit et aucune erreur n'est renvoyée.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-deleting-nodes-from-a-document-stored-in-an-untyped-xml-variable"></a>A. Suppression de nœuds d'un document stocké dans une variable xml non typée  
 L'exemple suivant montre comment supprimer différents nœuds d'un document. Tout d’abord, une instance XML est affectée à une variable de type **xml**. Ensuite, les instructions DML XML delete suivantes suppriment différents nœuds du document.  
  
```  
DECLARE @myDoc xml  
SET @myDoc = '<?Instructions for=TheWC.exe ?>   
<Root>  
 <!-- instructions for the 1st work center -->  
<Location LocationID="10"   
            LaborHours="1.1"  
            MachineHours=".2" >Some text 1  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>'  
SELECT @myDoc  
  
-- delete an attribute  
SET @myDoc.modify('  
  delete /Root/Location/@MachineHours  
')  
SELECT @myDoc  
  
-- delete an element  
SET @myDoc.modify('  
  delete /Root/Location/step[2]  
')  
SELECT @myDoc  
  
-- delete text node (in <Location>  
SET @myDoc.modify('  
  delete /Root/Location/text()  
')  
SELECT @myDoc  
  
-- delete all processing instructions  
SET @myDoc.modify('  
  delete //processing-instruction()  
')  
SELECT @myDoc  
```  
  
### <a name="b-deleting-nodes-from-a-document-stored-in-an-untyped-xml-column"></a>B. Suppression de nœuds d'un document stocké dans une colonne xml non typée  
 Dans l’exemple suivant, une instruction DML XML **delete** supprime le second élément enfant de <`Features`> du document stocké dans la colonne.  
  
```  
CREATE TABLE T (i int, x xml)  
go  
INSERT INTO T VALUES(1,'<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>')  
go  
-- verify the contents before delete  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
-- delete the second feature  
UPDATE T  
SET x.modify('delete /Root/ProductDescription/Features/*[2]')  
-- verify the deletion  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
```  
  
 Notez les points suivants dans la requête précédente :  
  
-   La [méthode modify() (type de données xml)](../../t-sql/xml/modify-method-xml-data-type.md) permet de spécifier le mot clé DML XML **delete**.  
  
-   La [méthode query() (type de données xml)](../../t-sql/xml/query-method-xml-data-type.md) permet d’interroger le document.  
  
### <a name="c-deleting-nodes-from-a-typed-xml-column"></a>C. Suppression de nœuds d'une colonne xml typée  
 Cet exemple supprime des nœuds d’un document XML d’instructions de fabrication stocké dans une colonne **xml** typée.  
  
 Vous créez d’abord une table (T) avec une colonne **xml** typée dans la base données AdventureWorks. Ensuite, vous copiez une instance XML des instructions de fabrication depuis la colonne Instructions de la table ProductModel vers la table T et supprimez un ou plusieurs nœuds du document.  
  
```  
use AdventureWorks  
go  
drop table T  
go  
create table T(ProductModelID int primary key,   
Instructions xml (Production.ManuInstructionsSchemaCollection))  
go  
insert  T   
select ProductModelID, Instructions  
from Production.ProductModel  
where ProductModelID=7  
go  
select Instructions  
from T  
--1) insert <Location 1000/>. Note: <Root> must be singleton in the query  
update T  
set Instructions.modify('  
  declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  insert <MI:Location LocationID="1000"  LaborHours="1000" >  
           These are manu steps at location 1000.   
           <MI:step>New step1 instructions</MI:step>  
           Instructions for step 2 are here  
           <MI:step>New step 2 instructions</MI:step>  
         </MI:Location>  
  as first  
  into   (/MI:root)[1]  
')  
go  
select Instructions  
from T  
  
-- delete an attribute  
update T  
set Instructions.modify('  
  declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/@LaborHours)   
')  
go  
select Instructions  
from T  
-- delete text in <location>  
update T  
set Instructions.modify('  
  declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/text())   
')  
go  
select Instructions  
from T  
-- delete 2nd manu step at location 1000  
update T  
set Instructions.modify('  
  declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/MI:step[2])   
')  
go  
select Instructions  
from T  
-- cleanup  
drop table T  
go  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Créer des instances de données XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Langage de manipulation de données XML &#40;DML XML&#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
