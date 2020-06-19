---
title: Structure SSVARIANT | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b2859c9d124382892949b32cb6efb65821663c5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85048083"
---
# <a name="ssvariant-structure"></a>Structure SSVARIANT
  La structure `SSVARIANT`, qui est définie dans sqlncli.h, correspond à une valeur DBTYPE_SQLVARIANT dans le fournisseur OLE DB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 `SSVARIANT` est une union de discrimination. En fonction de la valeur du membre vt, le consommateur peut identifier le membre à lire. Les valeurs de vt correspondent aux types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par conséquent, la structure `SSVARIANT` peut contenir tout type SQL Server. Pour plus d’informations sur la structure de données pour les types OLE DB standard, consultez [Indicateurs de type](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Remarques  
 Lorsque DataTypeCompat==80, plusieurs sous-types `SSVARIANT` deviennent des chaînes. Par exemple, les valeurs vt suivantes apparaissent dans `SSVARIANT` en tant que VT_SS_WVARSTRING :  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Lorsque DateTypeCompat == 0, ces types s'affichent sous leur forme native.  
  
 Pour plus d’informations sur la SSPROP_INIT_DATATYPECOMPATIBILITY, consultez [utilisation de mots clés de chaîne de connexion avec SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Le fichier sqlncli.h contient des macros d'accès de type Variant qui simplifient l'annulation de la référence des types de membres dans la structure `SSVARIANT`. Un exemple est V_SS_DATETIMEOFFSET, que vous pouvez utiliser comme suit :  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Pour obtenir le jeu complet de macros d'accès pour chaque membre de la structure `SSVARIANT`, consultez le fichier sqlncli.hi.  
  
 Le tableau ci-dessous décrit les membres de la structure `SSVARIANT` :  
  
|Membre|Indicateur de type OLE DB|Type de données OLE DB C|Valeur vt|Commentaires|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Spécifie le type de valeur contenu dans la structure `SSVARIANT`.|  
|bTinyIntVal|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|Prend en charge le type de données `tinyint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|Prend en charge le type de données `smallint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|Prend en charge le type de données `int`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|Prend en charge le type de données `bigint`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|Prend en charge le type de données `real`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|Prend en charge le type de données `float`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|Prend en charge les `money` types de données et **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|Prend en charge le type de données `bit`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|Prend en charge le type de données `uniqueidentifier`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|Prend en charge le type de données `numeric`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|Prend en charge le type de données `date`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|Prend en charge les types de données `smalldatetime`, `datetime` et `datetime2`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|Prend en charge le type de données `time`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Inclut les membres suivants :<br /><br /> *tTime2Val* ( `DBTIME2` )<br /><br /> *bScale* ( `BYTE` ) spécifie l’échelle pour la valeur *tTime2Val* .|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|Prend en charge le type de données `datetime2`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Inclut les membres suivants :<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* ( `BYTE` ) spécifie l’échelle pour la valeur *tsDataTimeVal* .|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|Prend en charge le type de données `datetimeoffset`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Inclut les membres suivants :<br /><br /> *tsoDateTimeOffsetVal* ( `DBTIMESTAMPOFFSET` )<br /><br /> *bScale* ( `BYTE` ) spécifie l’échelle pour la valeur *tsoDateTimeOffsetVal* .|  
|NCharVal|Aucun indicateur de type OLE DB correspondant.|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|Prend en charge les `nchar` types de données et **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Inclut les membres suivants :<br /><br /> *sActualLength* ( `SHORT` ) spécifie la longueur réelle de la chaîne vers laquelle *pwchNCharVal* pointe. N'inclut pas le zéro de fin.<br /><br /> *sMaxLength* ( `SHORT` ) spécifie la longueur maximale de la chaîne à laquelle *pwchNCharVal* pointe.<br /><br /> pointeur *pwchNCharVal* ( `WCHAR` \* ) vers la chaîne.<br /><br /> Membres inutilisés : *rgbReserved*, *dwReserved* et *pwchReserved*.|  
|CharVal|Aucun indicateur de type OLE DB correspondant.|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|Prend en charge les `char` types de données et **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Inclut les membres suivants :<br /><br /> *sActualLength* ( `SHORT` ) spécifie la longueur réelle de la chaîne vers laquelle *pchCharVal* pointe. N'inclut pas le zéro de fin.<br /><br /> *sMaxLength* ( `SHORT` ) spécifie la longueur maximale de la chaîne à laquelle *pchCharVal* pointe.<br /><br /> pointeur *pchCharVal* ( `CHAR` \* ) vers la chaîne.<br /><br /> Membres non utilisés :<br /><br /> *rgbReserved*, *dwReserved* et *pwchReserved*.|  
|BinaryVal|Aucun indicateur de type OLE DB correspondant.|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|Prend en charge les `binary` types de données **varbinary** et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Inclut les membres suivants :<br /><br /> *sActualLength* ( `SHORT` ) spécifie la longueur réelle des données auxquelles *prgbBinaryVal* pointe.<br /><br /> *sMaxLength* ( `SHORT` ) spécifie la longueur maximale des données auxquelles *prgbBinaryVal* pointe.<br /><br /> pointeur *prgbBinaryVal* ( `BYTE` \* ) vers les données binaires.<br /><br /> Membre inutilisé : *dwReserved*.|  
|UnknownType|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
  
## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
