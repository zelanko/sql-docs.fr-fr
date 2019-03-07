---
title: référence de configuration de cluster mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Article de référence pour les commandes de cluster mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 26e93151a1150bbbbd1798b38486ca5b01aaab1d
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527202"
---
# <a name="mssqlctl-cluster-config"></a>mssqlctl cluster config

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
| **--name -n** | Nom du cluster, utilisé pour l’espace de noms kubernetes. Obligatoire. |
| **--output-file -f** | Fichier de sortie pour stocker le résultat dans. Obligatoire. |

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).