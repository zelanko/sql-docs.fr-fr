---
title: référence de cluster mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: e4e54ac3c7206ad8a6592c8cfe0b45d9ea4b8fd8
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860470"
---
# <a name="mssqlctl-cluster"></a>Cluster mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **cluster** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a id="commands"></a> Commandes

|||
|---|---|
| [create](#create) | Créer le cluster. |
| [delete](#delete) | Supprimer le cluster. |
| [config](reference-mssqlctl-cluster-config.md) | Commandes de configuration de cluster. |
| [debug](reference-mssqlctl-cluster-debug.md) | Commandes de débogage. |

## <a id="create"></a> mssqlctl cluster create

Créer le cluster.

```
mssqlctl cluster create
   --name
   --accept-eula
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--nom - n** | Nom du cluster, utilisé pour l’espace de noms kubernetes. |
| **--accept-eula -e** | Acceptez-vous les termes du contrat de licence ? \[Oui/non\].  Valeurs autorisées : non, Oui. Obligatoire. |

## <a id="delete"></a> mssqlctl cluster delete

Supprimer le cluster.

```
mssqlctl cluster delete
   --name
   [--force]
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--nom - n** | Nom du cluster, utilisé pour l’espace de noms kubernetes. Obligatoire. |
| **--force -f** | Cluster de suppression de force. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).