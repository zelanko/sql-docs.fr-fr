---
title: Améliorations de la date et de l’heure (OLE DB) | Microsoft Docs
description: Améliorations des types de données de date et d’heure (OLE DB)
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
author: pmasl
ms.author: pelopes
ms.openlocfilehash: c4a93078b84cf5146f94043496bea0fdaed9fc80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015703"
---
# <a name="date-and-time-improvements-ole-db"></a>Améliorations des types de données de date et d’heure (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] introduit de nouveaux types de données de date et d'heure. Cette section décrit comment ces nouveaux types sont exposés en tant qu’extensions dans OLE DB pilote pour les SQL Server. Pour obtenir une vue d’ensemble du pilote OLE DB pour la prise en charge de SQL Server pour les nouveaux types de données de date et d’heure, consultez améliorations de la date et de l' [heure](../../oledb/features/date-and-time-improvements.md). Pour obtenir un exemple, consultez [utiliser les fonctionnalités &#40;de date et&#41;d’heure améliorées OLE DB](../../oledb/ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md).  
  
 Pour plus d’informations générales sur les types de données de date et d’heure, consultez [DateTime &#40;Transact-SQL&#41;](../../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Prise en charge des types de données pour les améliorations de date et heure OLE DB](../../oledb/ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 Fournit des informations sur les types de OLE DB (OLE DB Driver for SQL Server [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ) qui prennent en charge les types de données de date et d’heure.  
  
 [OLE DB &#40;de métadonnées&#41;](../../oledb/ole-db-date-time/metadata-parameter-and-rowset.md)  
 Contient des informations sur la structure DBBINDING, **ICommandWithParameters:: GetParameterInfo**, **ICommandWithParameters:: SetParameterInfo**, **IColumnsRowset:: GetColumnsRowset**et**ColumnsInfo:: GetColumnInfo** . Contient aussi des informations sur les mises à jour des ensembles de lignes de schéma OLE DB.  
  
 [Liaisons et conversions &#40;OLE DB&#41;](../../oledb/ole-db-date-time/conversions-ole-db.md)  
 Décrit les règles de conversion entre le serveur et le client pour les types date nouveaux et existants.  
  
 [Changements de la copie en bloc pour les types de date et d’heure améliorés (OLE DB)](../../oledb/ole-db-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db.md)  
 Décrit les améliorations des types date/time pour prendre en charge les opérations de copie en bloc.  
  
 [Prise en charge des API OLE DB pour les améliorations de date et heure](../../oledb/ole-db-date-time/ole-db-api-support-for-date-and-time-enhancements.md)  
 Décrit les API OLE DB qui prennent en charge les fonctionnalités améliorées des types date/time.  
  
 [Comparabilité pour IRowsetFind](../../oledb/ole-db-date-time/comparability-for-irowsetfind.md)  
 Décrit les types date/time et **IRowsetFind**.  
 
  
## <a name="see-also"></a>Voir aussi  
 [Programmation OLE DB Driver pour SQL Server](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
