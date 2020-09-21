---
title: IColumnsRowset (pilote OLE DB) | Microsoft Docs
description: La colonne DBCOLUMN_BASETABLEINSTANCE dans IColumnsRowset::GetColumnRowset est réservée à l’utilisation par Microsoft dans OLE DB Driver pour SQL Server.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6de3b4f286f891d611b2b9b874b9101a9490903f
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860195"
---
# <a name="icolumnsrowset"></a>IColumnsRowset
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver pour SQL Server ajoute la colonne DBCOLUMN_BASETABLEINSTANCE à IColumnsRowset::GetColumnRowset. Cette colonne retourne DBTYPE_I2 et est réservée pour une utilisation par Microsoft. Les informations de cette colonne sont fournies sous réserve de modifications dans les versions ultérieures.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md) 
  
  
