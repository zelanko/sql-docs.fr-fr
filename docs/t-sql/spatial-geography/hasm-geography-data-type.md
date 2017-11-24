---
title: "HasM (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 05/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- HasM_TSQL
- HasM
dev_langs: TSQL
helpviewer_keywords: HasM geography
ms.assetid: e752e97f-1619-437d-b962-48c188b4e94c
caps.latest.revision: "7"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60da3dd2be051b4ddda5b96a1adf8b9dacf2ba66
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="hasm-geography-data-type"></a>HasM (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne 1 (true) si un objet spatial contient au moins une valeur M ; sinon retourne 0 (false).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.HasM  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **bits**  
  
 Type de retour CLR : **booléenne**  
  
## <a name="remarks"></a>Notes  
  
## <a name="examples"></a>Exemples  
  
```tsql  
DECLARE @p GEOGRAPHY = 'Point(1 1 1 1)'  
SELECT @p.HasM   
--Returns: 1 (true)  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur les Instances Geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M &#40; Type de données geography &#41;](../../t-sql/spatial-geography/m-geography-data-type.md)  
  
  
