---
title: Comparabilité pour IRowsetFind | Documents Microsoft
description: Comparabilité pour IRowsetFind
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-date-time
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 499f88680a44e16180f08fa87955612bee06896a
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2018
ms.locfileid: "35665479"
---
# <a name="comparability-for-irowsetfind"></a>Comparabilité pour IRowsetFind
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

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
 [Date et heure améliorations &#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  
