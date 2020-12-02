---
description: HasZ (type de données geometry)
title: HasZ (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 05/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- HasZ geometry
ms.assetid: aa378943-252a-4079-848b-6c59344fcfce
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 58c43b02c466fa2f5f1bc2b06006855b894cd65c
ms.sourcegitcommit: c5078791a07330a87a92abb19b791e950672e198
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "88497064"
---
# <a name="hasz-geometry-datatype"></a>HasZ (type de données geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

  Retourne 1 (true) si un objet spatial contient au moins une valeur Z ; sinon retourne 0 (false).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.HasZ  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Types de retour
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **Boolean**  
  
## <a name="remarks"></a>Notes  
  
## <a name="examples"></a>Exemples  
  
```sql  
DECLARE @p GEOMETRY = 'Point(1 1 1 1)'  
SELECT @p.HasZ   
--Returns: 1 (true)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [Z &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  
