---
title: Informations de référence sur azdata bdc
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc status.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 712a5ac51f13450fe5cf6b8cc13400d5666eb4a0
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155197"
---
# <a name="azdata-bdc-status"></a>azdata bdc status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Cet article est un article de référence pour **azdata**. 

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc status show](#azdata-bdc-status-show) | Affiche l’état du BDC.
## <a name="azdata-bdc-status-show"></a>azdata bdc status show
Affiche l’état du BDC.
```bash
azdata bdc status show [--resource -r] 
                       [--all -a]
```
### <a name="examples"></a>Exemples
État du cluster Big Data où l’utilisateur est connecté.
```bash
azdata bdc status show
```
État du CDM avec toutes les instances des ressources incluses.
```bash
azdata bdc status show --all
```
État BDC des services qui incluent la ressource de contrôle.
```bash
azdata bdc status show --resource control
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--resource -r`
Obtient les services associés à cette ressource.
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
Chaîne de requêtes JMESPath. Pour obtenir plus d’informations et des exemples, consultez [http://jmespath.org/](http://jmespath.org/]).
#### `--verbose`
Augmentez le niveau de détail de la journalisation. Utilisez --debug pour les journaux d’activité de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

- Pour plus d’informations sur les autres commandes **azdata**, consultez [azdata reference](reference-azdata.md). 

- Pour plus d’informations sur l’installation de l’outil **azdata**, consultez [Installer azdata pour gérer les clusters Big Data SQL Server 2019](deploy-install-azdata.md).
