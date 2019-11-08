---
title: Prise en charge sql_variant pour les types de date et d’heure | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- sql_variant data type
ms.assetid: 12ff1ea6-e2cc-40e6-910c-3126974a90b3
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f795f1848f3e4c9fe1239df79677c35c38ba3b58
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783508"
---
# <a name="sql_variant-support-for-date-and-time-types"></a>Prise en charge de sql_variant pour les types Date et Time
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Cette rubrique décrit comment le type de données **sql_variant** prend en charge les fonctionnalités de date et d’heure améliorées.  
  
 L'attribut de colonne SQL_CA_SS_VARIANT_TYPE est utilisé pour retourner le type C d'une colonne de résultat de variante. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduit un attribut supplémentaire, SQL_CA_SS_VARIANT_SQL_TYPE, qui définit le type SQL d’une colonne de résultat de variante dans le descripteur de ligne d’implémentation (IRD). SQL_CA_SS_VARIANT_SQL_TYPE peut également être utilisé dans le descripteur de paramètre d’implémentation (IPD) pour spécifier le type SQL d’un paramètre SQL_SS_TIME2 ou SQL_SS_TIMESTAMPOFFSET qui a SQL_C_BINARY type C lié avec le type SQL_SS_VARIANT.  
  
 Les nouveaux types SQL_SS_TIME2 et SQL_SS_TIMESTAMPOFFSET peuvent être définis par SQLColAttribute. SQL_CA_SS_VARIANT_SQL_TYPE peut être retourné par SQLGetDescField.  
  
 Pour les colonnes de résultats, le pilote effectue une conversion de la variante vers les types date/heure. Pour plus d’informations, consultez [conversions de SQL en C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Lors de la liaison à SQL_C_BINARY, la longueur de la mémoire tampon doit être suffisamment grande pour recevoir le struct qui correspond au type SQL.  
  
 Pour les paramètres SQL_SS_TIME2 et SQL_SS_TIMESTAMPOFFSET, le pilote convertit les valeurs C en **sql_variant** valeurs, comme décrit dans le tableau ci-dessous. Si un paramètre est lié en tant que SQL_C_BINARY et que le type de serveur est SQL_SS_VARIANT, il est traité comme une valeur binaire à moins que l'application n'ait défini SQL_CA_SS_VARIANT_SQL_TYPE sur un autre type SQL. Dans ce cas, SQL_CA_SS_VARIANT_SQL_TYPE est prioritaire ; autrement dit, si SQL_CA_SS_VARIANT_SQL_TYPE est défini, il substitue le comportement par défaut consistant à déduire le type SQL variant du type C.  
  
|Type C|Type de serveur|Commentaires|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_TINYINT|smallint|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_STINYINT|smallint|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SHORT|smallint|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SSHORT|smallint|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_USHORT|int|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_LONG|int|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SLONG|int|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_ULONG|bigint|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SBIGINT|bigint|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_FLOAT|real|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_DOUBLE|float|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_UTINYINT|tinyint|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE n'est pas défini.|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Scale est défini sur SQL_DESC_PRECISION (le paramètre *DecimalDigits* de **SQLBindParameter**).|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Scale est défini sur SQL_DESC_PRECISION (le paramètre *DecimalDigits* de **SQLBindParameter**).|  
|SQL_C_TYPE_DATE|date|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Scale est défini sur SQL_DESC_PRECISION (le paramètre *DecimalDigits* de **SQLBindParameter**).|  
|SQL_C_NUMERIC|DECIMAL|La précision est définie sur SQL_DESC_PRECISION (le paramètre *Column* de **SQLBindParameter**).<br /><br /> Mise à l’échelle définie sur SQL_DESC_SCALE (paramètre *DecimalDigits* de SQLBindParameter).|  
|SQL_C_SS_TIME2|time|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré|  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations &#40;de la date et de l’heure ODBC&#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
