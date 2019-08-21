---
title: Connexion de bouclage à SQL Server à partir d’un script Python ou R
description: Découvrez comment utiliser une connexion de bouclage pour vous reconnecter à SQL Server sur ODBC pour lire ou écrire des données à partir d’un script Python ou R exécuté à partir de sp_execute_external_script. Vous pouvez l’utiliser lorsque vous ne pouvez pas utiliser les arguments InputDataSet et OutputDataSet de sp_execute_external_script.
ms.prod: sql
ms.technology: machine-learning
ms.date: 08/21/2019
ms.topic: conceptual
author: Aniruddh25
ms.author: anmunde
ms.reviewer: dphansen
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 62b4ce483df2d38e5e2549d054c02b6c797837f3
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69657486"
---
# <a name="loopback-connection-to-sql-server-from-a-python-or-r-script"></a>Connexion de bouclage à SQL Server à partir d’un script Python ou R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Découvrez comment utiliser une connexion de bouclage pour vous reconnecter à SQL Server sur [ODBC](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md) pour lire ou écrire des données à partir d’un script Python `sp_execute_external_script`ou R exécuté à partir de. Vous pouvez l’utiliser lorsque les `sp_execute_external_script` arguments **InputDataSet** et **OutputDataSet** ne sont pas possibles.

## <a name="connection-string"></a>Chaîne de connexion

Pour établir une connexion de bouclage, vous devez utiliser une chaîne de connexion correcte. Les arguments obligatoires courants sont le nom du [pilote ODBC](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md), l’adresse du serveur et le nom de la base de données.

### <a name="connection-string-on-windows"></a>Chaîne de connexion sur Windows

Pour l’authentification sur SQL Server sur Windows, le script Python ou R peut utiliser l’attribut de chaîne de connexion **Trusted_Connection** pour s’authentifier en tant qu’utilisateur qui a exécuté le sp_execute_external_script.

Voici un exemple de chaîne de connexion de bouclage sur Windows:

``` 
"Driver=SQL Server;Server=.;Database=nameOfDatabase;Trusted_Connection=Yes;"
```

### <a name="connection-string-on-linux"></a>Chaîne de connexion sur Linux

Pour l’authentification sur SQL Server sur Linux, le script Python ou R doit utiliser les attributs **ClientCertificate** et **CLIENTKEY vide** du pilote ODBC pour s’authentifier en tant qu’utilisateur `sp_execute_external_script`qui a exécuté. Cela nécessite l’utilisation de la dernière version du [pilote ODBC](../../connect/odbc/download-odbc-driver-for-sql-server.md) 17.4.1.1.

Voici un exemple de chaîne de connexion de bouclage sur Linux:

```
"Driver=ODBC Driver 17 for SQL Server;Server=fe80::8012:3df5:0:5db1%eth0;Database=nameOfDatabase;ClientCertificate=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitecert.pem;ClientKey=file:/var/opt/mssql-extensibility/data/baeaac72-60b3-4fae-acfd-c50eff5d34a2/sqlsatellitekey.pem;TrustServerCertificate=Yes;Trusted_Connection=no;Encrypt=Yes"
```

L’adresse du serveur, l’emplacement du fichier de certificat client et l’emplacement du fichier de `sp_execute_external_script` clé client sont uniques à chaque et peuvent être obtenus à l’aide de l’API **rx_get_sql_loopback_connection_string ()** pour Python ou  **rxGetSqlLoopbackConnectionString ()** pour R.

Pour plus d’informations sur les attributs de chaîne de connexion, consultez les [Mots clés et attributs de chaîne de connexion et DSN](https://docs.microsoft.com/sql/connect/odbc/dsn-connection-string-attribute?view=sql-server-linux-ver15#new-connection-string-keywords-and-connection-attributes) pour Microsoft ODBC Driver for SQL Server.

## <a name="generate-connection-string-with-revoscalepy-for-python"></a>Générer une chaîne de connexion avec revoscalepy pour Python

Vous pouvez utiliser l’API **rx_get_sql_loopback_connection_string ()** dans [revoscalepy](../python/ref-py-revoscalepy.md) pour générer une chaîne de connexion correcte pour une connexion de bouclage dans un script Python.

Il accepte les arguments suivants:

| Argument | Description |
|-|-|
| name_of_database | Nom de la base de données à laquelle la connexion doit être établie |
| odbc_driver | Nom du pilote ODBC |

### <a name="examples"></a>Exemples

Exemple pour SQL Server sur Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="SQL Server", name_of_database="DBName")
print("Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Exemple pour SQL Server sur Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'Python',
@script = N'
from revoscalepy import rx_get_sql_loopback_connection_string, RxSqlServerData, rx_data_step
loopback_connection_string = rx_get_sql_loopback_connection_string(odbc_driver="ODBC Driver 17 for SQL Server",
                                                                   name_of_database="DBName")
print("Loopback Connection String:{0}".format(loopback_connection_string))
data_set = RxSqlServerData(sql_query = "select col1, col2 from tableName",
                           connection_string = loopback_connection_string)
OutputDataSet = rx_data_step(data_set)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="generate-connection-string-with-revoscaler-for-r"></a>Générer une chaîne de connexion avec RevoScaleR pour R

Vous pouvez utiliser l’API **rxGetSqlLoopbackConnectionString ()** dans [RevoScaleR](../r/ref-r-revoscaler.md) pour générer une chaîne de connexion correcte pour une connexion de bouclage dans un script R.

Il accepte les arguments suivants:

| Argument | Description |
|-|-|
| nameOfDatabase | Nom de la base de données à laquelle la connexion doit être établie |
| odbcDriver | Nom du pilote ODBC |

### <a name="examples"></a>Exemples

Exemple pour SQL Server sur Windows:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <- rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", odbcDriver ="SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName",
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

Exemple pour SQL Server sur Linux:

```sql
EXECUTE sp_execute_external_script
@language = N'R',
@script = N'
    loopbackConnectionString <-  rxGetSqlLoopbackConnectionString(nameOfDatabase="DBName", 
                                                                  odbcDriver ="ODBC Driver 17 for SQL Server")
    print(paste("Connection String:", loopbackConnectionString))
    dataSet <- RxSqlServerData(sqlQuery = "select col1, col2 from tableName", 
                               connectionString = loopbackConnectionString)
    OutputDataSet <- rxDataStep(dataSet)
'
WITH RESULT SETS ((col1 int, col2 int))
GO
```

## <a name="next-steps"></a>Étapes suivantes

+ [Pilote Microsoft ODBC pour SQL Server](../../connect/odbc/microsoft-odbc-driver-for-sql-server.md)
+ [revoscalepy](../python/ref-py-revoscalepy.md)
+ [RevoScaleR](../r/ref-r-revoscaler.md)
