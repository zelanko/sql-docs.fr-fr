---
title: Informations de référence sur azdata bdc hdfs mount
titleSuffix: SQL Server big data clusters
description: Article de référence sur les commandes azdata bdc hdfs mount.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 11/04/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: b22e5b8427cd7f8033a630c30dabdd09420a44c3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "74820870"
---
# <a name="azdata-bdc-hdfs-mount"></a>azdata bdc hdfs mount

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]  

L’article suivant fournit des références sur les commandes `bdc hdfs mount` disponibles dans l’outil `azdata`. Pour plus d’informations sur les autres commandes `azdata`, consultez [Informations de référence sur azdata](reference-azdata.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[azdata bdc hdfs mount create](#azdata-bdc-hdfs-mount-create) | Créer des montages de magasins distants dans HDFS.
[azdata bdc hdfs mount delete](#azdata-bdc-hdfs-mount-delete) | Supprimer des montages de magasins distants dans HDFS.
[azdata bdc hdfs mount status](#azdata-bdc-hdfs-mount-status) | État du ou des montages.
[azdata bdc hdfs mount refresh](#azdata-bdc-hdfs-mount-refresh) | Actualiser le contenu d’un montage dans HDFS.
## <a name="azdata-bdc-hdfs-mount-create"></a>azdata bdc hdfs mount create
Créer des montages de magasins distants dans HDFS. Les informations d’identification permettant d’accéder au magasin distant, le cas échéant, doivent être spécifiées à l’aide de la variable d’environnement MOUNT_CREDENTIALS sous la forme d’une liste de paires clé=valeur séparées par des virgules. Toute virgule dans une clé ou une valeur doit être placée dans une séquence d’échappement.
```bash
azdata bdc hdfs mount create --remote-uri -r 
                             --mount-path -m
```
### <a name="examples"></a>Exemples
Monter le conteneur « data » dans le compte ADLS Gen 2 « adlsv2example » sur le chemin HDFS /mounts/adlsv2/data à l’aide de la clé partagée
```bash
Set the MOUNT_CREDENTIALS environment variable as "fs.azure.abfs.account.name=<your-storage-account-name>.dfs.core.windows.net,fs.azure.account.key.<your-storage-account-name>.dfs.core.windows.net=<storage-account-access-key>".
azdata bdc hdfs mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data
```
Monter un BDC HDFS distant (hdfs://namenode1:8080/) sur le chemin HDFS local /mounts/hdfs/
```bash
azdata bdc hdfs mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--remote-uri -r`
URI du magasin distant à monter (source du montage).
#### `--mount-path -m`
Chemin HDFS où le montage doit être créé (destination du montage).
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
## <a name="azdata-bdc-hdfs-mount-delete"></a>azdata bdc hdfs mount delete
Supprimer des montages de magasins distants dans HDFS.
```bash
azdata bdc hdfs mount delete --mount-path -m 
           ```
### Examples
Delete mount created at /mounts/adlsv2/data for a ADLS Gen 2 storage account.
```bash
azdata bdc hdfs mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--mount-path -m`
Chemin HDFS correspondant au montage à supprimer.
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
## <a name="azdata-bdc-hdfs-mount-status"></a>azdata bdc hdfs mount status
État du ou des montages.
```bash
azdata bdc hdfs mount status [--mount-path -m] 
           ```
### Examples
Get mount status by path
```bash
azdata bdc hdfs mount status --mount-path /mounts/hdfs
```
Obtenir l’état de tous les montages.
```bash
azdata bdc hdfs mount status
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--mount-path -m`
Chemin de montage.
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
## <a name="azdata-bdc-hdfs-mount-refresh"></a>azdata bdc hdfs mount refresh
Actualiser le contenu d’un montage dans HDFS.
```bash
azdata bdc hdfs mount refresh --mount-path -m 
            ```
### Examples
Refresh mount created at /mounts/adlsv2/data.
```bash
azdata bdc hdfs mount refresh --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--mount-path -m`
Chemin HDFS correspondant au montage à actualiser.
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
