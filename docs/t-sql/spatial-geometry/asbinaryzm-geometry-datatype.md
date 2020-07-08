---
title: AsBinaryZM (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- AsBinaryZM geometry
ms.assetid: 5eae2872-adca-4b8f-8b04-4ee91ced98f1
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: dc97cf967c645db6f647266190000252fd2d9022
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85700947"
---
# <a name="asbinaryzm-geometry-datatype"></a>AsBinaryZM (type de données geometry)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Retourne la représentation OGC (Open Geospatial Consortium) WKB (Well-Known Binary) d’une instance **geometry**, à laquelle s’ajoutent les valeurs **Z** (élévation) et **M** (mesure) apportées par l’instance.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.AsBinaryZM()  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **varbinary(max)**  
  
 Type de retour CLR : **SqlBytes**  
  
## <a name="remarks"></a>Notes  
  
## <a name="examples"></a>Exemples  
  
```sql  
DECLARE @g1 GEOMETRY = 'Point(1 1 2 3)';  
  
SELECT @g1.STAsBinary();  
-- Returns: 0x0101000000000000000000F03F000000000000F03F  
  
SELECT @g1.AsBinaryZM();  
--Returns: 0x01B90B0000000000000000F03F000000000000F03F00000000000000400000000000000840  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [M &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/m-geometry-data-type.md)   
 [Z &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  

