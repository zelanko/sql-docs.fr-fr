---
title: Comparabilité pour IRowsetFind | Microsoft Docs
description: Découvrez les comparaisons prises en charge par IRowsetFind pour les types de date/heure dans OLE DB Driver pour la SQL Server. DB_E_BADCOMPAREOP est retourné pour d’autres comparaisons.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- IRowsetFind comparability
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 16ef589a18c2be5317157e7db5790af06c8c613a
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88861404"
---
# <a name="comparability-for-irowsetfind"></a>Comparabilité pour IRowsetFind
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

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
  
  
