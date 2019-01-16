---
title: True (fonction) (XQuery) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2016
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- fn:true function
- true function
ms.assetid: 318e370d-0444-4812-afe4-307df7ef9f3b
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 611d23ad84df3087a259cbaf60870129b841715b
ms.sourcegitcommit: bfa10c54e871700de285d7f819095d51ef70d997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54257224"
---
# <a name="boolean-constructor-functions---true-xquery"></a>Fonctions constructeurs booléennes : true (XQuery)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne la valeur xs:boolean True. Ceci équivaut à `xs:boolean("1")`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
fn:true() as xs:boolean  
```  
  
## <a name="examples"></a>Exemples  
 Cette rubrique fournit des exemples de XQuery relatifs à des instances XML stockés dans différentes **xml** colonnes de type dans la base de données AdventureWorks.  
  
### <a name="a-using-the-true-xquery-boolean-function"></a>A. Utilisation de la fonction booléenne XQuery true()  
 L’exemple suivant interroge non typé **xml** variable. L’expression dans le **value()** méthode retourne la valeur booléenne **true()** si « aaa » est la valeur d’attribut. Le **value()** méthode de la **xml** convertit la valeur booléenne en bit de type de données et le retourne.  
  
```  
DECLARE @x XML  
SET @x= '<ROOT><elem attr="aaa">bbb</elem></ROOT>'  
select @x.value(' if ( (/ROOT/elem/@attr)[1] eq "aaa" ) then fn:true() else fn:false() ', 'bit')  
go  
-- result = 1  
```  
  
 Dans l’exemple suivant, la requête est spécifiée contre un typé **xml** colonne. L'expression `if` vérifie la valeur booléenne typée de l'élément <`ROOT`> et retourne le code XML construit en conséquence. Cet exemple illustre les opérations suivantes :  
  
-   Création d'une collection de schémas XML qui définit l'élément <`ROOT`> du type xs:boolean.  
  
-   Crée une table avec un typé **xml** colonne à l’aide de la collection de schémas XML.  
  
-   Enregistrement de l'instance XML dans la colonne et interrogation de l'instance.  
  
```  
-- Drop table if exist  
--DROP TABLE T  
--go  
DROP XML SCHEMA COLLECTION SC  
go  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="http://www.w3.org/2001/XMLSchema"  
targetNamespace="QNameXSD" >  
      <element name="ROOT" type="boolean" nillable="true"/>  
</schema>'  
go  
CREATE TABLE T (xmlCol XML(SC))  
go  
-- following OK  
insert into T values ('<ROOT xmlns="QNameXSD">true</ROOT>')  
 go  
-- Retrieve the local name.   
SELECT xmlCol.query('declare namespace a="QNameXSD";   
   if (/a:ROOT[1] eq true()) then  
       <result>Found boolean true</result>  
   else  
       <result>Found boolean false</result>')  
  
FROM T  
-- result = <result>Found boolean true</result>  
-- Clean up  
DROP TABLE T  
go  
DROP XML SCHEMA COLLECTION SC  
go  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de constructeur booléennes &#40;XQuery&#41;](https://msdn.microsoft.com/library/fa907f39-d4b7-4495-b829-c788928e0f64)  
  
  
