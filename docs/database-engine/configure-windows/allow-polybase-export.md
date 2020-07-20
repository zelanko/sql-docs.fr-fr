---
title: allow polybase export, option de configuration| Microsoft Docs
description: Définir l’option de configuration `allow polybase export` dans les paramètres de SQL Server
ms.custom: ''
ms.date: 07/10/2020
ms.prod: sql
ms.prod_service: ''
ms.reviewer: ''
ms.technology: polybase
ms.topic: conceptual
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c25a7e42b55561ed6337281497e847999d722292
ms.sourcegitcommit: dacd9b6f90e6772a778a3235fb69412662572d02
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2020
ms.locfileid: "86279648"
---
# <a name="set-allow-polybase-export-configuration-option"></a>Définir l’option de configuration `allow polybase export`

[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

L’option de configuration de serveur `allow polybase export` permet l’opération `INSERT` dans une table externe Hadoop. 

Cette fonctionnalité ne prend pas en charge l’insertion dans d’autres sources de données externes.

 Les valeurs possibles sont décrites dans le tableau suivant : 

| Valeur | Signification                                |
|-------|----------------------------------------|
| 0     | Désactivé. Il s'agit du paramètre par défaut. |
| 1     | activé                                |


Le paramètre prend effet immédiatement.

## <a name="example"></a>Exemple

L’exemple suivant active ce paramètre.

```sql
sp_configure 'show advanced options', 1;
GO
RECONFIGURE;
GO
sp_configure 'allow polybase export', 0;
GO
RECONFIGURE;
GO
```

## <a name="next-steps"></a>Étapes suivantes

 [Exportation de données](../../relational-databases/polybase/polybase-configure-hadoop.md#exporting-data)