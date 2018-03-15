---
title: "MinDbCompatibilityLevel (type de données geometry) | Microsoft Docs"
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
dev_langs:
- TSQL
helpviewer_keywords:
- MinDbCompatibilityLevel method (geometry)
ms.assetid: c848b974-8ccb-4c5c-a7eb-b019a9538d99
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 368e8c16724fd11e5518db839966f4a598e51cba
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="mindbcompatibilitylevel-geometry-data-type"></a>MinDbCompatibilityLevel (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne le niveau de compatibilité minimal de la base de données pour reconnaître l’instance de type de données **geometry**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.MinDbCompatibilityLevel ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **int**  
  
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
  
## <a name="see-also"></a> Voir aussi  
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)  
  
  

