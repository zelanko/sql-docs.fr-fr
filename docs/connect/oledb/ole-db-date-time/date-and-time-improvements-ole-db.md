---
title: Améliorations des types de données de date et d’heure (OLE DB) | Microsoft Docs
description: Ces articles décrivent comment OLE DB Driver pour SQL Server prend en charge de nouveaux types de données de date et d’heure. Consultez une vue d’ensemble et des exemples.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cd0f564a68f0b296008907f8620cd870c0e5ca7d
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88862028"
---
# <a name="date-and-time-improvements-ole-db"></a>Améliorations des types de données de date et d’heure (OLE DB)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] introduit de nouveaux types de données de date et d'heure. Cette section explique comment ces nouveaux types sont exposés en tant qu'extensions dans OLE DB Driver pour SQL Server. Pour une vue d’ensemble de la prise en charge d’OLE DB Driver pour SQL Server pour les nouveaux types de données de date et d'heure, voir [Améliorations des types de données date et heure](../../oledb/features/date-and-time-improvements.md). Pour obtenir un exemple, voir [Utiliser les fonctionnalités de date et d’heure améliorées &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Pour plus d'informations sur les types de données de date et d'heure, consultez [datetime &#40;Transact-SQL&#41;](../../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge des types de données pour les améliorations de date et heure OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Fournit des informations sur les types OLE DB (OLE DB Driver pour SQL Server) qui prennent en charge les types de données de date et heure [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Métadonnées &#40;OLE DB&#41;](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)  
 Contient des informations sur la structure DBBINDING, **ICommandWithParameters::GetParameterInfo**, **ICommandWithParameters::SetParameterInfo**, **IColumnsRowset::GetColumnsRowset** et I**ColumnsInfo::GetColumnInfo**. Contient aussi des informations sur les mises à jour des ensembles de lignes de schéma OLE DB.  
  
 [Liaisons et conversions &#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
 Décrit les règles de conversion entre le serveur et le client pour les types date nouveaux et existants.  
  
 [Changements de la copie en bloc pour les types de date et d’heure améliorés (OLE DB)](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md)  
 Décrit les améliorations des types date/time pour prendre en charge les opérations de copie en bloc.  
  
 [Prise en charge des API OLE DB pour les améliorations de date et d’heure](../../oledb/ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 Décrit les API OLE DB qui prennent en charge les fonctionnalités améliorées des types date/time.  
  
 [Comparabilité pour IRowsetFind](../../oledb/ole-db-date-time/comparability-for-irowsetfind.md)  
 Décrit les types date/time et **IRowsetFind**.  
 
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
