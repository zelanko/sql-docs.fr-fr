---
title: prise en charge pour les Types de Date et heure sql_variant | Documents Microsoft
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 4738fc4bfa536d66137578b697778d62c1a8c016
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2018
ms.locfileid: "35702450"
---
# <a name="sqlvariant-support-for-date-and-time-types"></a>prise en charge pour les Types de Date et heure sql_variant
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Cette rubrique décrit comment les **sql_variant** type de données prend en charge améliorée fonctionnalités de date et heure.  
  
 L'attribut de colonne SQL_CA_SS_VARIANT_TYPE est utilisé pour retourner le type C d'une colonne de résultat de variante. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduit un attribut supplémentaire, SQL_CA_SS_VARIANT_SQL_TYPE, qui définit le type SQL d’une colonne de résultat de variante dans le descripteur de ligne d’implémentation (IRD). SQL_CA_SS_VARIANT_SQL_TYPE peut également être utilisé dans le descripteur de paramètre d’implémentation (IPD) pour spécifier le type SQL d’un SQL_SS_TIME2 ou paramètre SQL_SS_TIMESTAMPOFFSET qui a le type C SQL_C_BINARY lié au type SQL_SS_VARIANT.  
  
 Les nouveaux types SQL_SS_TIME2 et SQL_SS_TIMESTAMPOFFSET peuvent être définies à SQLColAttribute. SQL_CA_SS_VARIANT_SQL_TYPE peut être retourné par SQLGetDescField.  
  
 Pour les colonnes de résultats, le pilote effectue une conversion de la variante vers les types date/heure. Pour plus d’informations, consultez [Conversions à partir de SQL pour C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Lors de la liaison à SQL_C_BINARY, la longueur de la mémoire tampon doit être assez grande pour recevoir le struct qui correspond au type SQL.  
  
 Pour les paramètres SQL_SS_TIME2 et SQL_SS_TIMESTAMPOFFSET, le pilote convertit les valeurs C à **sql_variant** des valeurs, comme décrit dans le tableau ci-dessous. Si un paramètre est lié en tant que SQL_C_BINARY et que le type de serveur est SQL_SS_VARIANT, il est traité comme une valeur binaire à moins que l'application n'ait défini SQL_CA_SS_VARIANT_SQL_TYPE sur un autre type SQL. Dans ce cas, SQL_CA_SS_VARIANT_SQL_TYPE est prioritaire ; autrement dit, si SQL_CA_SS_VARIANT_SQL_TYPE est défini, il substitue le comportement par défaut consistant à déduire le type SQL variant du type C.  
  
|Type C|Type de serveur|Commentaires|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_TINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_STINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SSHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_USHORT|INT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_LONG|INT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SLONG|INT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_ULONG|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SBIGINT|BIGINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_FLOAT|REAL|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_DOUBLE|FLOAT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_UTINYINT|TINYINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE n'est pas défini.|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Mise à l’échelle est définie à SQL_DESC_PRECISION (le *DecimalDigits* paramètre de **SQLBindParameter**).|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Mise à l’échelle est définie à SQL_DESC_PRECISION (le *DecimalDigits* paramètre de **SQLBindParameter**).|  
|SQL_C_TYPE_DATE|Date|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Mise à l’échelle est définie à SQL_DESC_PRECISION (le *DecimalDigits* paramètre de **SQLBindParameter**).|  
|SQL_C_NUMERIC|Décimal|Précision est définie à SQL_DESC_PRECISION (le *ColumnSize* paramètre de **SQLBindParameter**).<br /><br /> Mise à l’échelle est définie à SQL_DESC_SCALE (le *DecimalDigits* paramètre de SQLBindParameter).|  
|SQL_C_SS_TIME2|time|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré|  
  
## <a name="see-also"></a>Voir aussi  
 [Date et heure améliorations &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
