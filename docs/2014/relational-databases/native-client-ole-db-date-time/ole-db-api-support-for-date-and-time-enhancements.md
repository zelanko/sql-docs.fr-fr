---
title: Prise en charge OLE DB API pour les Date et heure améliorations | Documents Microsoft
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB, date/time improvements
ms.assetid: e65c9253-bd99-4dc3-9cb8-7613f754c966
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2bf7eee4dd2517d4ff9c9f871160ba0515b18ce8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154370"
---
# <a name="ole-db-api-support-for-date-and-time-enhancements"></a>Prise en charge OLE DB API pour les Date et heure améliorations
  Les API OLE DB suivantes prennent en charge les fonctionnalités de date/heure améliorées.  
  
|Fonction|Description|  
|--------------|-----------------|  
|IAccessor::CreateAccessor|Un indicateur est ajouté dans la structure DBBINDING pour permettre aux applications de distinguer les valeurs `datetime`, `datetime2` et `smalldatetime`. Pour plus d’informations, consultez [paramètre et Rowset Metadata](metadata-parameter-and-rowset.md).|  
|IBCPSession::BCPColFmt|Pour plus d’informations, consultez [modifications de copie en bloc pour les Types améliorées de Date et heure &#40;OLE DB et ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).|  
|ICommandWithParameters::GetParameterInfo|Pour plus d’informations, consultez[paramètre et Rowset Metadata](metadata-parameter-and-rowset.md).|  
|ICommandWithParameters::SetParameterinfo|Pour plus d’informations, consultez[paramètre et Rowset Metadata](metadata-parameter-and-rowset.md).|  
|IColumnsRowset::GetColumnsRowset|Pour plus d’informations, consultez[paramètre et Rowset Metadata](metadata-parameter-and-rowset.md).|  
|IColumnsInfo::GetColumnInfo|Pour plus d’informations, consultez[paramètre et Rowset Metadata](metadata-parameter-and-rowset.md).|  
|IDBSchemaRowset::GetRowset|Pour plus d’informations des ensembles de lignes de schéma affectés, consultez[Date et l’heure et ensembles de lignes de schéma](../native-client-ole-db-rowsets/rowsets.md).|  
|IRowsetFastLoad|Cette interface prend en charge les nouveaux types date/heure, mais aucune modification n'a été apportée à son interface.|  
|ITableDefinition::CreateTable|Pour plus d’informations, consultez [prise en charge du Type de données de Date OLE DB et les améliorations apportées au](data-type-support-for-ole-db-date-and-time-improvements.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Date et heure améliorations &#40;OLE DB&#41;](date-and-time-improvements-ole-db.md)  
  
  