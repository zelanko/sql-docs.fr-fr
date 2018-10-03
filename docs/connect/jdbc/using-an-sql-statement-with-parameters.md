---
title: À l’aide d’une instruction SQL avec des paramètres | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 3202b88f-ce13-44dd-982c-c6a3b0260378
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 66a0215721b906ed81e9daa06cb3dbc07804229d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629467"
---
# <a name="using-an-sql-statement-with-parameters"></a>Utilisation d'une instruction SQL avec paramètres

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour travailler sur des données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en utilisant une instruction SQL contenant des paramètres IN, vous pouvez utiliser la méthode [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) de la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) pour retourner un [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) contenant les données demandées. Pour ce faire, vous devez commencer par créer un objet SQLServerPreparedStatement à l’aide de la méthode [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

Lors de la construction d'une instruction SQL, les paramètres IN sont spécifiés à l'aide du caractère ? (point d'interrogation) qui fait office d'espace réservé pour les valeurs de paramètre qui sont transmises par la suite à l'instruction SQL. Pour spécifier une valeur pour un paramètre, vous pouvez utiliser une des méthodes setter de la classe SQLServerPreparedStatement. La méthode setter que vous utilisez est déterminée par le type de données de la valeur que vous souhaitez transmettre dans l'instruction SQL.

Lorsque vous transmettez une valeur à la méthode setter, vous devez spécifier non seulement la valeur réelle à utiliser dans l'instruction SQL, mais également la position ordinale du paramètre dans l'instruction. Par exemple, si votre instruction SQL contient un seul paramètre, sa valeur ordinale sera 1. Si l’inscription contient deux paramètres, la première valeur ordinale sera 1, tandis que la deuxième sera 2.

Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction, une instruction SQL préparée est générée et exécutée avec une seule valeur de paramètre String, puis les résultats sont lus dans le jeu de résultats.

[!code[JDBC#UsingSQLWithParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_1_1.java)]

## <a name="see-also"></a> Voir aussi

[Utilisation d’instructions avec SQL](../../connect/jdbc/using-statements-with-sql.md)
