---
title: Comparabilité pour IRowsetFind | Microsoft Docs
description: Comparabilité pour IRowsetFind
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 6750e4af88f875b7557671d628fdf2570f8dcff1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67995145"
---
# <a name="comparability-for-irowsetfind"></a>Comparabilité pour IRowsetFind
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Pour les types date/time uniquement, IRowsetFind prend en charge les comparaisons suivantes :  
  
-   LT  
  
-   LE  
  
-   EQ  
  
-   GE  
  
-   GT  
  
-   NE  
  
-   IGNORE  
  
 Si une autre comparaison est tentée, DB_E_BADCOMPAREOP est retourné. Ce comportement est conforme à la spécification OLE DB.  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations des types de données de date et d’heure &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
