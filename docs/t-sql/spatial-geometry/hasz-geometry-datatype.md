---
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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6ca656d9e1d041864c80328dcad2b9fa19de27c5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47839497"
---
# <a name="hasz-geometry-datatype"></a>HasZ (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne 1 (true) si un objet spatial contient au moins une valeur Z ; sinon retourne 0 (false).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.HasZ  
```  
  
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
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes étendues sur des instances Geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)   
 [Z &#40;type de données geometry&#41;](../../t-sql/spatial-geometry/z-geometry-data-type.md)  
  
  
