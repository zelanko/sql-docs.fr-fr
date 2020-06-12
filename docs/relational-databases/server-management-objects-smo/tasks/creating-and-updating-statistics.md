---
title: Créer et mettre à jour des statistiques
ms.prod: sql
ms.prod_service: database-engine
ms.technology: smo
ms.topic: reference
helpviewer_keywords: statistical information [SMO]
ms.assetid: 47a0a172-a969-4deb-bca9-dd04401a0fe1
author: markingmyname
ms.author: maghan
ms.reviewer: matteot
ms.custom: seo-dt-2019
ms.date: 06/04/2020
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5c90feb8f12be713f56a5fc6705f8c71908eb5fd
ms.sourcegitcommit: 38639b67a135ca1a50a8e38fa61a089efe90e3f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84454512"
---
# <a name="create-and-update-statistics"></a>Créer et mettre à jour des statistiques

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Dans SMO, les informations statistiques à propos du traitement de requêtes dans la base de données peuvent être recueillies en utilisant l'objet <xref:Microsoft.SqlServer.Management.Smo.Statistic>.

Il est possible de créer des statistiques pour n’importe quelle colonne à l’aide de l' <xref:Microsoft.SqlServer.Management.Smo.Statistic> <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> objet et. La méthode <xref:Microsoft.SqlServer.Management.Smo.Statistic.Update%2A> peut être exécutée pour mettre à jour les statistiques dans l'objet <xref:Microsoft.SqlServer.Management.Smo.Statistic>. Les résultats peuvent être affichés dans l'optimiseur de requête.

## <a name="example"></a>Exemple

Pour utiliser un exemple de code fourni, vous pouvez choisir l’environnement de programmation, le modèle de programmation et le langage de programmation dans lequel créer votre application. Pour plus d’informations, consultez [créer un projet Visual C&#35; Smo dans Visual Studio .net](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).

## <a name="create-and-update-statistics-in-visual-basic"></a>Créer et mettre à jour des statistiques dans Visual Basic

Cet exemple de code crée une table sur une base de données existante pour laquelle l'objet <xref:Microsoft.SqlServer.Management.Smo.Statistic> et l'objet <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> sont créés.

```vb
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Reference the CreditCard table.
Dim tb As Table
tb = db.Tables("CreditCard", "Sales")
'Define a Statistic object by supplying the parent table and name arguments in the constructor.
Dim stat As Statistic
stat = New Statistic(tb, "Test_Statistics")
'Define a StatisticColumn object variable for the CardType column and add to the Statistic object variable.
Dim statcol As StatisticColumn
statcol = New StatisticColumn(stat, "CardType")
stat.StatisticColumns.Add(statcol)
'Create the statistic counter on the instance of SQL Server.
stat.Create()
```

## <a name="create-and-update-statistics-in-c"></a>Créer et mettre à jour des statistiques en C #

Cet exemple de code crée une table sur une base de données existante pour laquelle l'objet <xref:Microsoft.SqlServer.Management.Smo.Statistic> et l'objet <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> sont créés.

```csharp
public static void CreatingAndUpdatingStatistics()
{
    // Connect to the local, default instance of SQL Server.
    var srv = new Server();

    // Reference the AdventureWorks2012 database.
    var db = srv.Databases["AdventureWorks"];

    // Reference the CreditCard table.
    var tb = db.Tables["CreditCard", "Sales"];

    // Define a Statistic object by supplying the parent table and name
    // arguments in the constructor.
    var stat = new Statistic(tb, "Test_Statistics");

    // Define a StatisticColumn object variable for the CardType column
    // and add to the Statistic object variable.
    var statcol = new StatisticColumn(stat, "CardType");
    stat.StatisticColumns.Add(statcol);

    //Create the statistic counter on the instance of SQL Server.
    stat.Create();

    // List all the statistics object on the table (you will see the newly created one)
    foreach (var s in tb.Statistics.Cast<Statistic>())
        Console.WriteLine($"{s.ID}\t{s.Name}");

    // Output:
    //  2       AK_CreditCard_CardNumber
    //  1       PK_CreditCard_CreditCardID
    //  3       Test_Statistics
 }
```

## <a name="create-and-update-statistics-in-powershell"></a>Créer et mettre à jour des statistiques dans PowerShell

Cet exemple de code crée une table sur une base de données existante pour laquelle l'objet <xref:Microsoft.SqlServer.Management.Smo.Statistic> et l'objet <xref:Microsoft.SqlServer.Management.Smo.StatisticColumn> sont créés.

```powershell
Import-Module SQLServer

# Connect to the local, default instance of SQL Server.  
$srv = Get-Item SQLSERVER:\SQL\localhost\DEFAULT

# Reference the AdventureWorks database.
$db = $srv.Databases["AdventureWorks"]

# Reference the CreditCard table.
$tb = $db.Tables["CreditCard", "Sales"]

# Define a Statistic object by supplying the parent table and name
# arguments in the constructor.
$stat = New-Object Microsoft.SqlServer.Management.Smo.Statistic($tb, "Test_Statistics")

# Define a StatisticColumn object variable for the CardType column
# and add to the Statistic object variable.
$statcol = New-Object Microsoft.SqlServer.Management.Smo.StatisticColumn($stat, "CardType")
$stat.StatisticColumns.Add($statcol)

# Create the statistic counter on the instance of SQL Server.
$stat.Create()

# Finally dump all the statistics (you can see the newly created one at the bottom)
$tb.Statistics

# Output:
# Name                                Last Updated Is From Index  Statistic Columns
#                                                  Creation
# ----                                ------------ -------------- -----------------
# AK_CreditCard_CardNumber      10/27/2017 2:33 PM True           {CardNumber}
# PK_CreditCard_CreditCardID    10/27/2017 2:33 PM True           {CreditCardID}
# Test_Statistics                 6/4/2020 8:11 PM False          {CardType}
```
