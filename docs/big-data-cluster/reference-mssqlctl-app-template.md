---
title: référence de modèle d’application mssqlctl
titleSuffix: SQL Server 2019 big data clusters
description: Article de référence pour les commandes de modèle d’application mssqlctl.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/28/2019
ms.topic: reference
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 16583ba970bfc13312864ea2e9d2571b04c20fcb
ms.sourcegitcommit: d7ed341b2c635dcdd6b0f5f4751bb919a75a6dfe
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57527222"
---
# <a name="mssqlctl-app-template"></a>mssqlctl app template

L’article suivant fournit la référence pour le **modèle d’application** commandes dans le **mssqlctl** outil. Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md).

## <a id="commands"></a> Commandes

|||
|---|---|
| [list](#list) | Extraire des modèles pris en charge. |
| [pull](#pull) | Téléchargez les modèles pris en charge. |

## <a id="list"></a> mssqlctl app template list

Extraire des modèles pris en charge.

```
mssqlctl app template list
   --url
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--url -u** | Spécifiez un emplacement de dépôt de modèle différent. Par défaut : https://github.com/Microsoft/sql-server-samples.git. |

### <a name="examples"></a>Exemples

Extraire tous les modèles sous l’emplacement de dépôt de modèle par défaut.

```
mssqlctl app template list
```

Extraire tous les modèles dans un emplacement autre dépôt.

```
mssqlctl app template list --url https://github.com/diffrent/templates.git
```

## <a id="pull"></a> mssqlctl app template pull

Téléchargez les modèles pris en charge.

```
mssqlctl app template pull
   --destination
   --name
   --url
```

### <a name="parameters"></a>Paramètres

| Paramètres | Description |
|---|---|
| **--destination -d** | Où placer le modèle d’application squelette.  Par défaut :. / modèles. |
| **--name -n** | Nom du modèle. Pour obtenir la liste complète désactiver les noms de modèle pris en charge, exécutez `mssqlctl app template list`. |
| **--url -u** | Spécifiez un emplacement de dépôt de modèle différent. Valeur par défaut :
https://github.com/Microsoft/sql-server-samples.git . |

### <a name="examples"></a>Exemples

Télécharger tous les modèles sous l’emplacement de dépôt de modèle par défaut.

```
mssqlctl app template pull
```

Télécharger tous les modèles dans un emplacement autre dépôt.

```
mssqlctl app template list --url https://github.com/diffrent/templates.git
```

Téléchargez le modèle individuel par nom.

```
mssqlctl app template pull --name ssis
```

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur les autres **mssqlctl** commandes, consultez [mssqlctl référence](reference-mssqlctl.md). Pour plus d’informations sur la façon d’installer le **mssqlctl** , consultez [installer mssqlctl pour gérer les clusters de données volumineuses de SQL Server 2019](deploy-install-mssqlctl.md).