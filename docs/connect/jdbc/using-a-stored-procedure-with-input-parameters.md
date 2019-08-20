---
title: Utilisation d'une procédure stockée avec des paramètres d'entrée | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8f491b70-7d1b-42bd-964f-9a8b86af5eaa
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c84e4081b9369d504d173387c6944b06d927c9c
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026905"
---
# <a name="using-a-stored-procedure-with-input-parameters"></a>Utilisation d'une procédure stockée avec des paramètres d'entrée

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Une procédure stockée [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous pouvez appeler est une procédure contenant un ou plusieurs paramètres IN, qui sont des paramètres pouvant servir à transmettre des données dans la procédure stockée. Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] intègre la classe [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), que vous pouvez utiliser pour appeler ce type de procédure stockée et traiter les données qu’elle retourne.

Quand vous utilisez le pilote JDBC pour appeler une procédure stockée avec des paramètres IN, vous devez utiliser la séquence d’échappement SQL `call` conjointement avec la méthode [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) de la classe [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). La syntaxe de la séquence d’échappement `call` avec les paramètres IN est la suivante :

`{call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Pour plus d’informations sur les séquences d’échappement SQL, consultez Utilisation de séquences d' [échappement SQL](../../connect/jdbc/using-sql-escape-sequences.md).

Quand vous construisez la séquence d’échappement `call`, spécifiez les paramètres IN à l’aide du caractère ? (point d'interrogation). Ce caractère fait office d'espace réservé pour les valeurs de paramètre qui sont transmises à la procédure stockée. Pour spécifier une valeur pour un paramètre, vous pouvez utiliser l’une des méthodes setter de la classe SQLServerPreparedStatement. La méthode de définition que vous pouvez utiliser est déterminée par le type de données du paramètre IN.

Lorsque vous transmettez une valeur à la méthode de définition, vous devez spécifier non seulement la valeur réelle qui sera utilisée dans le paramètre, mais également la position ordinale dans la procédure stockée. Par exemple, si votre procédure stockée contient un seul paramètre IN, sa valeur ordinale sera 1. Si la procédure stockée contient deux paramètres, la première valeur ordinale sera 1 et la deuxième sera 2.

Pour obtenir un exemple de la manière d’appeler une procédure stockée contenant un paramètre IN, utilisez la procédure stockée uspGetEmployeeManagers figurant dans l’exemple de base de données [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Cette procédure stockée n'accepte qu'un seul paramètre d'entrée nommé EmployeeID, qui est une valeur entière, et retourne une liste récursive d'employés et de leurs directeurs basée sur la valeur EmployeeID spécifiée. Le code Java pour l'appel de cette procédure stockée est le suivant :

```java
public static void executeSprocInParams(Connection con) throws SQLException {  
    try(PreparedStatement pstmt = con.prepareStatement("{call dbo.uspGetEmployeeManagers(?)}"); ) {  

        pstmt.setInt(1, 50);  
        ResultSet rs = pstmt.executeQuery();  

        while (rs.next()) {  
            System.out.println("EMPLOYEE:");  
            System.out.println(rs.getString("LastName") + ", " + rs.getString("FirstName"));  
            System.out.println("MANAGER:");  
            System.out.println(rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));  
            System.out.println();  
        }  
    }
}
```

## <a name="see-also"></a>Voir aussi

[Utilisation d'instructions avec des procédures stockées](../../connect/jdbc/using-statements-with-stored-procedures.md)
