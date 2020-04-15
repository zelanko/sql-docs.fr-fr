---
title: sql_variant support pour les types de dates et d’heure (fr) Microsoft Docs
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 588fcceb40ea096c549a004c1e2636d0eaf17c6c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81291665"
---
# <a name="sql_variant-support-for-date-and-time-types"></a>Prise en charge de sql_variant pour les types Date et Time
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Ce sujet décrit comment le type de données **sql_variant** prend en charge la fonctionnalité améliorée de date et d’heure.  
  
 L'attribut de colonne SQL_CA_SS_VARIANT_TYPE est utilisé pour retourner le type C d'une colonne de résultat de variante. [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] introduit un attribut supplémentaire, SQL_CA_SS_VARIANT_SQL_TYPE, qui définit le type SQL d'une colonne de résultat de variante dans le descripteur de ligne d'implémentation (IRD, Implementation Row Descriptor). SQL_CA_SS_VARIANT_SQL_TYPE peut également être utilisé dans le descripteur de paramètre d'implémentation (IPD, Implementation Parameter Descriptor) pour spécifier le type SQL d'un paramètre SQL_SS_TIME2 ou SQL_SS_TIMESTAMPOFFSET qui a le type de C SQL_C_BINARY lié au type SQL_SS_VARIANT.  
  
 Les nouveaux types SQL_SS_TIME2 et SQL_SS_TIMESTAMPOFFSET peuvent être réglés par SQLColAttribute. SQL_CA_SS_VARIANT_SQL_TYPE peut être retourné par SQLGetDescField.  
  
 Pour les colonnes de résultats, le pilote effectue une conversion de la variante vers les types date/heure. Pour plus d’informations, voir [Conversions de SQL à C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Lorsqu’elle est lier à SQL_C_BINARY, la longueur du tampon doit être suffisamment grande pour recevoir la struct qui correspond au type SQL.  
  
 Pour les paramètres SQL_SS_TIME2 et SQL_SS_TIMESTAMPOFFSET, le conducteur convertira les valeurs C en **valeurs sql_variant,** comme décrit dans le tableau ci-dessous. Si un paramètre est lié en tant que SQL_C_BINARY et que le type de serveur est SQL_SS_VARIANT, il est traité comme une valeur binaire à moins que l'application n'ait défini SQL_CA_SS_VARIANT_SQL_TYPE sur un autre type SQL. Dans ce cas, SQL_CA_SS_VARIANT_SQL_TYPE est prioritaire ; autrement dit, si SQL_CA_SS_VARIANT_SQL_TYPE est défini, il substitue le comportement par défaut consistant à déduire le type SQL variant du type C.  
  
|Type C|Type de serveur|Commentaires|  
|------------|-----------------|--------------|  
|SQL_C_CHAR|varchar|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_WCHAR|nvarcar|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_TINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_STINYINT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SSHORT|SMALLINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_USHORT|int|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_LONG|int|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SLONG|int|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_ULONG|bigint|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_SBIGINT|bigint|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_FLOAT|real|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_DOUBLE|float|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_BIT|bit|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_UTINYINT|TINYINT|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_BINARY|varbinary|SQL_CA_SS_VARIANT_SQL_TYPE n'est pas défini.|  
|SQL_C_BINARY|time|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIME2<br /><br /> Scale est fixé à SQL_DESC_PRECISION (le paramètre *DecimalDigits* de **SQLBindParameter**).|  
|SQL_C_BINARY|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE = SQL_SS_TIMESTAMPOFFSET<br /><br /> Scale est fixé à SQL_DESC_PRECISION (le paramètre *DecimalDigits* de **SQLBindParameter**).|  
|SQL_C_TYPE_DATE|Date|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_TYPE_TIME|time(0)|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré.|  
|SQL_C_TYPE_TIMESTAMP|datetime2|Scale est fixé à SQL_DESC_PRECISION (le paramètre *DecimalDigits* de **SQLBindParameter**).|  
|SQL_C_NUMERIC|Décimal|La précision est réglée pour SQL_DESC_PRECISION (le *paramètre ColumnSize* de **SQLBindParameter**).<br /><br /> Échelle réglée à SQL_DESC_SCALE (le paramètre *DecimalDigits* de SQLBindParameter).|  
|SQL_C_SS_TIME2|time|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré|  
|SQL_C_SS_TIMESTAMPOFFSET|datetimeoffset|SQL_CA_SS_VARIANT_SQL_TYPE est ignoré|  
  
## <a name="see-also"></a>Voir aussi  
 [Améliorations de la date et de l’heure &#40;&#41;ODBC](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
  
