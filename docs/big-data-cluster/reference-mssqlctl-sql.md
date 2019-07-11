---
title: mssqlctl sql reference
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes sql mssqlctl.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 844ea94e9df18132fd0729745ff154783b578fc1
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728508"
---
# <a name="mssqlctl-sql"></a>mssqlctl sql

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **sql** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[mssqlctl sql shell](#mssqlctl-sql-shell) | L’interface de base de données SQL CLI permet à l’utilisateur d’interagir avec SQL Server par le biais de T-SQL.
[mssqlctl sql query](#mssqlctl-sql-query) | La commande de requête autorise l’exécution d’une requête T-SQL.
## <a name="mssqlctl-sql-shell"></a>mssqlctl sql shell
L’interface de base de données SQL CLI permet à l’utilisateur d’interagir avec SQL Server par le biais de T-SQL.
```bash
mssqlctl sql shell 
```
### <a name="examples"></a>Exemples
Exemple de ligne de commande pour démarrer l’expérience interactive.
```bash
mssqlctl sql shell
```
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.
## <a name="mssqlctl-sql-query"></a>requête sql de mssqlctl
La commande de requête autorise l’exécution d’une requête T-SQL.
```bash
mssqlctl sql query --database -d 
                   -q
```
### <a name="examples"></a>Exemples
Sélectionnez la liste des noms de tables.  Valeurs par défaut de la base de données maître.
```bash
mssqlctl sql query 'SELECT name FROM SYS.TABLES'
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--database -d`
Base de données pour exécuter la requête.  Valeur par défaut est master.
#### `-q`
Requête T-SQL à exécuter.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).