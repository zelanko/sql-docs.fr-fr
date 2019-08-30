---
title: Référence de l’état de l’application azdata BDC
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes d’état de l’application azdata BDC.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 08/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7ebf442b3bf87960d081bfe4b0867cdd082ec22a
ms.sourcegitcommit: 5e45cc444cfa0345901ca00ab2262c71ba3fd7c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70158094"
---
# <a name="azdata-bdc-app-status"></a>État de l’application azdata BDC

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

Cet article est un article de référence pour **azdata**. 

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[affichage de l’état de l’application azdata BDC](#azdata-bdc-app-status-show) | État de App service.
## <a name="azdata-bdc-app-status-show"></a>affichage de l’état de l’application azdata BDC
État de App service.
```bash
azdata bdc app status show [--resource -r] 
                           [--all -a]
```
### <a name="examples"></a>Exemples
Obtient l’état d’App service.
```bash
azdata bdc app status show
```
Obtient l’état d’App service avec toutes les instances.
```bash
azdata bdc app status show --all
```
Obtient l’état de la ressource appproxy dans App service.
```bash
azdata bdc app status show --resource appproxy
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
