---
title: Informations de référence sur azdata arc dc status
titleSuffix: SQL Server big data clusters
description: Article d’informations de référence sur les commandes azdata arc dc status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: seanw
ms.date: 09/22/2020
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 817571e809ab9ea4133a2f1933c3b23d99d9b1bc
ms.sourcegitcommit: 29a2be59c56f8a4b630af47760ef38d2bf56a3eb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92358787"
---
# <a name="azdata-arc-dc-status"></a>azdata arc dc status

S'applique à l'[!INCLUDE [azure-data-cli-azdata](../../includes/azure-data-cli-azdata.md)]

L’article suivant fournit des informations de référence sur les commandes **sql ** dans l’outil **azdata**. Pour plus d’informations sur les commandes **azdata**, consultez [azdata reference](reference-azdata.md)

## <a name="commands"></a>Commandes

|Commande|Description|
| --- | --- |
[azdata arc dc status show](#azdata-arc-dc-status-show) | Affiche l’état du contrôleur de données.
## <a name="azdata-arc-dc-status-show"></a>azdata arc dc status show
Affiche l’état du contrôleur de données.
```bash
azdata arc dc status show [--namespace -ns] 
                          
```
### <a name="examples"></a>Exemples
Affiche l’état du contrôleur de données dans un espace de noms particulier.
```bash
azdata arc dc status show --namespace <ns>
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--namespace -ns`
Espace de noms Kubernetes dans lequel le contrôleur de données existe.
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

