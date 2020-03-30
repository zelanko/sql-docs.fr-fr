---
title: STIsClosed (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsClosed (geography Data Type)
- STIsClosed_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STIsClosed method
ms.assetid: eba1643f-07c4-4500-8643-b7e90f908147
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: dbc1bd923b0e86acfd0fbae995bd6fdbd16816a2
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68042036"
---
# <a name="stisclosed-geography-data-type"></a>STIsClosed (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Retourne 1 si les points de début et de fin de l’instance **geography** donnée sont identiques. Retourne 1 pour les types de collection **geography** si chaque instance **geography** contenue est fermée. Retourne 0 si l'instance n'est pas fermée.  
  
 Cette méthode de type de données **geography** prend en charge les instances **FullGlobe** ou les instances spatiales qui sont plus grandes qu’un hémisphère.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIsClosed ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="remarks"></a>Notes  
 Cette méthode retourne 0 si les figures d’une instance **geography** sont des points, ou si l’instance est vide.  
  
 Cette méthode retourne true si une instance **FullGlobe** est une instance **Polygon** ou un autre type d’instance.  
  
 Toutes les instances **Polygon** sont considérées comme fermées.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `Polygon` et utilise `STIsClosed()` pour tester si le `Polygon` est fermé.  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STIsClosed();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
