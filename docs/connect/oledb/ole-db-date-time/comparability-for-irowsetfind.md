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
manager: craigg
ms.openlocfilehash: 33ddde806c456b59391e06b75d5ab11446b038f7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731837"
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
  
## <a name="see-also"></a> Voir aussi  
 [Améliorations des types de données de date et d’heure &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
