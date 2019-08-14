---
title: Informations de référence sur azdata bdc control status
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc control status
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: d1f7e2e5931ec55cd2fd2632072de223db252b84
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426249"
---
# <a name="azdata-bdc-control-status"></a>azdata bdc control status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes **bdc control status** dans l’outil **azdata**. Pour plus d’informations sur les autres commandes **azdata**, consultez les [informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc control status show](#azdata-bdc-control-status-show) | État du contrôle.
## <a name="azdata-bdc-control-status-show"></a>azdata bdc control status show
État du contrôle.
```bash
azdata bdc control status show 
```
### <a name="examples"></a>Exemples
Obtenir l’état du contrôle.
```bash
azdata bdc control status show
```
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmenter le niveau de détail de la journalisation pour afficher tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et quitter.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmenter le niveau de détail de la journalisation. Utilisez --debug pour obtenir des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
