---
title: "Copie de données vers SQL Server sur Linux | Documents Microsoft"
description: 
author: sanagama
ms.author: sanagama
manager: jhubbard
ms.date: 10/02/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 7b93d0d7-7946-4b78-b33a-57d6307cdfa9
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 1463c56a247a2d578fc0a69f96cb8ead829dfba3
ms.contentlocale: fr-fr
ms.lasthandoff: 10/02/2017

---
# <a name="bulk-copy-data-with-bcp-to-sql-server-on-linux"></a>Données de copie en bloc avec bcp à SQL Server sur Linux

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

Cette rubrique montre comment utiliser le [bcp](../tools/bcp-utility.md) utilitaire de ligne de commande pour copier en bloc des données entre une instance de 2017 du serveur SQL sur Linux et un fichier de données dans un format spécifié par l’utilisateur.

Vous pouvez utiliser `bcp` pour importer un grand nombre de lignes dans des tables SQL Server ou pour exporter des données à partir de tables SQL Server dans les fichiers de données. Sauf lorsqu’il est utilisé avec l’option queryout, `bcp` ne nécessite aucune connaissance de Transact-SQL. Le `bcp` utilitaire de ligne de commande fonctionne avec Microsoft SQL Server exécuté localement ou dans le cloud, sur Linux, Windows ou Docker et base de données SQL Azure et Azure SQL Data Warehouse.

Cette rubrique vous indiquent comment à :
- Importer des données dans une table à l’aide de la `bcp in` commande
- Exporter les données d’une table d’utilisant le `bcp out` commande

## <a name="install-the-sql-server-command-line-tools"></a>Installer les outils de ligne de commande SQL Server

`bcp`fait partie des outils de ligne de commande SQL Server, qui ne sont pas installés automatiquement avec SQL Server sur Linux. Si vous n’avez pas déjà installé les outils de ligne de commande de SQL Server sur l’ordinateur Linux, vous devez les installer. Pour plus d’informations sur la façon d’installer les outils, sélectionnez votre distribution Linux à partir de la liste suivante :

- [Red Hat Enterprise Linux (RHEL)](sql-server-linux-setup-tools.md#RHEL)
- [Ubuntu](sql-server-linux-setup-tools.md#ubuntu)
- [SUSE Linux Enterprise Server (SLES)](sql-server-linux-setup-tools.md#SLES)

## <a name="import-data-with-bcp"></a>Importer des données avec bcp

Dans ce didacticiel, vous allez créer une base de données exemple et une table sur l’instance de SQL Server locale (**localhost**), puis utilisez `bcp` à charger dans la table d’exemple à partir d’un fichier texte sur le disque.

### <a name="create-a-sample-database-and-table"></a>Créer une base de données exemple et une table

Commençons par la création d’une base de données exemple avec une table simple qui sera utilisée dans le reste de ce didacticiel.

1. Dans votre boîte de Linux, ouvrez un terminal de commande.

2. Copiez et collez les commandes ci-dessous dans la fenêtre de Terminal Server. Ces commandes utilisent le **sqlcmd** utilitaire de ligne de commande pour créer une base de données exemple (**BcpSampleDB**) et une table (**TestEmployees**) sur l’instance de SQL Server locale (**localhost**). N’oubliez pas de remplacer le `username` et `<your_password>` si nécessaire avant d’exécuter les commandes.

Créer la base de données **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -Q "CREATE DATABASE BcpSampleDB;"
```
Créer la table **TestEmployees** dans la base de données **BcpSampleDB**:
```bash 
sqlcmd -S localhost -U sa -P <your_password> -d BcpSampleDB -Q "CREATE TABLE TestEmployees (Id INT IDENTITY(1,1) NOT NULL PRIMARY KEY, Name NVARCHAR(50), Location NVARCHAR(50));"
```
### <a name="create-the-source-data-file"></a>Créez le fichier de données source
Copiez et collez la commande ci-dessous dans votre fenêtre de terminal. Nous allons utiliser la fonction intégrée `cat` commande pour créer un fichier de données texte avec 3 enregistrements enregistrez le fichier dans votre répertoire de base en tant que **~/test_data.txt**. Les champs dans les enregistrements sont délimités par une virgule.

```bash
cat > ~/test_data.txt << EOF
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
EOF
```

Vous pouvez vérifier que le fichier de données a été correctement créé en exécutant la commande ci-dessous dans votre fenêtre de terminal :
```bash 
cat ~/test_data.txt
```

Il doit afficher les éléments suivants dans la fenêtre de Terminal Server :
```bash
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

### <a name="import-data-from-the-source-data-file"></a>Importer des données à partir du fichier de données source
Copiez et collez les commandes ci-dessous dans la fenêtre de Terminal Server. Cette commande utilise `bcp` pour se connecter à l’instance de SQL Server locale (**localhost**) et importer les données à partir du fichier de données (**~/test_data.txt**) dans la table (**TestEmployees**) dans la base de données (**BcpSampleDB**). N’oubliez pas de remplacer le nom d’utilisateur et `<your_password>` si nécessaire avant d’exécuter les commandes.

```bash 
bcp TestEmployees in ~/test_data.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t  ','
```

Voici une brève vue d’ensemble des paramètres de ligne de commande que nous avons utilisé avec `bcp` dans cet exemple :
- `-S`: Spécifie l’instance de SQL Server à laquelle se connecter
- `-U`: Spécifie l’ID de connexion utilisé pour se connecter à SQL Server
- `-P`: Spécifie le mot de passe pour l’ID de connexion
- `-d`: Spécifie la base de données pour se connecter à
- `-c`: effectue des opérations à l’aide d’un type de données caractère
- `-t`: Spécifie la marque de fin de champ. Nous utilisons `comma` comme indicateur de fin de champ pour les enregistrements dans notre fichier de données

> [!NOTE]
> Nous spécifions pas une marque de fin de ligne personnalisée dans cet exemple. Les lignes dans le fichier de données de texte ont été terminées correctement avec `newline` lorsque nous avons utilisé le `cat` commande pour créer le fichier de données précédemment.

Vous pouvez vérifier que les données n’a été importées en exécutant la commande ci-dessous dans votre fenêtre de terminal. N’oubliez pas de remplacer le `username` et `<your_password>` si nécessaire avant d’exécuter la commande.
```bash 
sqlcmd -S localhost -d BcpSampleDB -U sa -P <your_password> -I -Q "SELECT * FROM TestEmployees;"
```

Il doit afficher les résultats suivants :
```bash
Id          Name                Location
----------- ------------------- -------------------
          1 Jared               Australia
          2 Nikita              India
          3 Tom                 Germany

(3 rows affected)
```

## <a name="export-data-with-bcp"></a>Exporter des données avec bcp

Dans ce didacticiel, vous allez utiliser `bcp` pour exporter des données à partir de la table d’exemple que nous avons créées précédemment dans un fichier de données.

Copiez et collez les commandes ci-dessous dans la fenêtre de Terminal Server. Ces commandes utilisent le `bcp` utilitaire de ligne de commande pour exporter des données à partir de la table **TestEmployees** dans le dans la base de données **BcpSampleDB** vers un nouveau fichier de données appelé **~/test_export.txt**.  N’oubliez pas de remplacer le nom d’utilisateur et `<your_password>` si nécessaire avant d’exécuter la commande.

```bash 
bcp TestEmployees out ~/test_export.txt -S localhost -U sa -P <your_password> -d BcpSampleDB -c -t ','
```

Vous pouvez vérifier que les données ont été correctement exportées en exécutant la commande ci-dessous dans votre fenêtre de terminal :
```bash 
cat ~/test_export.txt
```

Il doit afficher les éléments suivants dans la fenêtre de Terminal Server :
```
1,Jared,Australia
2,Nikita,India
3,Tom,Germany
```

## <a name="see-also"></a>Voir aussi
- [bcp (utilitaire)](../tools/bcp-utility.md)
- [Formats de données pour la compatibilité lors de l’utilisation de bcp](../relational-databases/import-export/specify-data-formats-for-compatibility-when-using-bcp-sql-server.md)
- [Importer des données en bloc à l’aide de BULK INSERT](../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)
- [INSERTION en bloc (Transact-SQL)](../t-sql/statements/bulk-insert-transact-sql.md)

