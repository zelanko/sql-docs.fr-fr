---
title: Informations de référence sur azdata bdc control status
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc control status
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 33a479f30617fae22ecfc46ddaf115d3a29eed6c
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70155284"
---
# <a name="azdata-bdc-control-status"></a>azdata bdc control status

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Cet article est un article de référence pour **azdata**. 

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc control status show](#azdata-bdc-control-status-show) | Contrôle de l’état du service.
## <a name="azdata-bdc-control-status-show"></a>azdata bdc control status show
Contrôle de l’état du service.
```bash
azdata bdc control status show [--resource -r] 
                               [--all -a]
```
### <a name="examples"></a>Exemples
Obtient l’état du service.
```bash
azdata bdc control status show
```
Obtient l’état du service de contrôle avec toutes les instances.
```bash
azdata bdc control status show --all
```
Obtient l’état de la ressource de contrôle dans le service de contrôle.
```bash
azdata bdc control status show --resource control
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--resource -r`
Obtient cette ressource dans ce service.
#### `--all -a`
Affichez toutes les instances de chaque ressource au sein du service.
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
