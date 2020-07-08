---
title: UnionAggregate (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- UnionAggregate
- UnionAggregate_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- UnionAggregate method (geography)
ms.assetid: 1a3aeef1-5b0e-4ae8-aeb7-c4aab22f42ab
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 0e37094620354c86185244326d6dcd3c3cb35640
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85701356"
---
# <a name="unionaggregate-geography-data-type"></a>UnionAggregate (type de données geography)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Effectue une opération d'union sur un jeu d'objets de type geography.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
UnionAggregate ( geography_operand )  
```  
  
## <a name="arguments"></a>Arguments  
 *geography_operand*  
 Colonne de table de type **geography** qui contient l’ensemble d’objets **geography** sur lequel effectuer une opération d’union.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
## <a name="remarks"></a>Notes  
 La méthode retourne **null** si l’entrée a des SRID différents. Consultez [Identificateurs de référence spatiale &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 La méthode ignore les entrées **null**.  
  
> [!NOTE]  
>  La méthode retourne **null** si toutes les valeurs entrées sont **null**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant effectue un `UnionAggregate` sur un ensemble de points d’emplacement **geography** dans une ville.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT City,  
 geography::UnionAggregate(SpatialLocation) AS SpatialLocation  
 FROM Person.Address  
 WHERE PostalCode LIKE('981%')  
 GROUP BY City;
 ```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes geography statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
