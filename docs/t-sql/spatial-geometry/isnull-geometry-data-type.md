---
description: IsNull (type de données geometry)
title: IsNull (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 02e8775089f6e8112452ff2a0ff780bc9a848f31
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88497042"
---
# <a name="isnull-geometry-data-type"></a>IsNull (type de données geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Le type d’une instance **geometry** a une valeur Null. Retourne 0 si l'instance n’est pas NULL.
  
## <a name="syntax"></a>Syntaxe  
  
```  
.IsNull  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Remarques  
 `IsNull` permet de tester si une instance **geometry** a une valeur Null. `IsNull` retourne 0 si l’instance n’est pas NULL, mais NULL si l’instance est NULL.  
  
 Cette méthode est utilisée principalement par l'infrastructure SQL Server ; il n'est pas recommandé d'utiliser `IsNull` pour tester si une instance est Null.  
  

## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les instances géométriques](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

