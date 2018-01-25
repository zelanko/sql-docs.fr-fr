---
title: "IsValidDetailed (type de données de géométrie) | Documents Microsoft"
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
helpviewer_keywords: IsValidDetailed geometry
ms.assetid: 5a31e88a-ad7b-4ef7-b773-e2571f1cb3aa
caps.latest.revision: "7"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 96f7531e9b692db3a026e4697e502f3d10e39cfa
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2018
---
# <a name="isvaliddetailed-geometry-datatype"></a>IsValidDetailed (type de données geometry)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

Retourne un message qui peut aider à identifier les problèmes concernant un objet spatial non valide. Lorsque l'objet n'est pas valide, seule la première erreur est retournée. Lorsque l'objet est valide, la valeur 24400 est retournée.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.IsValidDetailed()  
```  
  
## <a name="return-types"></a>Types de retour  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]type de retour : **nvarchar (max)**  
  
 Type de retour CLR : **chaîne**  
  
## <a name="remarks"></a>Notes  
 Le tableau suivant contient les valeurs de retour possibles :  
  
|Valeur retournée| Description|  
|------------------|-----------------|  
|24400|Valide|  
|24401|Non valide pour une raison inconnue.|  
|24402|Non valide car le point {0} est un point isolé, ce qui n'est pas valide dans ce type d'objet.|  
|24403|Non valide, car deux bords de polygone se chevauchent.|  
|24404|Non valide, car l'anneau polygonal ({0}) entre en intersection avec lui-même ou un autre anneau.|  
|24405|Non valide, car un anneau polygonal entre en intersection avec lui-même ou un autre anneau.|  
|24406|Non valide, car la courbe {0} dégénère en un point.|  
|24407|Non valide, car {0} en anneau de polygone est réduit à une ligne à {{1} du point.|  
|24408|Non valide, car l'anneau polygonal {0} n'est pas fermé.|  
|24409|Non valide, car une partie de l'anneau polygonal {0} se trouve à l'intérieur d'un polygone.|  
|24410|Non valide, car l'anneau {0} est le premier anneau d'un polygone dont il n'est pas l'anneau extérieur.|  
|24411|Non valide, car {0} anneau se trouve en dehors de la {{1} de l’anneau extérieur de son polygone.|  
|24412|Non valide, car l’intérieur d’un polygone avec {0} anneaux et {{1} n’est pas connecté.|  
|24413|Non valide, car deux bords se chevauchent dans la courbe {0}.|  
|24414|Non valide, car un bord de {0} courbe chevauche un bord de {{1} de la courbe.|  
|24415|Non valide, car un polygone a une structure d'anneau non valide.|  
|24416|Non valide, car dans {0} de la courbe du bord qui commence au point {{1} est une ligne ou un arc dégénéré avec des points de terminaison antipodes.|  
  
## <a name="examples"></a>Exemples  
 Un objet spatial non valide l’exemple suivant illustre comment la **IsValidDetailed()** se comporte des méthodes.  
  
```sql  
DECLARE @p GEOMETRY = 'Polygon((2 2, 4 4, 4 2, 2 4, 2 2))'  
SELECT @p.IsValidDetailed()  
--Returns: 24404: Not valid because polygon ring (1) intersects itself or some other ring.  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes étendues sur des instances geometry](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

