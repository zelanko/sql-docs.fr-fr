---
title: ConvexHullAggregate (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ConvexHullAggregate_TSQL
- ConvexHullAggregate
dev_langs:
- TSQL
helpviewer_keywords:
- ConvexHullAggregate method (geography)
ms.assetid: 21784c66-2725-471b-9e2d-a8c2e3695197
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: b973e39b4e402bbe5fb970a57478587ac240daf0
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "68066534"
---
# <a name="convexhullaggregate-geography-data-type"></a>ConvexHullAggregate (type de données geography)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Retourne une enveloppe convexe pour un ensemble donné d’objets **geography**.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
ConvexHullAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Arguments  
 *geography_operand*  
 Colonne de table de type **geography** qui représente un ensemble d’objets **geography**.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
## <a name="exception"></a>Exception  
 Lève un `FormatException` en présence de valeurs d'entrée qui ne sont pas valides. Consultez [STIsValid &#40;type de données geography&#41;](../../t-sql/spatial-geography/stisvalid-geography-data-type.md)  
  
## <a name="remarks"></a>Notes  
 La méthode retourne **null** quand l’entrée est vide ou que ses SRID sont différents. Consultez [Identificateurs de référence spatiale &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)  
  
 La méthode ignore les entrées **null**.  
  
> [!NOTE]  
>  La méthode retourne **null** si toutes les valeurs entrées sont **null**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant retourne une enveloppe convexe de l’ensemble d’objets **geography**.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT geography::ConvexHullAggregate(SpatialLocation).ToString() AS SpatialLocation  
 FROM Person.Address  
 WHERE City LIKE ('Bothell')
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geography statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
