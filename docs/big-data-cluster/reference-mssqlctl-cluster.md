---
title: référence de cluster mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Article de référence pour les commandes de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 088168e3400feea78fb9b92fa120f1140714ab34
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018425"
---
# <a name="mssqlctl-cluster"></a>mssqlctl cluster

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
   [--accept-eula]
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--name -n** | Nom du cluster, utilisé pour l’espace de noms kubernetes. |
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
| **--name -n** | Nom du cluster, utilisé pour l’espace de noms kubernetes. Obligatoire. |
| **--force -f** | Cluster de suppression de force. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).