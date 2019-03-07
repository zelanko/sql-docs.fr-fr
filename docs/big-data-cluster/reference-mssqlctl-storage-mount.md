---
title: référence de montage du stockage mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Article de référence pour les commandes de stockage mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: f8336c59ffc11ff1a2b7842c393f3387298b832a
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527182"
---
# <a name="mssqlctl-storage-mount"></a>montage du stockage mssqlctl

L’article suivant fournit la référence pour le **montage du stockage** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a id="commands"></a> Commandes

|||
|---|---|
| [create](#create) | Créer des montages de magasins distants dans HDFS. |
| [delete](#delete) | Supprimer les montages de magasins distants dans HDFS. |
| [status](#status) | État de mount(s). |

## <a id="create"></a> montage du stockage mssqlctl créer

Créer des montages de magasins distants dans HDFS.

```
mssqlctl storage mount create
   --local-path
   --remote-uri
   [--credential-file]
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--local-path** | Chemin d’accès HDFS dans lequel le montage doit être créer (destination de montage). Obligatoire. |
| **--remote-uri** | URI de la banque à distance qui doit être monté (source de montage). Obligatoire. |
| **--credential-file** | Fichier qui contient les informations d’identification pour accéder au magasin distant. Les informations d’identification doivent être spécifiés en tant que clé de paires de valeur avec une clé = valeur par ligne. Tout est égale à dans les clés ou les valeurs ont être échappé. Aucune information d’identification n’est obligatoires par défaut. Les clés requises varient selon le type de magasin distant qui est monté et le type d’autorisation utilisé. |

### <a name="examples"></a>Exemples

Pour monter des « données » du conteneur dans le compte ADLS Gen 2 « adlsv2example » sur le chemin d’accès HDFS `/mounts/adlsv2/data` à l’aide de la clé partagée :

```
mssqlctl storage mount create --remote-uri abfs://data@adlsv2example.dfs.core.windows.net/ --local-path /mounts/adlsv2/data --credentials credential_file
```

Pour monter un cluster HDFS à distance (`hdfs://namenode1:8080/`) sur le chemin d’accès local de HDFS `/mounts/hdfs/`:

```
mssqlctl storage mount create --remote-uri hdfs://namenode1:8080/ --local-path /mounts/hdfs/
```

## <a id="delete"></a> mssqlctl storage mount delete

Supprimer les montages de magasins distants dans HDFS.

```
mssqlctl storage mount delete
   --local-path
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--local-path** | Le chemin d’accès HDFS correspondant pour le montage qui doit être supprimé. Obligatoire. |

### <a name="examples"></a>Exemples

Supprimer le montage créé au /mounts/adlsv2/data pour un compte de stockage ADLS Gen 2.

```
mssqlctl storage mount delete --local-path /mounts/adlsv2/data
```

## <a id="status"></a> état de montage du stockage mssqlctl

État de mount(s).

```
mssqlctl storage mount status
   --local-path
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--mount-path** | Chemin d’accès de montage. Obligatoire. |

### <a name="examples"></a>Exemples

Obtenir l’état de montage par chemin d’accès

```
mssqlctl storage mount status --mount-path /mounts/hdfs
```

Obtenir l’état de tous les montages.

```
mssqlctl storage mount status
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).