---
title: Informations de référence sur les commandes azdata bdc pool status
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc pool status
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/21/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: eafc72c6d86d38eabd26b735a9d5dab967e2e6be
ms.sourcegitcommit: 5e838bdf705136f34d4d8b622740b0e643cb8d96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69653482"
---
# <a name="azdata-bdc-pool-status"></a>azdata bdc pool status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes **bdc pool status** dans l’outil **azdata**. Pour plus d’informations sur les autres commandes de l’outil **azdata**, consultez [Informations de référence sur azdata](reference-azdata.md).

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

Pour plus d’informations sur l’installation de l’outil **azdata** , consultez [installer azdata pour [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]gérer ](deploy-install-azdata.md).
