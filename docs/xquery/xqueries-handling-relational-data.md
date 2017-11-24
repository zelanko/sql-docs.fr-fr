---
title: "La gestion des données relationnelles de requêtes XQuery | Documents Microsoft"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
dev_langs: XML
helpviewer_keywords:
- relational data [XQuery]
- XQuery, relational data
ms.assetid: 9812b71a-52ec-48a0-92f3-016a93660229
caps.latest.revision: "23"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c7a14ed2b176f65b379f9e09a7f920094a16b2f0
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="xqueries-handling-relational-data"></a>Requêtes XQuery pour la gestion des données relationnelles
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vous spécifiez la requête XQuery portant sur une **xml** colonne de type ou une variable en utilisant l’une de le [les méthodes de Type de données XML](../t-sql/xml/xml-data-type-methods.md). Ceux-ci incluent **query()**, **value()**, **exist()**, ou **modify()**. La requête XQuery est exécutée par rapport à l'instance XML identifiée dans la requête qui génère le document XML.  
  
 Le document XML généré par l'exécution d'une requête XQuery peut comprendre des valeurs extraites à partir d'autres colonnes d'ensemble de lignes ou variables Transact-SQL. Pour lier des données relationnelles non-XML au document XML obtenu, SQL Server fournit les pseudo-fonctions suivantes comme extensions XQuery :  
  
-   **SQL :Column()** (fonction)  
  
-   **SQL :variable()** (fonction)  
  
 Vous pouvez utiliser ces extensions XQuery lorsque vous spécifiez une requête XQuery dans le **query()** méthode de la **xml** type de données. Par conséquent, le **query()** méthode peut produire du code XML qui combine des données à partir de XML et non-**xml** des types de données.  
  
 Vous pouvez également utiliser ces fonctions lorsque vous utilisez la **xml** méthodes du type de données **modify()**, **value()**, **query()**, et **exist()**pour exposer une valeur relationnelle dans du code XML.  
  
 Pour plus d’informations, consultez [fonction SQL :Column() (XQuery)](../xquery/xquery-extension-functions-sql-column.md) et [:variable() (XQuery)](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Données XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Références relatives au langage Xquery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Construction XML &#40; XQuery &#41;](../xquery/xml-construction-xquery.md)  
  
  
