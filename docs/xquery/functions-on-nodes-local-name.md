---
title: local-name Function (XQuery) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: xquery
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- fn:local-name function
- local-name function
ms.assetid: c901ef5d-89c5-482a-bf64-3eefbcf3098d
caps.latest.revision: "14"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2412e0f5a350b2e8bb4fb507440bcbfba289e359
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2017
---
# <a name="functions-on-nodes---local-name"></a>Functions on Nodes - local-name
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Returns the local part of the name of *$arg* as an xs:string that will either be the zero-length string or will have the lexical form of an xs:NCName. If the argument is not provided, the default is the context node.  
  
## <a name="syntax"></a>Syntax  
  
```  
fn:local-name() as xs:string  
fn:local-name($arg as node()?) as xs:string  
```  
  
## <a name="arguments"></a>Arguments  
 *$arg*  
 Node name whose local-name part will be retrieved.  
  
## <a name="remarks"></a>Remarks  
  
-   In SQL Server, **fn:local-name()** without an argument can only be used in the context of a context-dependent predicate. Specifically, it can only be used inside brackets (`[ ]`).  
  
-   If the argument is supplied and is the empty sequence, the function returns the zero-length string.  
  
-   If the target node has no name, because it is a document node, a comment, or a text node, the function returns the zero-length string.  
  
## <a name="examples"></a>Examples  
 This topic provides XQuery examples against XML instances that are stored in various **xml** type columns in the AdventureWorks database.  
  
### <a name="a-retrieve-local-name-of-a-specific-node"></a>A. Retrieve local name of a specific node  
 The following query is specified against an untyped XML instance. The query expression, `local-name(/ROOT[1])`, retrieves the local name part of the specified node.  
  
```  
declare @x xml  
set @x='<ROOT><a>111</a></ROOT>'  
SELECT @x.query('local-name(/ROOT[1])')  
-- result = ROOT  
```  
  
 The following query is specified against the Instructions column, a typed xml column, of the ProductModel table. The expression, `local-name(/AWMI:root[1]/AWMI:Location[1])`, returns the local name, `Location`, of the specified node.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
     local-name(/AWMI:root[1]/AWMI:Location[1])') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
-- result = Location  
```  
  
### <a name="b-using-local-name-without-argument-in-a-predicate"></a>B. Using local-name without argument in a predicate  
 The following query is specified against the Instructions column, typed **xml** column, of the ProductModel table. The expression returns all the element children of the <`root`> element whose local name part of the QName is "Location". The **local-name()** function is specifed in the predicate and it has no arguments The context node is used by the function.  
  
```  
SELECT Instructions.query('  
declare namespace AWMI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions" ;  
  /AWMI:root//*[local-name() = "Location"]') as Result  
FROM Production.ProductModel  
WHERE ProductModelID=7  
```  
  
 The query returns all the <`Location`> element children of the <`root`> element.  
  
## <a name="see-also"></a>See Also  
 [Functions on Nodes](http://msdn.microsoft.com/library/09a8affa-3341-4f50-aebc-fdf529e00c08)   
 [namespace-uri Function &#40;XQuery&#41;](../xquery/functions-on-nodes-namespace-uri.md)  
  
  
