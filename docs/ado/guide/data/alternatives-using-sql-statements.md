---
title: 'Alternatives : Utilisation d’instructions SQL | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b95e6f0bd2b702080b3580b8b9eeb80ac5b06e8d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674257"
---
# <a name="alternatives-using-sql-statements"></a>Alternatives : utilisation d’instructions SQL
ADO permet également à l’aide des commandes comme alternatives à ses propriétés et méthodes intégrées pour la modification des données. En fonction de votre fournisseur, toutes les opérations indiquées dans cette section peuvent également être effectuées en passant des commandes à votre source de données. Par exemple, les instructions de mise à jour de SQL peuvent être utilisées pour modifier des données sans utiliser le **valeur** propriété d’un **champ**. Instructions SQL INSERT peuvent être utilisées pour ajouter de nouveaux enregistrements à une source de données, plutôt que la méthode ADO **AddNew**. Pour plus d’informations sur SQL ou du langage de manipulation de données de votre fournisseur, consultez la documentation de votre source de données.  
  
 Par exemple, vous pouvez passer une chaîne SQL contenant une instruction DELETE à une base de données, comme indiqué dans le code suivant :  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
