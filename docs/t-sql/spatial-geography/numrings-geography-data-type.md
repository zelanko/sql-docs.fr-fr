---
title: NumRings (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- NumRings_TSQL
- NumRings
dev_langs:
- TSQL
helpviewer_keywords:
- NumRings method
ms.assetid: 0e4e4fa2-b608-4cc4-98ba-0845ddb4214c
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: e47aebb82c0cc3149dae7de697e92c965903a753
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101792"
---
# <a name="numrings-geography-data-type"></a>NumRings (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne le nombre total d’anneaux d’une instance **Polygon**. Dans le type [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography**, aucune distinction n’est faite entre les anneaux externes et internes, car n’importe quel anneau peut être considéré en tant qu’anneau externe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.NumRings ()  
```  
  
## <a name="return-type"></a>Type de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **int**  
  
 Type de retour CLR : **SqlInt32**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne NULL s’il ne s’agit pas d’une instance **Polygon**, et retourne 0 si l’instance est vide. Cette méthode est précise.  
  
## <a name="examples"></a>Exemples  
 Cet exemple crée une instance `Polygon` avec deux anneaux et confirme qu'elle a deux anneaux.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653), (-122.357 47.654, -122.357 47.657, -122.349 47.657, -122.349 47.650, -122.357 47.654))', 4326);  
SELECT @g.NumRings();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances geography](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
