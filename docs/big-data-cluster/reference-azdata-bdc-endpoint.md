---
title: Informations de référence sur azdata bdc endpoint
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc endpoint.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 71f52b8312518cf669751d50dcc857c3d892bd98
ms.sourcegitcommit: db1b6153f0bc2d221ba1ce15543ecc83e1045453
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82588075"
---
# <a name="azdata-bdc-endpoint"></a>azdata bdc endpoint

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

L’article suivant fournit des références sur la commande `bdc endpoint` disponible dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc endpoint list](#azdata-bdc-endpoint-list) | Lister les points de terminaison du cluster Big Data.
## <a name="azdata-bdc-endpoint-list"></a>azdata bdc endpoint list
Lister les points de terminaison du cluster Big Data.

```bash
azdata bdc endpoint list [--endpoint-name -e] 
```

### <a name="optional-parameters"></a>Paramètres facultatifs

#### `--endpoint-name -e`

Nom du point de terminaison du cluster Big Data.

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
