---
title: référence d’état mssqlctl bdc pool
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes d’état pool mssqlctl bdc.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b6eba925adeb7f18adff133ba8110c6766bfed79
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67394311"
---
# <a name="mssqlctl-bdc-pool-status"></a>mssqlctl bdc pool status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **état du pool bdc** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[afficher d’état mssqlctl bdc pool](#mssqlctl-bdc-pool-status-show) | État du pool.
## <a name="mssqlctl-bdc-pool-status-show"></a>afficher d’état mssqlctl bdc pool
État du pool.
```bash
mssqlctl bdc pool status show --kind -k 
                              [--name -n]
```
### <a name="examples"></a>Exemples
Obtenir l’état du pool de stockage.
```bash
mssqlctl bdc pool status show --kind storage --name default
```
Obtenir l’état du pool de données.
```bash
mssqlctl bdc pool status show --kind data --name default
```
Obtenir l’état du pool de calcul.
```bash
mssqlctl bdc pool status show --kind compute --name default
```
Obtenir l’état du pool principal.
```bash
mssqlctl bdc pool status show --kind master --name default
```
Obtenir l’état du pool de spark.
```bash
mssqlctl bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--kind -k`
Type de pool BDC.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du pool BDC.
`default`
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).