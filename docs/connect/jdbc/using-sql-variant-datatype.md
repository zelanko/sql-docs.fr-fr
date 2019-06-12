---
title: À l’aide du Type de données Sql_variant | Microsoft Docs
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
manager: jroth
ms.openlocfilehash: c004bc40ed0c85b82612be9069e1a53041c8095c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798587"
---
# <a name="using-sqlvariant-data-type"></a>Utilisation du type de données Sql_variant

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Depuis la version 6.3.0, le pilote JDBC prend en charge le type de données sql_variant. Sql_variant est également pris en charge à l’aide des fonctionnalités telles que les paramètres table et BulkCopy avec certaines limitations mentionnées plus loin dans cette page. Pas tous les types de données peuvent être stockées dans le type de données sql_variant. Pour obtenir la liste des types de données pris en charge avec sql_variant, vérifiez le serveur SQL Server [Docs](https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql).

##  <a name="populating-and-retrieving-a-table"></a>Remplissage et la récupération d’une table :
En supposant qu’il a une table avec une colonne sql_variant en tant que :

```sql
CREATE TABLE sampleTable (col1 sql_variant)  
```

Un exemple de script pour insérer des valeurs à l’aide d’instruction :

```java
try (Statement stmt = connection.createStatement()){
    stmt.execute("insert into sampleTable values (1)");
}
```

Insertion de valeur à l’aide d’instruction préparée :

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into sampleTable values (?)")) {
    preparedStatement.setObject(1, 1);  
    preparedStatement.execute();
}
```      

Si le type sous-jacent de données passées est connu, la méthode setter respectif utilisable. Par exemple, `preparedStatement.setInt()` peut être utilisé lors de l’insertion d’une valeur entière.

```java
try (PreparedStatement preparedStatement = con.prepareStatement("insert into table values (?)")) {
    preparedStatement.setInt (1, 1);
    preparedStatement.execute();
}
```

Pour lire les valeurs de la table, vous pouvez utiliser les méthodes getter respectifs. Par exemple, `getInt()` ou `getString()` méthodes peuvent être utilisées si les valeurs provenant du serveur sont connues :    

```java
try (SQLServerResultSet resultSet = (SQLServerResultSet) stmt.executeQuery("select * from sampleTable ")) {
    resultSet.next();          
    resultSet.getInt(1); //or rs.getString(1); or rs.getObject(1);
}
```

## <a name="using-stored-procedures-with-sqlvariant"></a>Utilisation de procédures stockées avec sql_variant :   
Avoir une procédure stockée comme :     

```java
String sql = "CREATE PROCEDURE " + inputProc + " @p0 sql_variant OUTPUT AS SELECT TOP 1 @p0=col1 FROM sampleTable ";
``` 
    
Paramètres de sortie doivent être enregistrés :

```java
try (CallableStatement callableStatement = con.prepareCall(" {call " + inputProc + " (?) }")) {
    callableStatement.registerOutParameter(1, microsoft.sql.Types.SQL_VARIANT);      
    callableStatement.execute();
}
```

## <a name="limitations-of-sqlvariant"></a>Limitations de sql_variant :
- Lors de l’utilisation de TVP pour remplir une table avec un `datetime` / `smalldatetime` / `date` valeur stockée dans un type sql_variant, appelant `getDateTime()` / `getSmallDateTime()` / `getDate()` sur un Jeu de résultats ne fonctionne pas et lève l’exception suivante :
    
    `Java.lang.String cannot be cast to java.sql.Timestamp`
   
    Solution de contournement : utilisez `getString()` ou `getObject()` à la place. 
    
- L’utilisation de TVP pour remplir une table et l’envoi d’une valeur null dans un type sql_variant ne sont pas pris en charge et lève une exception :
    
    `Inserting null value with column type sql_variant in TVP is not supported.`

## <a name="see-also"></a>Voir aussi

[Présentation des types de données du pilote JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
