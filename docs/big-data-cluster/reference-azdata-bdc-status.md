---
title: Informations de référence sur azdata bdc
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 15fec084fc6ff5d7b3e62ec0b775047aa9bc59db
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68426049"
---
# <a name="azdata-bdc-status"></a>azdata bdc status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes **bdc status** dans l’outil **azdata**. Pour plus d’informations sur les autres commandes **azdata**, consultez les [informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc status show](#azdata-bdc-status-show) | Affiche l’état du cluster Big Data.
## <a name="azdata-bdc-status-show"></a>azdata bdc status show
Affiche l’état du cluster Big Data.
```bash
azdata bdc status show 
```
### <a name="examples"></a>Exemples
État du cluster Big Data où l’utilisateur est connecté.
```bash
azdata bdc status show
```
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmenter le niveau de détail de la journalisation pour montrer tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et quitter.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Valeur par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Pour plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmenter le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes **azdata**, consultez les [informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
