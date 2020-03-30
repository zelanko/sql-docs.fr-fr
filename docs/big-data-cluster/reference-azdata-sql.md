---
title: Informations de référence sur azdata sql
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata sql.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f8fa1ca8df7f4d72c6df9b252d639f8771dee30c
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "74908736"
---
# <a name="azdata-sql"></a>azdata sql

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

L’article suivant fournit des références sur les commandes `sql` disponibles dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
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
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.
## <a name="azdata-sql-query"></a>azdata sql query
La commande query permet l’exécution d’une requête T-SQL.
```bash
azdata sql query -q --database -d
```
### <a name="examples"></a>Exemples
Sélectionner la liste des noms des tables.  La base de données est « master » par défaut.
```bash
azdata sql query -q 'SELECT name FROM SYS.TABLES'
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
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil `azdata`, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
