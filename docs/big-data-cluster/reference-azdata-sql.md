---
title: Informations de référence sur azdata sql
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata sql.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: bb7dd195d489be289cf434e8e4651ac17c6a6709
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242980"
---
# <a name="azdata-sql"></a>azdata sql

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

L’article suivant fournit des références sur les commandes `sql` disponibles dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
| Commande | Description |
| --- | --- |
[azdata sql shell](#azdata-sql-shell) | L’interface CLI SQL DB permet à l’utilisateur d’interagir avec SQL Server via T-SQL.
[azdata sql query](#azdata-sql-query) | La commande query permet l’exécution d’une requête T-SQL.
## <a name="azdata-sql-shell"></a>azdata sql shell
L’interface CLI SQL DB permet à l’utilisateur d’interagir avec SQL Server via T-SQL.
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
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-sql-query"></a>azdata sql query
La commande query permet l’exécution d’une requête T-SQL.
```bash
azdata sql query --database -d 
                 -q
```
### <a name="examples"></a>Exemples
Sélectionner la liste des noms des tables.  La base de données est « master » par défaut.
```bash
azdata sql query "SELECT name FROM SYS.TABLES"
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--database -d`
Base de données où exécuter la requête.  La base de données est « master » par défaut.
#### `-q`
Requête T-SQL à exécuter.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil `azdata`, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
