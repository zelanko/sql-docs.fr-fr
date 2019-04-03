---
title: référence de configuration de cluster mssqlctl
titleSuffix: SQL Server big data clusters
description: Article de référence pour les commandes de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 57b77e83994f8471e677ba2ba367acc48a66cddd
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860020"
---
# <a name="mssqlctl-cluster-config"></a>Configuration de cluster mssqlctl

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

L’article suivant fournit la référence pour le **cluster config** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a id="commands"></a> Commandes

|||
|---|---|
| [get](#get) | Obtenir le cluster. |

## <a id="get"></a> mssqlctl cluster config get

Obtenir le cluster.

```
mssqlctl cluster config get
   --name
   --output-file
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--nom - n** | Nom du cluster, utilisé pour l’espace de noms kubernetes. Obligatoire. |
| **--output-file -f** | Fichier de sortie pour stocker le résultat dans. Obligatoire. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).