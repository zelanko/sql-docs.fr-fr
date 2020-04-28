---
title: Requêtes XQuery gestion des données relationnelles | Microsoft Docs
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
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67946165"
---
# <a name="xqueries-handling-relational-data"></a>Requêtes XQuery pour la gestion des données relationnelles
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Vous spécifiez XQuery sur une variable ou une colonne de type **XML** à l’aide de l’une des [méthodes de type de données XML](../t-sql/xml/xml-data-type-methods.md). Il peut s’agir des **requêtes ()**, **value ()**, **exist ()** ou **Modify ()**. La requête XQuery est exécutée par rapport à l'instance XML identifiée dans la requête qui génère le document XML.  
  
 Le document XML généré par l'exécution d'une requête XQuery peut comprendre des valeurs extraites à partir d'autres colonnes d'ensemble de lignes ou variables Transact-SQL. Pour lier des données relationnelles non-XML au document XML obtenu, SQL Server fournit les pseudo-fonctions suivantes comme extensions XQuery :  
  
-   fonction **SQL : Column ()**  
  
-   fonction **SQL : variable ()**  
  
 Vous pouvez utiliser ces extensions XQuery lors de la spécification d’une requête XQuery dans la méthode **query ()** du type de données **XML** . Par conséquent, la méthode **query ()** peut produire du code XML qui combine des données de types de données XML et non-**XML** .  
  
 Vous pouvez également utiliser ces fonctions lorsque vous utilisez les méthodes de type de données **XML** **Modify ()**, **value ()**, **query ()** et **exist ()** pour exposer une valeur relationnelle dans du code XML.  
  
 Pour plus d’informations, consultez [SQL : Column (), fonction (XQuery)](../xquery/xquery-extension-functions-sql-column.md) et [fonction SQL : variable () (XQuery)](../xquery/xquery-extension-functions-sql-variable.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQL Server de &#40;de données XML&#41;](../relational-databases/xml/xml-data-sql-server.md)   
 [Référence du langage XQuery &#40;SQL Server&#41;](../xquery/xquery-language-reference-sql-server.md)   
 [Construction XML &#40;XQuery&#41;](../xquery/xml-construction-xquery.md)  
  
  
