---
title: référence SQL azdata
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes SQL azdata.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 90512592901fcf83e4697b5eefc80a6df7aeb032
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426019"
---
# <a name="azdata-sql"></a>azdata SQL

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes **SQL** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata SQL shell](#azdata-sql-shell) | L’interface CLI de SQL DB permet à l’utilisateur d’interagir avec SQL Server via T-SQL.
[requête SQL azdata](#azdata-sql-query) | La commande de requête permet l’exécution d’une requête T-SQL.
## <a name="azdata-sql-shell"></a>azdata SQL shell
L’interface CLI de SQL DB permet à l’utilisateur d’interagir avec SQL Server via T-SQL.
```bash
azdata sql shell 
```
### <a name="examples"></a>Exemples
Exemple de ligne de commande pour démarrer l’expérience interactive.
```bash
azdata sql shell
```
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées: JSON, jsonc, table, TSV.  Valeur par défaut: JSON.
#### `--query -q`
Chaîne de requête JMESPath. Pour [http://jmespath.org/](http://jmespath.org/]) plus d’informations et d’exemples, consultez.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="azdata-sql-query"></a>requête SQL azdata
La commande de requête permet l’exécution d’une requête T-SQL.
```bash
azdata sql query --database -d 
                 -q
```
### <a name="examples"></a>Exemples
Sélectionnez la liste des noms de tables.  La base de données est définie par défaut sur Master.
```bash
azdata sql query 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--database -d`
Base de données dans laquelle exécuter la requête.  La valeur par défaut est Master.
#### `-q`
Requête T-SQL à exécuter.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées: JSON, jsonc, table, TSV.  Valeur par défaut: JSON.
#### `--query -q`
Chaîne de requête JMESPath. Pour [http://jmespath.org/](http://jmespath.org/]) plus d’informations et d’exemples, consultez.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’installation de l’outil **azdata** , consultez [installer azdata pour gérer les clusters SQL Server 2019 Big Data](deploy-install-azdata.md).
