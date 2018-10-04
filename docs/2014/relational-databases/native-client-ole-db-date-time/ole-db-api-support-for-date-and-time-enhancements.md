---
title: Prise en charge des API OLE DB pour les améliorations de date et d’heure | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 536860699bcdbed6753724bfad7832bc9fa7705e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48144001"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Prise en charge des API OLE DB pour les améliorations de date et d’heure
  Les API OLE DB suivantes prennent en charge les fonctionnalités de date/heure améliorées.  
  
|Fonction|Description|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Un indicateur est ajouté dans la structure DBBINDING pour permettre aux applications de distinguer les valeurs `datetime`, `datetime2` et `smalldatetime`. Pour plus d’informations, consultez [Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Pour plus d’informations, consultez [modifications de copie en bloc pour les Types améliorées de Date / heure &#40;OLE DB et ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Pour plus d’informations, consultez[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Pour plus d’informations, consultez[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Pour plus d’informations, consultez[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Pour plus d’informations, consultez[Parameter and Rowset Metadata](metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Pour plus d’informations sur les ensembles de lignes de schéma affectés, consultez[Date / heure et ensembles de lignes de schéma](../native-client-ole-db-rowsets/rowsets.md).|  
|IRowsetFastLoad|Cette interface prend en charge les nouveaux types date/heure, mais aucune modification n'a été apportée à son interface.|  
|ITableDefinition::CreateTable|Pour plus d’informations, consultez [prise en charge du Type de données pour les améliorations OLE DB Date / heure](data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations des types de données de date et d’heure &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  
