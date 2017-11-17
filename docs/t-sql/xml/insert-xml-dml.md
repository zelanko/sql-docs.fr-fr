---
title: Insert (DML XML) | Documents Microsoft
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
- XML DML [SQL Server]
- inserting nodes
- insert keyword [XML DML]
- insert XML DML statement
ms.assetid: 0c95c2b3-5cc2-4c38-9e25-86493096c442
caps.latest.revision: 38
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9f995a0dcd0b91c0835c4121a7a2072c2a586f35
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="insert-xml-dml"></a>insert (XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Insère un ou plusieurs nœuds identifiés par *Expression1* en tant que nœuds enfants ou frères du nœud identifié par *Expression2*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
insert   
      Expression1 (  
                 {as first | as last} into | after | before  
                                    Expression2  
                )  
```  
  
## <a name="arguments"></a>Arguments  
 *Expression1*  
 Identifie un ou plusieurs nœuds à insérer. Cela peut être une instance XML constante ; une référence à une instance de type de données XML typée de la même collection de schémas XML à laquelle la méthode de modification est appliquée ; une instance de type de données XML non typée à l’aide d’une manière autonome **SQL :Column()**/**SQL :variable()** fonction ; ou une expression XQuery. L'expression peut résulter en un nœud, un nœud de texte ou une séquence ordonnée de nœuds. Le résultat ne peut pas être le nœud racine (/). Si l'expression a pour résultat une valeur ou une séquence de valeurs, ces valeurs sont insérées en tant que nœud de texte unique avec un espace séparant chaque valeur dans la séquence. Si vous spécifiez plusieurs nœuds sous la forme d'une constante, les nœuds sont inclus entre parenthèses et sont séparés par des virgules. Vous ne pouvez pas insérer des séquences hétérogènes telles qu'une séquence d'éléments, d'attributs ou de valeurs. Si *Expression1* correspond à une séquence vide, aucune insertion n’a lieu et aucune erreur est retournée.  
  
 en  
 Nœuds identifiés par *Expression1* sont insérés en tant que descendants directs (nœuds enfants) du nœud identifié par *Expression2*. Si le nœud dans *Expression2* dispose déjà d’un ou plusieurs nœuds enfants, vous devez utiliser soit **en tant que premier** ou **en dernier** pour spécifier où vous souhaitez que le nouveau nœud ajouté. Par exemple, respectivement au début et à la fin de la liste des enfants. Le **en tant que premier** et **en dernier** sont ignorées lors de l’insertion d’attributs.  
  
 after  
 Nœuds identifiés par *Expression1* sont insérés en tant que frères directement après le nœud identifié par *Expression2*. Le **après** mot clé ne peut pas être utilisé pour insérer des attributs. Par exemple, il ne peut pas être utilisé pour insérer un constructeur d'attribut ou pour retourner un attribut à partir d'une requête XQuery.  
  
 before  
 Nœuds identifiés par *Expression1* sont insérés en tant que frères directement avant le nœud identifié par *Expression2*. Le **avant** mot clé ne peut pas être utilisé lors de l’insertion d’attributs. Par exemple, il ne peut pas être utilisé pour insérer un constructeur d'attribut ou pour retourner un attribut à partir d'une requête XQuery.  
  
 *Expression2*  
 Identifie un nœud. Les nœuds identifiés dans *Expression1* sont insérés par rapport au nœud identifié par *Expression2*. Il peut s'agir d'une expression XQuery qui retourne une référence à un nœud qui existe dans le document actuellement référencé. Si plusieurs nœuds sont retournés, l'insertion échoue. Si *Expression2* retourne une séquence vide, aucune insertion n’a lieu et aucune erreur est retournées. Si *Expression2* est statiquement pas un singleton, une erreur statique est retournée. *Expression2* ne peut pas être une instruction de traitement, un commentaire ou un attribut. Notez que *Expression2* doit être une référence à un nœud existant dans le document et pas un nœud construit.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-inserting-element-nodes-into-the-document"></a>A. Insertion de nœuds d'élément dans le document  
 L'exemple suivant illustre l'insertion d'éléments dans un document. Tout d’abord, un document XML est attribué à une variable de **xml** type. Ensuite, plusieurs **insérer** instructions XML DML, l’exemple illustre la façon dont les nœuds d’élément sont insérés dans le document. Après chaque insertion, l'instruction SELECT affiche le résultat.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;         
SET @myDoc = '<Root>         
    <ProductDescription ProductID="1" ProductName="Road Bike">         
        <Features>         
        </Features>         
    </ProductDescription>         
</Root>'  ;       
SELECT @myDoc;     
-- insert first feature child (no need to specify as first or as last)         
SET @myDoc.modify('         
insert <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>   
into (/Root/ProductDescription/Features)[1]') ;  
SELECT @myDoc ;        
-- insert second feature. We want this to be the first in sequence so use 'as first'         
set @myDoc.modify('         
insert <Warranty>1 year parts and labor</Warranty>          
as first         
into (/Root/ProductDescription/Features)[1]         
')  ;       
SELECT @myDoc  ;       
-- insert third feature child. This one is the last child of <Features> so use 'as last'         
SELECT @myDoc         
SET @myDoc.modify('         
insert <Material>Aluminium</Material>          
as last         
into (/Root/ProductDescription/Features)[1]         
')         
SELECT @myDoc ;        
-- Add fourth feature - this time as a sibling (and not a child)         
-- 'after' keyword is used (instead of as first or as last child)         
SELECT @myDoc  ;       
set @myDoc.modify('         
insert <BikeFrame>Strong long lasting</BikeFrame>   
after (/Root/ProductDescription/Features/Material)[1]         
')  ;       
SELECT @myDoc;  
GO  
```  
  
 Notez que des expressions de chemin d'accès différentes dans cet exemple spécifient "[1]" comme exigence par type statique. Cela garantit l'unicité du nœud cible.  
  
### <a name="b-inserting-multiple-elements-into-the-document"></a>B. Insertion de plusieurs éléments dans le document  
 Dans l’exemple suivant, un document est affecté à une variable de **xml** type. Ensuite, une séquence de deux éléments, qui représente les fonctionnalités du produit, est attribuée à une deuxième variable de **xml** type. Cette séquence est alors insérée dans la première variable.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc = N'<Root>             
<ProductDescription ProductID="1" ProductName="Road Bike">             
    <Features> </Features>             
</ProductDescription>             
</Root>';  
DECLARE @newFeatures xml;  
SET @newFeatures = N'<Warranty>1 year parts and labor</Warranty>            
<Maintenance>3 year parts and labor extended maintenance is available</Maintenance>';           
-- insert new features from specified variable            
SET @myDoc.modify('             
insert sql:variable("@newFeatures")             
into (/Root/ProductDescription/Features)[1] ')             
SELECT @myDoc;  
GO  
```  
  
### <a name="c-inserting-attributes-into-a-document"></a>C. Insertion d'attributs dans un document  
 L’exemple suivant illustre la façon dont les attributs sont insérés dans un document. Tout d’abord, un document est affecté à un **xml** variable de type. Ensuite, une série de **insérer** instructions XML DML est utilisé pour insérer des attributs dans le document. Après chaque insertion d'attribut, l'instruction SELECT affiche le résultat.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml ;            
SET @myDoc =   
'<Root>             
    <Location LocationID="10" >             
        <step>Manufacturing step 1 at this work center</step>             
        <step>Manufacturing step 2 at this work center</step>             
    </Location>             
</Root>' ;  
SELECT @myDoc  ;          
-- insert LaborHours attribute             
SET @myDoc.modify('             
insert attribute LaborHours {".5" }             
into (/Root/Location[@LocationID=10])[1] ') ;           
SELECT @myDoc  ;          
-- insert MachineHours attribute but its value is retrived from a sql variable @Hrs             
DECLARE @Hrs float ;            
SET @Hrs =.2   ;          
SET @myDoc.modify('             
insert attribute MachineHours {sql:variable("@Hrs") }             
into   (/Root/Location[@LocationID=10])[1] ');            
SELECT @myDoc;             
-- insert sequence of attribute nodes (note the use of ',' and ()              
-- around the attributes.             
SET @myDoc.modify('             
insert (              
           attribute SetupHours {".5" },             
           attribute SomeOtherAtt {".2"}             
        )             
into (/Root/Location[@LocationID=10])[1] ');             
SELECT @myDoc;  
GO  
```  
  
### <a name="d-inserting-a-comment-node"></a>D. Insertion d'un nœud de commentaire  
 Dans cette requête, un document XML est affecté à une variable de **xml** type. Ensuite, XML DML est utilisé pour insérer un nœud de commentaire après le premier élément <`step`>.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;             
SET @myDoc =   
'<Root>             
    <Location LocationID="10" >             
        <step>Manufacturing step 1 at this work center</step>             
        <step>Manufacturing step 2 at this work center</step>             
    </Location>             
</Root>' ;           
SELECT @myDoc;             
SET @myDoc.modify('             
insert <!-- some comment -->             
after (/Root/Location[@LocationID=10]/step[1])[1] ');            
SELECT @myDoc;  
GO  
```  
  
### <a name="e-inserting-a-processing-instruction"></a>E. Insertion d'une instruction de traitement  
 Dans la requête suivante, un document XML est affecté à une variable de **xml** type. Ensuite, le mot clé XML DML est utilisé pour insérer une instruction de traitement au début du document.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>   
    <Location LocationID="10" >   
        <step>Manufacturing step 1 at this work center</step>   
        <step>Manufacturing step 2 at this work center</step>   
    </Location>   
</Root>' ;  
SELECT @myDoc ;  
SET @myDoc.modify('   
insert <?Program = "Instructions.exe" ?>   
before (/Root)[1] ') ;  
SELECT @myDoc ;  
GO  
```  
  
### <a name="f-inserting-data-using-a-cdata-section"></a>F. Insertion de données à l'aide d'une section CDATA  
 Lorsque vous insérez du texte qui inclut des caractères non valides en XML, tels que < ou >, vous pouvez utiliser des sections CDATA pour insérer les données comme cela est illustré dans la requête ci-dessous. La requête spécifie une section CDATA, mais elle est ajoutée comme nœud de texte avec les caractères non valides convertis en entités. Par exemple, ' <' est enregistré sous la forme &lt;.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;             
SET @myDoc =   
'<Root>             
    <ProductDescription ProductID="1" ProductName="Road Bike">             
        <Features> </Features>             
    </ProductDescription>             
</Root>' ;            
SELECT @myDoc ;            
SET @myDoc.modify('             
insert <![CDATA[ <notxml> as text </notxml> or cdata ]]>   
into  (/Root/ProductDescription/Features)[1] ') ;   
SELECT @myDoc ;  
GO  
```  
  
 La requête insère un nœud de texte dans l'élément <`Features`> :  
  
```  
<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features> <notxml> as text </notxml> or cdata </Features>  
</ProductDescription>  
</Root>       
```  
  
### <a name="g-inserting-text-node"></a>G. Insertion d'un nœud de texte  
 Dans cette requête, un document XML est affecté à une variable de **xml** type. Ensuite, XML DML est utilisé pour insérer un nœud de texte comme premier enfant de l'élément <`Root`>. Le constructeur de texte est utilisé pour spécifier le texte.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc = '<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  
</Features>  
</ProductDescription>  
</Root>'  
SELECT @myDoc;  
set @myDoc.modify('  
 insert text{"Product Catalog Description"}   
 as first into (/Root)[1]  
');  
SELECT @myDoc;  
```  
  
### <a name="h-inserting-a-new-element-into-an-untyped-xml-column"></a>H. Insertion d'un nouvel élément dans une colonne xml non typée  
 L’exemple suivant applique XML DML pour mettre à jour une instance XML stockée dans une **xml** colonne de type :  
  
```  
USE AdventureWorks;  
GO  
CREATE TABLE T (i int, x xml);  
go  
INSERT INTO T VALUES(1,'<Root>  
    <ProductDescription ProductID="1" ProductName="Road Bike">  
        <Features>  
            <Warranty>1 year parts and labor</Warranty>  
            <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
        </Features>  
    </ProductDescription>  
</Root>');  
go  
-- insert a new element  
UPDATE T  
SET x.modify('insert <Material>Aluminium</Material> as first  
  into   (/Root/ProductDescription/Features)[1]  
');  
GO  
```  
  
 De nouveau, lorsque le nœud d'élément <`Material`> est inséré, l'expression de chemin d'accès doit retourner une seule cible. Cela est spécifié explicitement par l'ajout de [1] à la fin de l'expression.  
  
```  
-- check the update  
SELECT x.query(' //ProductDescription/Features')  
FROM T;  
GO  
```  
  
### <a name="i-inserting-based-on-an-if-condition-statement"></a>I. Insertion basée sur une instruction de condition if  
 Dans l’exemple suivant, une condition IF est spécifiée dans Expression1 dans le **insérer** instruction XML DML. Si la condition a la valeur True, un attribut est ajouté à l'élément <`WorkCenter`>.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>  
    <Location LocationID="10" LaborHours="1.2" >  
        <step>Manufacturing step 1 at this work center</step>  
    <step>Manufacturing step 2 at this work center</step>  
    </Location>  
</Root>';  
SELECT @myDoc  
SET @myDoc.modify('  
insert  
if (/Root/Location[@LocationID=10])  
then attribute MachineHours {".5"}  
else ()  
    as first into   (/Root/Location[@LocationID=10])[1] ');  
SELECT @myDoc;  
GO  
```  
  
 L’exemple suivant est similaire, à ceci près que le **insérer** instruction XML DML insère un élément dans le document si la condition est True. C'est-à-dire, si l'élément <`WorkCenter`> possède deux ou moins de deux éléments enfants <`step`>.  
  
```  
USE AdventureWorks;  
GO  
DECLARE @myDoc xml;  
SET @myDoc =   
'<Root>  
    <Location LocationID="10" LaborHours="1.2" >  
        <step>Manufacturing step 1 at this work center</step>  
        <step>Manufacturing step 2 at this work center</step>  
    </Location>  
</Root>';  
SELECT @myDoc;  
SET @myDoc.modify('  
insert  
if (count(/Root/Location/step) <= 2)  
then element step { "This is a new step" }  
else ()  
    as last into   (/Root/Location[@LocationID=10])[1] ');  
SELECT @myDoc;  
GO  
```  
  
 Voici le résultat obtenu :  
  
```  
<Root>  
 <WorkCenter WorkCenterID="10" LaborHours="1.2">  
  <step>Manufacturing step 1 at this work center</step>  
  <step>Manufacturing step 2 at this work center</step>  
  <step>This is a new step</step>  
 </WorkCenter>  
```  
  
### <a name="j-inserting-nodes-in-a-typed-xml-column"></a>J. Insertion de nœuds dans une colonne xml typée  
 Cet exemple insère un élément et un attribut dans une instructions de fabrication XML stockée dans un typé **xml** colonne.  
  
 Dans l’exemple, vous créez une table (T) avec un typé **xml** colonne, dans la base de données AdventureWorks. Ensuite, vous copiez une instance XML des instructions de fabrication de la colonne Instructions dans la table ProductModel vers la table T. Les insertions sont ensuite appliquées à l'instance XML dans la table T.  
  
```  
USE AdventureWorks;  
GO            
DROP TABLE T;  
GO             
CREATE TABLE T(ProductModelID int primary key,    
Instructions xml (Production.ManuInstructionsSchemaCollection));  
GO  
INSERT T              
    SELECT ProductModelID, Instructions             
    FROM Production.ProductModel             
    WHERE ProductModelID=7;  
GO             
SELECT Instructions             
FROM T;  
-- now insertion begins             
--1) insert a new manu. Location. The <Root> specified as              
-- expression 2 in the insert() must be singleton.      
UPDATE T   
set Instructions.modify('   
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";   
insert <MI:Location LocationID="1000" >   
           <MI:step>New instructions go here</MI:step>   
         </MI:Location>   
as first   
into   (/MI:root)[1]   
') ;  
  
SELECT Instructions             
FROM T ;  
-- 2) insert attributes in the new <Location>             
UPDATE T             
SET Instructions.modify('             
declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";             
insert attribute LaborHours { "1000" }             
into (/MI:root/MI:Location[@LocationID=1000])[1] ');   
GO             
SELECT Instructions             
FROM T ;  
GO             
--cleanup             
DROP TABLE T ;  
GO             
```  
  
## <a name="see-also"></a>Voir aussi  
 [Comparer du XML typé et du XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [Créer des instances de données XML](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)   
 [XML Data Modification Language &#40; XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  

