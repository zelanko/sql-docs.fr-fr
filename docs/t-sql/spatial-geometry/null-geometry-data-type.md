---
title: "Null (type de données geometry) | Microsoft Docs"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Null (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- Null (geometry Data Type)
ms.assetid: 67a4b019-9091-4443-85cc-f4836d0cb509
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a036b1801284fa43e4bdf7b690037711e9970638
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="null-geometry-data-type"></a>Null (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Propriété en lecture seule qui fournit une instance ayant une valeur Null du type **geometry**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Null  
```  
  
## <a name="arguments"></a>Arguments  
  
## <a name="return-types"></a>Types de retour  
 Type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geometry**  
  
 Type CLR : **SqlGeometry**  
  
## <a name="remarks"></a>Notes   
  
## <a name="examples"></a>Exemples  
 L'exemple suivant extrait une instance `geometry` Null.  
  
```  
DECLARE @g geometry;   
SET @g = geometry::[Null];  
SELECT @g  
```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes geometry statiques étendues](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

