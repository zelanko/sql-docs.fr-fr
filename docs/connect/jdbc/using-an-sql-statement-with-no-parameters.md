---
title: À l’aide d’une instruction SQL sans paramètres | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bd6fbcc2813fbd1e19078e94e4ba23b002e2818c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37982154"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>Utilisation d'une instruction SQL sans paramètres
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Pour travailler sur des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] à l’aide d’une instruction SQL ne contenant pas de paramètres, vous pouvez utiliser la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) pour retourner un [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) contenant les données demandées. Pour ce faire, vous devez commencer par créer un objet SQLServerStatement à l’aide de la méthode [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
 Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction, une instruction SQL est générée et exécutée, puis les résultats sont lus à partir du jeu de résultats.  
  
 [!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]  
  
 Pour plus d’informations sur l’utilisation de jeux de résultats, consultez [la gestion des jeux de résultats avec le pilote JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Utilisation d’instructions avec SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  
