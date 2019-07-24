---
title: Référence du point de terminaison BDC azdata
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de point de terminaison azdata BDC.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: db24ca1ca1bb6fa25ddd7486fe041ea54722276c
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426209"
---
# <a name="azdata-bdc-endpoint"></a>point de terminaison BDC azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes de **point de terminaison BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[liste de points de terminaison BDC azdata](#azdata-bdc-endpoint-list) | Répertorie les points de terminaison pour le cluster Big Data.
## <a name="azdata-bdc-endpoint-list"></a>liste de points de terminaison BDC azdata
Répertorie les points de terminaison pour le cluster Big Data.
```bash
azdata bdc endpoint list [--endpoint-name -e] 
                         
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--endpoint-name -e`
Nom du point de terminaison du cluster Big Data.
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

Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md). Pour plus d’informations sur l’installation de l’outil **azdata** , consultez [installer azdata pour gérer les clusters SQL Server 2019 Big Data](deploy-install-azdata.md).
