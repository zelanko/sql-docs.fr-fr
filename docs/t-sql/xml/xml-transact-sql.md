---
title: XML (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- xml_TSQL
- xml
dev_langs:
- TSQL
helpviewer_keywords:
- xml data type [SQL Server], about xml data type
ms.assetid: 9198f671-8e61-4ca4-9c3a-859f84020e62
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9e85eb245cf9d53f7d38579928a5145828797002
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="xml-transact-sql"></a>xml (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Type de données qui stocke les données XML. Vous pouvez stocker **xml** les instances dans une colonne ou une variable de **xml** type.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
xml ( [ CONTENT | DOCUMENT ] xml_schema_collection )  
```  
  
## <a name="arguments"></a>Arguments  
 CONTENT  
 Restreint la **xml** instance soit un fragment XML correctement formé. Les données XML peuvent contenir zéro ou plusieurs éléments au niveau supérieur. Les nœuds de texte sont également autorisés au niveau supérieur.  
  
 Il s'agit du comportement par défaut.  
  
 DOCUMENT  
 Restreint la **xml** instance soit un document XML bien formé. Les données XML doivent posséder un et un seul élément racine. Les nœuds de texte ne sont pas autorisés au niveau supérieur.  
  
 *xml_schema_collection*  
 Nom d'une collection de schémas XML. Pour créer un typé **xml** colonne ou une variable, vous pouvez éventuellement spécifier le nom de collection de schémas XML. Pour plus d’informations sur le XML typé et, consultez [comparer du XML au format XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="remarks"></a>Notes  
 La représentation stockée de **xml** les instances de type de données ne peut pas dépasser 2 gigaoctets (Go).  
  
 Les facettes CONTENT et DOCUMENT s'appliquent uniquement aux variables typées XML. Pour plus d’informations, consultez [comparer du XML au format XML non typé](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md).  
  
## <a name="examples"></a>Exemples  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @y xml (Sales.IndividualSurveySchemaCollection);  
SET @y =  (SELECT TOP 1 Demographics FROM Sales.Individual);  
SELECT @y;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Conversion de Type de données &#40; moteur de base de données &#41;](../../t-sql/data-types/data-type-conversion-database-engine.md)   
 [Types de données &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [méthodes de type de données xml](../../t-sql/xml/xml-data-type-methods.md)   
 [Références relatives au langage Xquery &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)  
  
  

