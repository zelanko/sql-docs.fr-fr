---
title: Informations de référence sur azdata bdc
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 731b8c169816b365469521e2b8c952044599b68c
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242375"
---
# <a name="azdata-bdc-status"></a>azdata bdc status

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

L’article suivant fournit des références sur les commandes `sql` disponibles dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
| Commande | Description |
| --- | --- |
[azdata bdc status show](#azdata-bdc-status-show) | Indique l’état du cluster Big Data.
## <a name="azdata-bdc-status-show"></a>azdata bdc status show
Indique l’état du cluster Big Data.
```bash
azdata bdc status show [--resource -r] 
                       [--all -a]
```
### <a name="examples"></a>Exemples
État du cluster Big Data où l’utilisateur est connecté.
```bash
azdata bdc status show
```
État du cluster Big Data avec toutes les instances des ressources incluses.
```bash
azdata bdc status show --all
```
État du cluster Big Data des services qui incluent la ressource de contrôle.
```bash
azdata bdc status show --resource control
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--resource -r`
Obtenez les services associés à cette ressource.
#### `--all -a`
Affichez toutes les instances de chaque ressource dans les services.
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
