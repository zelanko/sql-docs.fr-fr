---
title: Référence de montage azdata BDC HDFS
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de montage azdata BDC HDFS.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 07/24/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 7f0b259a3ac4ac0850fa05de3867e928b035307b
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68426269"
---
# <a name="azdata-bdc-hdfs-mount"></a>montage HDFS BDC azdata

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit des informations de référence sur les commandes de **montage HDFS BDC** dans l’outil **azdata** . Pour plus d’informations sur les autres commandes **azdata** , consultez [référence azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[création de azdata BDC HDFS Mount](#azdata-bdc-hdfs-mount-create) | Créer des montages de magasins distants dans HDFS.
[azdata BDC HDFS monter supprimer](#azdata-bdc-hdfs-mount-delete) | Supprimer des montages de magasins distants dans HDFS.
[État de montage du HDFS BDC azdata](#azdata-bdc-hdfs-mount-status) | État du ou des montages.
[actualisation du montage du HDFS BDC azdata](#azdata-bdc-hdfs-mount-refresh) | Actualiser le contenu d’un montage dans HDFS.
## <a name="azdata-bdc-hdfs-mount-create"></a>création de azdata BDC HDFS Mount
Créer des montages de magasins distants dans HDFS. Les informations d’identification permettant d’accéder au magasin distant, le cas échéant, doivent être spécifiées à l’aide de la variable d’environnement MOUNT_CREDENTIALS sous la forme d’une liste de paires clé = valeur séparées par des virgules. Toutes les virgules dans les clés ou les valeurs doivent être placées dans une séquence d’échappement.
```bash
azdata bdc hdfs mount create --remote-uri -r 
                             --mount-path -m
```
### <a name="examples"></a>Exemples
Pour monter le conteneur «Data» dans le compte ADLS Gen 2 «adlsv2example» sur HDFS Path/Mounts/adlsv2/Data à l’aide de la clé partagée
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
azdata bdc hdfs mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
Pour monter un HDFS BDC distant (hdfs://namenode1:8080/) sur le chemin d’accès HDFS local/Mounts/HDFS/
```bash
azdata bdc hdfs mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--remote-uri -r`
URI du magasin distant qui doit être monté (source de montage).
#### `--mount-path -m`
Chemin d’accès HDFS où le montage doit être créé (destination du montage).
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
## <a name="azdata-bdc-hdfs-mount-delete"></a>azdata BDC HDFS monter supprimer
Supprimer des montages de magasins distants dans HDFS.
```bash
azdata bdc hdfs mount delete --mount-path -m 
                             
```
### <a name="examples"></a>Exemples
Supprimez le montage créé sur/Mounts/adlsv2/Data pour un compte de stockage ADLS Gen 2.
```bash
azdata bdc hdfs mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--mount-path -m`
chemin d’accès HDFS correspondant au montage qui doit être supprimé.
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
## <a name="azdata-bdc-hdfs-mount-status"></a>État de montage du HDFS BDC azdata
État du ou des montages.
```bash
azdata bdc hdfs mount status [--mount-path -m] 
                             
```
### <a name="examples"></a>Exemples
Obtient l’état du montage par chemin d’accès
```bash
azdata bdc hdfs mount status --mount-path /mounts/hdfs
```
Obtient l’état de tous les montages.
```bash
azdata bdc hdfs mount status
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--mount-path -m`
Chemin de montage.
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
## <a name="azdata-bdc-hdfs-mount-refresh"></a>actualisation du montage du HDFS BDC azdata
Actualiser le contenu d’un montage dans HDFS.
```bash
azdata bdc hdfs mount refresh --mount-path -m 
                              
```
### <a name="examples"></a>Exemples
Actualiser le montage créé sur/Mounts/adlsv2/Data.
```bash
azdata bdc hdfs mount refresh --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--mount-path -m`
HDFS chemin d’accès correspondant au montage qui doit être actualisé.
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
