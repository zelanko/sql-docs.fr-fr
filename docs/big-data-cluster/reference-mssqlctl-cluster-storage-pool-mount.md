---
title: référence de montage de pool de stockage de cluster mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de montage de pool de stockage de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: jroth
ms.date: 05/22/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: eb527779cd844064bcabccc91f5356676e06f004
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779305"
---
# <a name="mssqlctl-cluster-storage-pool-mount"></a>Montage de pool de stockage de cluster mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **montage du pool de stockage de clusters** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[montage du pool de stockage de clusters mssqlctl créer](#mssqlctl-cluster-storage-pool-mount-create) | Créer des montages de magasins distants dans HDFS.
[mssqlctl cluster storage-pool mount delete](#mssqlctl-cluster-storage-pool-mount-delete) | Supprimer les montages de magasins distants dans HDFS.
[état de montage du pool de stockage de cluster mssqlctl](#mssqlctl-cluster-storage-pool-mount-status) | État de mount(s).
## <a name="mssqlctl-cluster-storage-pool-mount-create"></a>montage du pool de stockage de clusters mssqlctl créer
Créer des montages de magasins distants dans HDFS.
```bash
mssqlctl cluster storage-pool mount create --remote-uri 
                                           --mount-path  
                                           [--credential-file]
```
### <a name="examples"></a>Exemples
Pour monter le conteneur « données » dans le compte de ADLS Gen 2 « adlsv2example » sur /mounts/adlsv2/data de chemin d’accès HDFS à l’aide de la clé partagée
```bash
mssqlctl cluster storage-pool mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data --credentials credential_file
```
Pour monter un cluster HDFS à distance (hdfs://namenode1:8080 /) on local HDFS path /mounts/hdfs /
```bash
mssqlctl cluster storage-pool mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--remote-uri`
URI de la banque à distance qui doit être monté (source de montage).
#### `--mount-path`
Chemin d’accès HDFS dans lequel le montage doit être créé (destination de montage).
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--credential-file`
Fichier qui contient les informations d’identification pour accéder au magasin distant. Les informations d’identification doivent être spécifiés en tant que clé de paires de valeur avec une clé = valeur par ligne. Tout est égale à dans les clés ou les valeurs ont être échappé. Aucune information d’identification n’est obligatoires par défaut. Les clés requises varient selon le type de magasin distant qui est monté et le type d’autorisation utilisé.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.
## <a name="mssqlctl-cluster-storage-pool-mount-delete"></a>mssqlctl cluster storage-pool mount delete
Supprimer les montages de magasins distants dans HDFS.
```bash
mssqlctl cluster storage-pool mount delete --mount-path 
                                           
```
### <a name="examples"></a>Exemples
Supprimer le montage créé au /mounts/adlsv2/data pour un compte de stockage ADLS Gen 2.
```bash
mssqlctl cluster storage-pool mount delete --mount-path /mounts/adlsv2/data
```
### <a name="required-parameters"></a>Paramètres obligatoires
#### `--mount-path`
Le chemin d’accès HDFS correspondant pour le montage qui doit être supprimé.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.
## <a name="mssqlctl-cluster-storage-pool-mount-status"></a>état de montage du pool de stockage de cluster mssqlctl
État de mount(s).
```bash
mssqlctl cluster storage-pool mount status [--mount-path] 
                                           
```
### <a name="examples"></a>Exemples
Obtenir l’état de montage par chemin d’accès
```bash
mssqlctl cluster storage-pool mount status --mount-path /mounts/hdfs
```
Obtenir l’état de tous les montages.
```bash
mssqlctl cluster storage-pool mount status
```
### <a name="optional-parameters"></a>Paramètres facultatifs
#### `--mount-path`
Chemin d’accès de montage.
### <a name="global-arguments"></a>Arguments globaux
#### `--debug`
Augmente le détail de journalisation pour afficher que tous les journaux de débogage.
#### `--help -h`
Afficher ce message d’aide et de sortie.
#### `--output -o`
Format de sortie.  Valeurs autorisées : json, jsonc, table, tsv.  Par défaut : json.
#### `--query -q`
Chaîne de requête JMESPath. Consultez [ http://jmespath.org/ ](http://jmespath.org/]) pour plus d’informations et des exemples.
#### `--verbose`
Augmente le détail de journalisation. Utilisez--debug pour les journaux de débogage complets.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).