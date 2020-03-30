---
title: Informations de référence sur azdata bdc app status
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc app status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8322db228d67fc4341e3138c8a79079114065ba5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "74820941"
---
# <a name="azdata-bdc-app-status"></a>azdata bdc app status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

L’article suivant fournit des références sur les commandes `bdc app status` disponibles dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc app status show](#azdata-bdc-app-status-show) | État du service App Service.
## <a name="azdata-bdc-app-status-show"></a>azdata bdc app status show
État du service App Service.
```bash
azdata bdc app status show [--resource -r] 
                           [--all -a]
```
### <a name="examples"></a>Exemples
Obtenez l’état du service App Service.
```bash
azdata bdc app status show
```
Obtenez l’état du service App Service avec toutes les instances.
```bash
azdata bdc app status show --all
```
Obtenez l’état de la ressource de proxy d’application au sein du service App Service.
```bash
azdata bdc app status show --resource appproxy
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--resource -r`
Obtenez cette ressource dans ce service.
#### `--all -a`
Affichez toutes les instances de chaque ressource dans le service.
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
