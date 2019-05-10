---
title: référence de montage du stockage mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de montage du stockage mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 04/23/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 523253e8d1ff2d621d9f7a5ef90dbc957fba82ec
ms.sourcegitcommit: d5cd4a5271df96804e9b1a27e440fb6fbfac1220
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64774690"
---
# <a name="mssqlctl-storage-mount"></a>Montage de stockage mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **montage du stockage** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a name="commands"></a>Commandes
|     |     |
| --- | --- |
[montage du stockage mssqlctl créer](#mssqlctl-storage-mount-create) | Créer des montages de magasins distants dans HDFS.
[mssqlctl storage mount delete](#mssqlctl-storage-mount-delete) | Supprimer les montages de magasins distants dans HDFS.
[état de montage du stockage mssqlctl](#mssqlctl-storage-mount-status) | État de mount(s).
## <a name="mssqlctl-storage-mount-create"></a>montage du stockage mssqlctl créer
Créer des montages de magasins distants dans HDFS.
```bash
mssqlctl storage mount create --remote-uri 
                              --mount-path  
                              [--credential-file]
```
### <a name="examples"></a>Exemples
Pour monter le conteneur « données » dans le compte de ADLS Gen 2 « adlsv2example » sur /mounts/adlsv2/data de chemin d’accès HDFS à l’aide de la clé partagée
```bash
mssqlctl storage mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/
    --mount-path /mounts/adlsv2/data --credentials credential_file
```
Pour monter un cluster HDFS à distance (hdfs://namenode1:8080 /) on local HDFS path /mounts/hdfs /
```bash
mssqlctl storage mount create --remote-uri hdfs://namenode1:8080/ --mount-path /mounts/hdfs/
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
## <a name="mssqlctl-storage-mount-delete"></a>mssqlctl storage mount delete
Supprimer les montages de magasins distants dans HDFS.
```bash
mssqlctl storage mount delete --mount-path 
                              
```
### <a name="examples"></a>Exemples
Supprimer le montage créé au /mounts/adlsv2/data pour un compte de stockage ADLS Gen 2.
```bash
mssqlctl storage mount delete --mount-path /mounts/adlsv2/data
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
## <a name="mssqlctl-storage-mount-status"></a>état de montage du stockage mssqlctl
État de mount(s).
```bash
mssqlctl storage mount status [--mount-path] 
                              
```
### <a name="examples"></a>Exemples
Obtenir l’état de montage par chemin d’accès
```bash
mssqlctl storage mount status --mount-path /mounts/hdfs
```
Obtenir l’état de tous les montages.
```bash
mssqlctl storage mount status
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