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
ms.sourcegitcommit: 2533383a7baa03b62430018a006a339c0bd69af2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57018435"
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