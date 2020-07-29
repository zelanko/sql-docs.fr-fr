---
title: Informations de référence sur azdata bdc gateway status
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc gateway status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 30410e4acbaa6b52228c89334c9ee8a26a80d5b4
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87243057"
---
# <a name="azdata-bdc-gateway-status"></a>azdata bdc gateway status

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

L’article suivant fournit des références sur les commandes `sql` disponibles dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
| Commande | Description |
| --- | --- |
[azdata bdc gateway status show](#azdata-bdc-gateway-status-show) | État du service de passerelle.
## <a name="azdata-bdc-gateway-status-show"></a>azdata bdc gateway status show
État du service de passerelle.
```bash
azdata bdc gateway status show [--resource -r] 
                               [--all -a]
```
### <a name="examples"></a>Exemples
Obtenez l’état du service de passerelle.
```bash
azdata bdc gateway status show
```
Obtenez l’état du service de passerelle avec toutes les instances.
```bash
azdata bdc gateway status show --all
```
Obtenez l’état de la ressource de passerelle au sein du service de passerelle.
```bash
azdata bdc gateway status show --resource gateway
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
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil `azdata`, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
