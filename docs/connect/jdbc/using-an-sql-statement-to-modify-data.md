---
title: À l’aide d’une instruction SQL pour modifier des données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4704199b-c0ae-4c77-8a2e-6963715b4ffb
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89fd14cf4245a3c44dad41b4af5b3b14e779e82b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47838288"
---
# <a name="using-an-sql-statement-to-modify-data"></a>Utilisation d'une instruction SQL pour modifier des données

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Pour modifier les données contenues dans une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l’aide d’une instruction SQL, vous pouvez appliquer la méthode [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) de la classe [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). La méthode executeUpdate transmet l’instruction SQL à la base de données pour traitement, puis retourne une valeur indiquant le nombre de lignes affectées.

Pour ce faire, vous devez commencer par créer un objet SQLServerStatement à l’aide de la méthode [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction. Une instruction SQL est générée pour ajouter des données à la table, puis l’instruction est exécutée et la valeur retournée est affichée.

[!code[JDBC#UsingSQLToModifyData1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_1_1.java)]

> [!NOTE]  
> Si vous devez utiliser une instruction SQL contenant des paramètres pour modifier les données d’une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous devez utiliser la méthode [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md) de la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).
>
> Si la colonne dans laquelle vous tentez d'insérer des données contient des caractères spéciaux, tels que des espaces, vous devez fournir les valeurs à insérer, même s'il s'agit de valeurs par défaut. Si vous ne le faites pas, l'insertion échoue.
>
> Si vous souhaitez que le pilote JDBC retourne tous les nombres de mises à jour, y compris les nombres de mises à jour retournées par des déclencheurs qui ont pu se déclencher, définissez la propriété de chaîne de connexion lastUpdateCount sur « false ». Pour plus d’informations sur la propriété lastUpdateCount, consultez [définissant les propriétés de connexion](../../connect/jdbc/setting-the-connection-properties.md).

## <a name="see-also"></a> Voir aussi

[Utilisation d’instructions avec SQL](../../connect/jdbc/using-statements-with-sql.md)
