---
title: Utilisation d'une procédure stockée avec retour d'état | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b126e95-8458-41d6-af37-fc6662859f19
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b5b5425dcc88a3f4a2b5bc24c85ab41beb04bb48
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69027113"
---
# <a name="using-a-stored-procedure-with-a-return-status"></a>Utilisation d'une procédure stockée avec retour d'état

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Une procédure stockée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous pouvez appeler est une procédure qui retourne un état ou un paramètre de résultat. Cette procédure permet généralement d'indiquer la réussite ou l'échec de la procédure stockée. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] intègre la classe [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), que vous pouvez utiliser pour appeler ce type de procédure stockée et traiter les données qu’elle retourne.

Quand vous appelez ce type de procédure stockée à l’aide du pilote JDBC, vous devez utiliser la séquence d’échappement SQL `call` conjointement avec la méthode [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). La syntaxe de la séquence d’échappement `call` avec un paramètre de retour d’état est la suivante :

`{[?=]call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Pour plus d’informations sur les séquences d’échappement SQL, consultez Utilisation de séquences d' [échappement SQL](../../connect/jdbc/using-sql-escape-sequences.md).

Quand vous construisez la séquence d’échappement `call`, spécifiez le paramètre de retour d’état l’aide du caractère ? (point d'interrogation). Ce caractère fait office d'espace réservé pour la valeur de paramètre qui est retournée par la procédure stockée. Pour spécifier une valeur pour un paramètre de retour d’état, vous devez spécifier le type de données du paramètre à l’aide de la méthode [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) de la classe SQLServerCallableStatement avant d’exécuter la procédure stockée.

> [!NOTE]  
> Lors de l’utilisation du pilote JDBC avec une base de données SQL Server, la valeur spécifiée pour le paramètre de retour d’état dans la méthode registerOutParameter est toujours un nombre entier que vous pouvez spécifier à l’aide du type de données java.sql.Types.INTEGER.

En outre, quand vous transmettez une valeur à la méthode registerOutParameter pour un paramètre de retour d’état, vous devez spécifier non seulement le type de données à utiliser pour le paramètre, mais également la position ordinale de celui-ci dans l’appel de procédure stockée. La position ordinale du paramètre de retour d'état est toujours 1 car il s'agit toujours du premier paramètre de l'appel à la procédure stockée. Bien que la classe SQLServerCallableStatement fournisse la prise en charge de l’utilisation du nom de paramètre pour indiquer le paramètre spécifique, vous pouvez utiliser uniquement le numéro de position ordinale d’un paramètre pour les paramètres de retour d’état.

Par exemple, créez la procédure stockée suivante dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] :

```sql
CREATE PROCEDURE CheckContactCity  
   (@cityName CHAR(50))  
AS  
BEGIN  
   IF ((SELECT COUNT(*)  
   FROM Person.Address  
   WHERE City = @cityName) > 1)  
   RETURN 1  
ELSE  
   RETURN 0  
END  
```

Cette procédure stockée retourne une valeur de statut 1 ou 0, selon que la ville spécifiée dans le paramètre cityName figure ou non dans la table Person.Address.

Dans l’exemple suivant, une connexion ouverte à l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] est transmise à la fonction et la méthode [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) permet d’appeler la procédure stockée CheckContactCity :

[!code[JDBC#UsingSprocWithReturnStatus1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_1_1.java)]

## <a name="see-also"></a>Voir aussi

[Utilisation d'instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md)
