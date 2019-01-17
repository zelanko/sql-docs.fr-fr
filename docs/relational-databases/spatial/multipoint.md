---
title: MultiPoint | Microsoft Docs
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- MultiPoint geometry subtype [SQL Server]
ms.assetid: 2aaab211-3aba-4dbd-90b7-095d997b1f62
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: f417e004ead7e089930a9c970a2eebf00e015ab2
ms.sourcegitcommit: 467b2c708651a3a2be2c45e36d0006a5bbe87b79
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53978849"
---
# <a name="multipoint"></a>MultiPoint
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Un **MultiPoint** est une collection de zéro ou plusieurs points. La limite d'une instance **MultiPoint** est vide.  
  
## <a name="examples"></a>Exemples  

### <a name="example-a"></a>Exemple A.
L'exemple suivant crée une instance `geometry MultiPoint` avec un SRID 23 et deux points : un point avec les coordonnées (2, 3), un point avec les coordonnées (7, 8) et une valeur Z de 9.5.  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
### <a name="example-b"></a>Exemple B. 
L’exemple suivant exprime l’instance `MultiPoint` à l’aide de `STMPointFromText()`.  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::STMPointFromText('MULTIPOINT((2 3), (7 8 9.5))', 23);  
```  
  
### <a name="example-c"></a>Exemple C.
L'exemple suivant utilise la méthode `STGeometryN()` pour extraire une description du premier point dans la collection.  
  
```sql  
SELECT @g.STGeometryN(1).STAsText();  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Point](../../relational-databases/spatial/point.md)   
 [Données spatiales &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)  
  
  
