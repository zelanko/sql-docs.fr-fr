---
title: À l’aide d’une instruction SQL sans paramètres | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 041a0119425e6469a394420469b14f47f3b84a81
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674837"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>Utilisation d'une instruction SQL sans paramètres

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour travailler sur des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une instruction SQL ne contenant pas de paramètres, vous pouvez utiliser la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) pour retourner un [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) contenant les données demandées. Pour ce faire, vous devez commencer par créer un objet SQLServerStatement à l’aide de la méthode [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction, une instruction SQL est générée et exécutée, puis les résultats sont lus à partir du jeu de résultats.

[!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]

Pour plus d’informations sur l’utilisation de jeux de résultats, consultez [la gestion des jeux de résultats avec le pilote JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).

## <a name="see-also"></a> Voir aussi

[Utilisation d’instructions avec SQL](../../connect/jdbc/using-statements-with-sql.md)
