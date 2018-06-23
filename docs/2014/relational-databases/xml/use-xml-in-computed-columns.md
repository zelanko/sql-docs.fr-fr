---
title: Utiliser des données XML dans les colonnes calculées | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-xml
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- computed columns, XML
- XML [SQL Server], computed columns
ms.assetid: 1313b889-69b4-4018-9868-0496dd83bf44
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b9af73a4ad0a0dbc1c71d6f2cd0a9e39aa035ab4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36052557"
---
# <a name="use-xml-in-computed-columns"></a>Utiliser des données XML dans les colonnes calculées
  Une instance XML peut faire office de source ou de type de colonne calculée. Les exemples dans cette rubrique indiquent comment utiliser des données XML avec des colonnes calculées.  
  
## <a name="creating-computed-columns-from-xml-columns"></a>Création de colonnes calculées à partir de colonnes XML  
 Dans l'instruction `CREATE TABLE` suivante, une colonne de type `xml` (`col2`) est calculée à partir de `col1`:  
  
```  
CREATE TABLE T(col1 varchar(max), col2 AS CAST(col1 AS xml) )    
```  
  
 Le type de données `xml` peut également faire office de source pour la création d'une colonne calculée, comme le montre l'instruction `CREATE TABLE` suivante :  
  
```  
CREATE TABLE T (col1 xml, col2 as cast(col1 as varchar(1000) ))   
```  
  
 Vous pouvez créer une colonne calculée en extrayant une valeur d'une colonne de type `xml` , comme le montre l'exemple ci-après. Étant donné que les méthodes de type de données `xml` ne peuvent pas être directement utilisées pour créer des colonnes calculées, l'exemple définit d'abord une fonction (`my_udf`) qui renvoie une valeur d'une instance XML. La fonction inclut la méthode `value()` du type `xml` . Le nom de la fonction est ensuite spécifié dans l'instruction `CREATE TABLE` de la colonne calculée.  
  
```  
CREATE FUNCTION my_udf(@var xml) returns int  
AS BEGIN   
RETURN @var.value('(/ProductDescription/@ProductModelID)[1]' , 'int')  
END  
GO  
-- Use the function in CREATE TABLE.  
CREATE TABLE T (col1 xml, col2 as dbo.my_udf(col1) )  
GO  
-- Try adding a row.   
INSERT INTO T values('<ProductDescription ProductModelID="1" />')  
GO  
-- Verify results.  
SELECT col2, col1  
FROM T  
  
```  
  
 Comme l'exemple précédent, l'exemple suivant définit une fonction afin de renvoyer une instance de type `xml` pour une colonne calculée. Dans la fonction, la méthode `query()` du type de données `xml` extrait une valeur d'un paramètre de type `xml` .  
  
```  
CREATE FUNCTION my_udf(@var xml)   
  RETURNS xml AS   
BEGIN   
   RETURN @var.query('ProductDescription/Features')  
END  
```  
  
 Dans l'instruction `CREATE TABLE` suivante, `Col2` est une colonne calculée qui utilise les données XML (élément`<Features>` ) renvoyées par la fonction :  
  
```  
CREATE TABLE T (Col1 xml, Col2 as dbo.my_udf(Col1) )  
-- Insert a row in table T.  
INSERT INTO T VALUES('  
<ProductDescription ProductModelID="1" >  
  <Features>  
    <Feature1>description</Feature1>  
    <Feature2>description</Feature2>  
  </Features>  
</ProductDescription>')  
-- Verify the results.  
SELECT *  
FROM T  
```  
  
### <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Promouvoir les valeurs XML les plus fréquentes à l'aide de colonnes calculées](promote-frequently-used-xml-values-with-computed-columns.md)|Décrit comment utiliser la promotion de propriété avec des colonnes calculées et des tables de propriétés.|  
  
  