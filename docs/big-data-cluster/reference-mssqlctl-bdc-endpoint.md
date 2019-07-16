---
title: référence de point de terminaison mssqlctl bdc
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de point de terminaison mssqlctl bdc.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 06/26/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: ae9a5ad79f388f260494c18448dd80e815b3ac02
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67958087"
---
# <a name="mssqlctl-bdc-endpoint"></a>point de terminaison mssqlctl bdc

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **bdc le point de terminaison** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[liste de point de terminaison mssqlctl bdc](#mssqlctl-bdc-endpoint-list) | Répertorie les points de terminaison pour le Cluster de données volumineuses.
## <a name="mssqlctl-bdc-endpoint-list"></a>liste de point de terminaison mssqlctl bdc
Répertorie les points de terminaison pour le Cluster de données volumineuses.
```bash
mssqlctl bdc endpoint list [--endpoint-name -e] 
                           
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--endpoint-name -e`
Nom du point de terminaison BDC.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de la journalisation pour afficher tous les journaux d’activité de débogage.
#### `--help -h`
Affiche ce message d’aide et quitte.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).