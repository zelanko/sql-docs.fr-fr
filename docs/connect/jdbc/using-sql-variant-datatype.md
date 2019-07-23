---
title: Utilisation du type de données sql_variant | Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 662362a692742d206902a0cf23aff63a3ba89df9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916171"
---
# <a name="using-sqlvariant-data-type"></a>Utilisation du type de données Sql_variant

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

À partir de la version 6.3.0, le pilote JDBC prend en charge le type de données sql_variant. Sql_variant est également pris en charge lors de l’utilisation de fonctionnalités telles que les paramètres table et l’BulkCopy avec certaines limitations mentionnées plus loin dans cette page. Tous les types de données ne peuvent pas être stockés dans le type de données sql_variant. Pour obtenir la liste des types de données pris en charge avec sql_variant, consultez les [documents](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql)SQL Server.

##  <a name="populating-and-retrieving-a-table"></a>Remplissage et extraction d’une table:
En supposant qu’il existe une table avec une colonne sql_variant comme suit:

```sql
CREATE TABLE sampleTable (col1 sql_variant)  
```

Exemple de script pour insérer des valeurs à l’aide d’une instruction:

```java
try (Statement stmt = connection.createStatement()){
    stmt.execute("insert into sampleTable values (1)");
}
```

Insertion d’une valeur à l’aide de l’instruction préparée:

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into sampleTable values (?)")) {
    preparedStatement.setObject(1, 1);  
    preparedStatement.execute();
}
```      

Si le type sous-jacent des données passées est connu, vous pouvez utiliser la méthode setter respective. Par exemple, `preparedStatement.setInt()` peut être utilisé lors de l’insertion d’une valeur entière.

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into table values (?)")) {
    preparedStatement.setInt (1, 1);
    preparedStatement.execute();
}
```

Pour la lecture des valeurs de la table, les getters respectifs peuvent être utilisés. Par exemple, `getInt()` les `getString()` méthodes ou peuvent être utilisées si les valeurs provenant du serveur sont connues:    

```java
try (SQLServerResultSet resultSet = (SQLServerResultSet) stmt.executeQuery("select * from sampleTable ")) {
    resultSet.next();          
    resultSet.getInt(1); //or rs.getString(1); or rs.getObject(1);
}
```

## <a name="using-stored-procedures-with-sqlvariant"></a>Utilisation de procédures stockées avec sql_variant:   
Disposer d’une procédure stockée telle que:     

```java
String sql = "CREATE PROCEDURE " + inputProc + " @p0 sql_variant OUTPUT AS SELECT TOP 1 @p0=col1 FROM sampleTable ";
``` 
    
Les paramètres de sortie doivent être enregistrés:

```java
try (CallableStatement callableStatement = con.prepareCall(" {call " + inputProc + " (?) }")) {
    callableStatement.registerOutParameter(1, microsoft.sql.Types.SQL_VARIANT);      
    callableStatement.execute();
}
```

## <a name="limitations-of-sqlvariant"></a>Limitations de sql_variant:
- Lors de l’utilisation de TVP pour remplir une `datetime` table avec une `smalldatetime` `getSmallDateTime()` `getDate()` / `getDateTime()` `date` / / valeur stockée dans un sql_variant, l’appel / de sur un ResultSet ne fonctionne pas et lève l’exception suivante:
    
    `Java.lang.String cannot be cast to java.sql.Timestamp`
   
    Solution de contournement `getString()` : `getObject()` utilisez ou à la place. 
    
- L’utilisation de TVP pour remplir une table et l’envoi d’une valeur null dans sql_variant n’est pas prise en charge et lève une exception:
    
    `Inserting null value with column type sql_variant in TVP is not supported.`

## <a name="see-also"></a>Voir aussi

[Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
