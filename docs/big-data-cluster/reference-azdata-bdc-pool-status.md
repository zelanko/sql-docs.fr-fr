---
title: référence d’État du pool BDC azdata
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes d’État du pool azdata BDC.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d0a5925af4f16f2147988b2318880d9acec664c3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426129"
---
# <a name="azdata-bdc-pool-status"></a>État du pool BDC azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes d' **État du pool BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[affichage de l’état du pool BDC azdata](#azdata-bdc-pool-status-show) | État du pool.
## <a name="azdata-bdc-pool-status-show"></a>affichage de l’état du pool BDC azdata
État du pool.
```bash
azdata bdc pool status show --kind -k 
                            [--name -n]
```
### <a name="examples"></a>Exemples
Obtient l’état du pool de stockage.
```bash
azdata bdc pool status show --kind storage --name default
```
Obtient l’état du pool de données.
```bash
azdata bdc pool status show --kind data --name default
```
Obtient l’état du pool de calcul.
```bash
azdata bdc pool status show --kind compute --name default
```
Obtient l’état du pool principal.
```bash
azdata bdc pool status show --kind master --name default
```
Obtient l’état du pool Spark.
```bash
azdata bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--kind -k`
Type de pool de clusters Big Data.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du pool de clusters Big Data.
`default`
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
