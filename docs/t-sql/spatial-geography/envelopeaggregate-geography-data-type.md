---
description: EnvelopeAggregate (type de données geography)
title: EnvelopeAggregate (type de données geography) | Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EnvelopeAggregate_TSQL
- EnvelopeAggregate
dev_langs:
- TSQL
helpviewer_keywords:
- EnvelopeAggregate method (geography)
ms.assetid: 4947797f-edb8-490f-beca-37df9ec06954
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 9b14db5a616f41049b5cabc845cd822356e34522
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88467521"
---
# <a name="envelopeaggregate-geography-data-type"></a>EnvelopeAggregate (type de données geography)
[!INCLUDE [SQL Server Azure SQL Database ](../../includes/applies-to-version/sql-asdb.md)]

Retourne un objet englobant pour un ensemble donné d’objets **geography**. L’objet **geography** résultant contient plusieurs segments d’arc de cercle.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EnvelopeAggregate ( geography_operand )  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Arguments
 *geography_operand*  
 Colonne de table de type **geography** qui contient l’ensemble d’objets **geography** sur lequel effectuer une opération d’agrégation d’enveloppe.  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **geography**  
  
## <a name="remarks"></a>Remarques  
 Un objet **FullGlobe** est retourné quand l’objet englobant résultant est plus grand qu’un hémisphère. Cette méthode n'est pas précise.  
  
 La méthode retourne **null** si l’entrée a des SRID différents. Consultez [Identificateurs de référence spatiale &#40;SRID&#41;](../../relational-databases/spatial/spatial-reference-identifiers-srids.md).  
  
 La méthode ignore les entrées **null**.  
  
> [!NOTE]  
>  La méthode retourne **null** si toutes les valeurs entrées sont **null**.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant effectue un `EnvelopeAggregate` sur un ensemble de points d’emplacement **geography** dans une ville.  
  
 ```
 USE AdventureWorks2012  
 GO  
 SELECT City,  
 geography::EnvelopeAggregate(SpatialLocation) AS SpatialLocation  
 FROM Person.Address  
 WHERE PostalCode LIKE('981%')  
 GROUP BY City;
 ```  
  
## <a name="see-also"></a> Voir aussi  
 [Méthodes geography statiques étendues](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
