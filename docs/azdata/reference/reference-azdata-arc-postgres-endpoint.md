---
title: Informations de référence sur azdata arc postgres endpoint
titleSuffix: SQL Server big data clusters
description: Article d’informations de référence sur les commandes azdata arc postgres endpoint.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 097bfb40f8636f66f142fc785c4699dce2084440
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358757"
---
# <a name="azdata-arc-postgres-endpoint"></a>azdata arc postgres endpoint

S'applique à l'[!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

L’article suivant fournit des informations de référence sur les commandes **sql ** dans l’outil **azdata**. Pour plus d’informations sur les commandes **azdata**, consultez [azdata reference](reference-azdata.md)

## <a name="commands"></a>Commandes

|Commande|Description|
| --- | --- |
[azdata arc postgres endpoint list](#azdata-arc-postgres-endpoint-list) | Répertorie les points de terminaison de groupe de serveurs PostgreSQL.
## <a name="azdata-arc-postgres-endpoint-list"></a>azdata arc postgres endpoint list
Répertorie les points de terminaison de groupe de serveurs PostgreSQL.
```bash
azdata arc postgres endpoint list --name -n 
                                  [--engine-version -ev]
```
### <a name="examples"></a>Exemples
Répertorie les points de terminaison de groupe de serveurs PostgreSQL.
```bash
azdata arc postgres endpoint list -n postgres01
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--name -n`
Nom du groupe de serveurs PostgreSQL.
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--engine-version -ev`
--engine-version peut être utilisé avec --name pour identifier un groupe de serveurs PostgreSQL hyperscale lorsque deux groupes de serveurs d’une version de moteur différente portent le même nom. --engine-version est facultatif et, lorsqu’il est utilisé pour identifier un groupe de serveurs, doit être 11 ou 12.
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

Pour plus d’informations sur les autres commandes **azdata**, consultez [azdata reference](reference-azdata.md). 

Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata](..\install\deploy-install-azdata.md).

