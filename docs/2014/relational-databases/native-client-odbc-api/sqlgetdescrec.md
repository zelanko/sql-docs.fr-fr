---
title: SQLGetDescRec | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLGetDescRec function
ms.assetid: f3389ff2-f3be-4035-9fb5-c9ebc2f15025
author: rothja
ms.author: jroth
ms.openlocfilehash: 432dfc5f41d5333bf9e6cb9111464e1dcb01f579
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022305"
---
# <a name="sqlgetdescrec"></a>SQLGetDescRec
  Cette rubrique décrit les fonctionnalités de SQLGetDescRec qui sont spécifiques à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="sqlgetdescrec-and-table-valued-parameters"></a>SQLGetDescRec et paramètres table  
 SQLGetDescRec peut être utilisé pour obtenir des valeurs pour les attributs de paramètres table et les colonnes de paramètre table. Le paramètre *recnumber* de SQLGetDescRec correspond au paramètre *ParameterNumber* de SQLBindParameter.  
  
 Les colonnes de paramètre table sont disponibles uniquement lorsque le champ d'en-tête de descripteur SQL_SOPT_SS_PARAM_FOCUS est défini sur l'ordinal d'un enregistrement pour lequel SQL_DESC_TYPE a la valeur SQL_SS_TABLE. Pour plus d’informations sur les SQL_SOPT_SS_PARAM_FOCUS sur, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 SQLGetDescRec retourne les données suivantes :  
  
|Paramètre|Paramètre table|Colonnes de paramètre table et autres paramètres|  
|---------------|-----------------------------|----------------------------------------------------------|  
|*Nom*|Nom de paramètre formel pour un appel de procédure stockée ; sinon, chaîne de longueur 0.|Nom de la colonne de paramètre table.|  
|*TypePtr*|SQL_DESC_TYPE. Pour les paramètres table, il s'agit de SQL_SS_TABLE.|SQL_DESC_TYPE|  
|*SubTypePtr*|Indéfini|SQL_DESC_DATETIME_INTERVAL_CODE (pour les enregistrements de type SQL_DATETIME ou SQL_INTERVAL.)|  
|*LengthPtr*|0|SQL_DESC_OCTET_LENGTH|  
|*PrecisionPtr*|0|SQL_DESC_PRECISION|  
|*ScalePtr*|0|SQL_DESC_SCALE|  
|*NullablePtr*|1|SQL_DESC_NULLABLE|  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-enhanced-date-and-time-features"></a>Prise en charge  par SQLGetDescRec des fonctionnalités de date et heure améliorées  
 Les valeurs retournées pour les types date/heure sont les suivantes :  
  
||*TypePtr*|*SubTypePtr*|*LengthPtr*|*PrecisionPtr*|*ScalePtr*|  
|-|---------------|------------------|-----------------|--------------------|----------------|  
|DATETIME|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|Date|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-large-clr-udts"></a>Prise en charge par SQLSetDescRec des grands types CLR définis par l'utilisateur  
 `SQLGetDescRec` prend en charge les grands types CLR définis par l'utilisateur. Pour plus d’informations, consultez [types CLR volumineux définis par l’utilisateur &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLGetDescRec](https://go.microsoft.com/fwlink/?LinkId=80707)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
