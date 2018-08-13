---
title: Attributs d’instruction qui affectent les paramètres table | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor header field
- table-valued parameters (ODBC), statement attribute
ms.assetid: 089213b0-d368-4332-b2e5-b2bd8770c64f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 932528d7625cacc3b6c573964d537224ef306453
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2018
ms.locfileid: "39563033"
---
# <a name="statement-attributes-that-affect-table-valued-parameters"></a>Attributs d'instruction qui affectent des paramètres table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Le tableau suivant décrit les attributs dans un champ de descripteur.  
  
|Nom de l'attribut|Type|Description|  
|--------------------|----------|-----------------|  
|SQL_SOPT_SS_PARAM_FOCUS|SQLUINTEGER|Pour plus d’informations sur SQL_SS_PARAM_FOCUS, consultez [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).|  
|SQL_SOPT_SS_NAME_SCOPE|SQLUINTEGER|Pour plus d’informations sur SQL_SS_NAME_SCOPE, consultez [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).|  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
