---
title: Informations de référence sur les commandes azdata bdc pool status
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc pool status
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ee49ee09107c98047bd5aea849b9ae486eb6736a
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70153113"
---
# <a name="azdata-bdc-pool-status"></a>azdata bdc pool status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)] 

Cet article est un article de référence pour **azdata**. 

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc pool status show](#azdata-bdc-pool-status-show) | État du pool.
## <a name="azdata-bdc-pool-status-show"></a>azdata bdc pool status show
État du pool.
```bash
azdata bdc pool status show --kind -k 
                            [--name -n]
```
### <a name="examples"></a>Exemples
Obtenir l’état du pool de stockage.
```bash
azdata bdc pool status show --kind storage --name default
```
Obtenir l’état du pool de données.
```bash
azdata bdc pool status show --kind data --name default
```
Obtenir l’état du pool de calcul.
```bash
azdata bdc pool status show --kind compute --name default
```
Obtenir l’état du pool principal.
```bash
azdata bdc pool status show --kind master --name default
```
Obtenir l’état du pool spark.
```bash
azdata bdc pool status show --kind spark --name default
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--kind -k`
Type de pool du cluster Big Data.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--name -n`
Nom du pool du cluster Big Data.
`default`
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmentez le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Affichez ce message d’aide et quittez.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur les autres commandes **azdata**, consultez [azdata reference](reference-azdata.md). 

- Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
