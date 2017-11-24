---
title: "MinDbCompatibilityLevel (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|spatial-geography
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords: MinDbCompatibilityLevel method (geometry)
ms.assetid: c848b974-8ccb-4c5c-a7eb-b019a9538d99
caps.latest.revision: "17"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: da6280eace840b92f30237bbb60873db7160cd53
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="mindbcompatibilitylevel-geometry-data-type"></a>MinDbCompatibilityLevel (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne le niveau de compatibilité minimale de la base de données qui reconnaît le **geometry** instance de type de données.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.MinDbCompatibilityLevel ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **int**  
  
 Type de retour CLR : **int**  
  
## <a name="remarks"></a>Notes  
 Utilisez `MinDbCompatibilityLevel()` pour tester la compatibilité d'un objet spatial avant de modifier le niveau de compatibilité sur une base de données.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-testing-circularstring-type-for-compatibility-with-compatibility-level-110"></a>A. Test de compatibilité de CircularString avec le niveau de compatibilité 110  
 L'exemple suivant teste la compatibilité d'une instance `CircularString` avec une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```
 DECLARE @g geometry = 'CIRCULARSTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 110 
 BEGIN 
 SELECT @g.ToString(); 
 END
 ```  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>B. Test de compatibilité de LineString avec le niveau de compatibilité 100  
 L'exemple suivant teste la compatibilité d'une instance `LineString` avec [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] :  
  
```
 DECLARE @g geometry = 'LINESTRING(3 4, 8 9, 5 6)'; 
 IF @g.MinDbCompatibilityLevel() <= 100 
 BEGIN 
 SELECT @g.ToString(); 
 END
``` 
  
## <a name="see-also"></a>Voir aussi  
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  

