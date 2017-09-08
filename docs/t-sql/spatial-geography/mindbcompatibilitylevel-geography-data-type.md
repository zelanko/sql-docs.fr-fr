---
title: "MinDbCompatibilityLevel (Type de données geography) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- MinDbCompatibilityLevel
- MinDbCompatibilityLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MinDbCompatibilityLevel method (geography)
ms.assetid: a9e44748-4a9e-4179-abc4-7631597be5a7
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 6c95aafc0278834c6108b99dd67908958fb47b17
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="mindbcompatibilitylevel-geography-data-type"></a>MinDbCompatibilityLevel (type de données geography)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  Retourne la compatibilité minimale de la base de données qui reconnaît le **geography** type de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
. MinDbCompatibilityLevel ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **int**  
  
 Type de retour CLR : **int**  
  
## <a name="remarks"></a>Notes  
 Utilisez `MinDbCompatibilityLevel()` pour tester la compatibilité d'un objet spatial avant de modifier le niveau de compatibilité sur une base de données. Non valide **geography** tapez retourne 110.  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-testing-circularstring-type-for-compatibility-with-compatibility-level-110"></a>A. Test de compatibilité de CircularString avec le niveau de compatibilité 110  
 L'exemple suivant teste la compatibilité d'une instance `CircularString` avec une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(-120.533 46.566, -118.283 46.1, -122.3 47.45)';  
IF @g.MinDbCompatibilityLevel() <= 110  
BEGIN  
    SELECT @g.ToString();  
END  
  
```  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>B. Test de compatibilité de LineString avec le niveau de compatibilité 100  
 L'exemple suivant teste la compatibilité d'une instance `LineString` avec [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] :  
  
```  
DECLARE @g geometry = 'LINESTRING(-120.533 46.566, -118.283 46.1, -122.3 47.45)';  
IF @g.MinDbCompatibilityLevel() <= 100  
BEGIN  
    SELECT @g.ToString();  
END  
  
```  
  
### <a name="c-testing-the-value-of-a-geography-instance-for-compatibility"></a>C. Test de compatibilité de la valeur d'une instance géographique  
 L'exemple suivant affiche les niveaux de compatibilité de deux instances `geography`. L'une est plus petite qu'un hémisphère et l'autre est plus grande qu'un hémisphère :  
  
```  
DECLARE @g geography = geography::Parse('POLYGON((0 -10, 120 -10, 240 -10, 0 -10))');  
DECLARE @h geography = geography::Parse('POLYGON((0 10, 120 10, 240 10, 0 10))');  
IF (@g.EnvelopeAngle() >= 90)  
BEGIN  
SELECT @g.MinDbCompatibilityLevel();  
END     
IF (@h.EnvelopeAngle() < 90)  
BEGIN  
SELECT @h.MinDbCompatibilityLevel();  
END  
  
```  
  
 La première instruction SELECT retourne 110, la deuxième retourne 100.  
  
## <a name="see-also"></a>Voir aussi  
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [Compatibilité descendante du moteur de base de données SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md)  
  
  
