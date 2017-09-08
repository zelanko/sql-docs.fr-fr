---
title: "MinDbCompatibilityLevel (Type de données geometry) | Documents Microsoft"
ms.custom: 
ms.date: 08/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- MinDbCompatibilityLevel method (geometry)
ms.assetid: c848b974-8ccb-4c5c-a7eb-b019a9538d99
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 51bde32ba27af0ed46bb176ede7bb4a61ef15292
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="mindbcompatibilitylevel-geometry-data-type"></a>MinDbCompatibilityLevel (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

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
  
 `DECLARE @g geometry = 'CIRCULARSTRING(3 4, 8 9, 5 6)';`  
  
 `IF @g.MinDbCompatibilityLevel() <= 110`  
  
 `BEGIN`  
  
 `SELECT @g.ToString();`  
  
 `END`  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>B. Test de compatibilité de LineString avec le niveau de compatibilité 100  
 L'exemple suivant teste la compatibilité d'une instance `LineString` avec [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] :  
  
 `DECLARE @g geometry = 'LINESTRING(3 4, 8 9, 5 6)';`  
  
 `IF @g.MinDbCompatibilityLevel() <= 100`  
  
 `BEGIN`  
  
 `SELECT @g.ToString();`  
  
 `END`  
  
## <a name="see-also"></a>Voir aussi  
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  


