---
title: Requêtes XQuery pour la gestion des données relationnelles | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- relational data [XQuery]
- XQuery, relational data
ms.assetid: 9812b71a-52ec-48a0-92f3-016a93660229
author: rothja
ms.author: jroth
ms.openlocfilehash: ed4583b30ed1e4538a36079f9f7794704b819cda
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67946165"
---
# <a name="xqueries-handling-relational-data"></a>Requêtes XQuery pour la gestion des données relationnelles
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vous spécifiez la requête XQuery portant sur une **xml** colonne de type ou une variable en utilisant l’une de le [les méthodes de Type de données XML](../t-sql/xml/xml-data-type-methods.md). Ceux-ci incluent **query()** , **value()** , **exist()** , ou **modify()** . La requête XQuery est exécutée par rapport à l'instance XML identifiée dans la requête qui génère le document XML.  
  
 Le document XML généré par l'exécution d'une requête XQuery peut comprendre des valeurs extraites à partir d'autres colonnes d'ensemble de lignes ou variables Transact-SQL. Pour lier des données relationnelles non-XML au document XML obtenu, SQL Server fournit les pseudo-fonctions suivantes comme extensions XQuery :  
  
-   **SQL :Column()** (fonction)  
  
-   **SQL :variable()** (fonction)  
  
 Vous pouvez utiliser ces extensions XQuery lorsque vous spécifiez une requête XQuery dans la **query()** méthode de la **xml** type de données. Par conséquent, le **query()** méthode peut produire du code XML qui combine des données à partir de XML et non-**xml** types de données.  
  
 Vous pouvez également utiliser ces fonctions lorsque vous utilisez le **xml** méthodes de type de données **modify()** , **value()** , **query()** , et  **EXIST()** pour exposer une valeur relationnelle dans du code XML.  
  
 Pour plus d’informations, consultez [fonction SQL :Column() (XQuery)](../xquery/xquery-extension-functions-sql-column.md) et [fonction SQL :variable() (XQuery)](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Données XML &#40;SQL Server&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Références relatives au langage Xquery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Construction XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)  
  
  
