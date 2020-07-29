---
title: Informations de référence sur azdata bdc endpoint
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc endpoint.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 242290998de52eb10b09bf03a8f67c44da9e2f2f
ms.sourcegitcommit: 591bbf4c7e4e2092f8abda6a2ffed263cb61c585
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86943031"
---
# <a name="azdata-bdc-endpoint"></a>azdata bdc endpoint

[!INCLUDE[SQL Server 2019](../includes/applies-to-version/sqlserver2019.md)]

L’article suivant fournit des références sur les commandes `sql` disponibles dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
| Commande | Description |
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
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour des journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil `azdata`, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
