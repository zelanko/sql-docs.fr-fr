---
title: 'Alternatives : À l’aide d’instructions SQL | Documents Microsoft'
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09f2220a4dc896858923013a087d5e52c373809f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="alternatives-using-sql-statements"></a>Alternatives : À l’aide d’instructions SQL
ADO permet également à l’aide de commandes en tant qu’alternatives pour ses propriétés et méthodes intégrées pour la modification des données. En fonction de votre fournisseur, toutes les opérations indiquées dans cette section peut également être accomplies en passant des commandes à votre source de données. Par exemple, les instructions de mise à jour de SQL peuvent être utilisées pour modifier des données sans utiliser le **valeur** propriété d’un **champ**. Les instructions SQL INSERT peuvent être utilisées pour ajouter de nouveaux enregistrements dans une source de données, plutôt que la méthode ADO **AddNew**. Pour plus d’informations sur SQL ou le langage de manipulation de données de votre fournisseur, consultez la documentation de votre source de données.  
  
 Par exemple, vous pouvez passer une chaîne SQL contenant une instruction DELETE à une base de données, comme indiqué dans le code suivant :  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
