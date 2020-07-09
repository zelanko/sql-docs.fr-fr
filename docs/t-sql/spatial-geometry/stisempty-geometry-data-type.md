---
title: STIsEmpty (type de données geometry) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsEmpty_TSQL
- STIsEmpty (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsEmpty (geometry Data Type)
ms.assetid: dcbd6ae1-5d63-485f-9d58-28bfd504524e
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 44b62d04c52ddb707bfd094d3b29fbfe84cf5bb4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85762396"
---
# <a name="stisempty-geometry-data-type"></a>STIsEmpty (type de données geometry)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

Retourne 1 si une instance **geometry** est vide. Retourne 0 si une instance **geometry** n’est pas vide.
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STIsEmpty ( )  
```  
  
## <a name="return-types"></a>Types de retour  
 Type de retour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] : **bit**  
  
 Type de retour CLR : **SqlBoolean**  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant crée une instance `geometry` vide et utilise `STIsEmpty()` pour tester si l'instance est vide.  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON EMPTY', 0);  
SELECT @g.STIsEmpty();  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes OGC sur des instances geography](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

