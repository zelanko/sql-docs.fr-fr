---
title: "IsNull (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: IsNull (geography Data Type)
dev_langs: TSQL
helpviewer_keywords: IsNull method
ms.assetid: c031074f-bfda-4584-a3bf-4e7c324f237f
caps.latest.revision: "16"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3873babae0514b35626872b1b592f287a884be1c
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="isnull-geography-data-type"></a>IsNull (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Une propriété qui spécifie si le **geography** instance est null. Retourne 'TRUE' si l'instance est Null ; retourne 0 si l'instance n'est pas Null.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.IsNull  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type : **bits**  
  
 Type CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 `IsNull`peut être utilisé pour tester si un **geography** instance est null. Les résultats peuvent prêter à confusion, la méthode retournant 0 si l'instance n'est pas Null, mais Null si l'instance est Null.  
  
 Cette méthode est utilisée principalement par le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] infrastructure ; il est recommandé d’utiliser le prédicat T-SQL IS NULL pour tester si un **geography** instance est null. Pour plus d’informations sur le code T-SQL de prédicat IS NULL, consultez [IS NULL &#40; Transact-SQL &#41; ](../../t-sql/queries/is-null-transact-sql.md).  
  
## <a name="examples"></a>Exemples  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
