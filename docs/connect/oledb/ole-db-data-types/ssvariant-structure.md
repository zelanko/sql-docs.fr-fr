---
title: Structure SSVARIANT (pilote OLE DB)
description: Structure SSVARIANT dans OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6cef1fb9b92df92cba00ea9e9aa8c9591e887a6
ms.sourcegitcommit: c7f40918dc3ecdb0ed2ef5c237a3996cb4cd268d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/05/2020
ms.locfileid: "91727221"
---
# <a name="ssvariant-structure"></a>Structure SSVARIANT
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  La structure **SSVARIANT**, qui est définie dans msoledbsql.h correspond à une valeur DBTYPE_SQLVARIANT dans OLE DB Driver pour SQL Server.  
  
 **SSVARIANT** est une union de discrimination. En fonction de la valeur du membre vt, le consommateur peut identifier le membre à lire. Les valeurs de vt correspondent aux types de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Ainsi, la structure **SSVARIANT** peut contenir n’importe quel type SQL Server. Pour plus d’informations sur la structure de données pour les types OLE DB standard, consultez [Indicateurs de type](/previous-versions/windows/desktop/ms711251(v=vs.85)).  
  
## <a name="remarks"></a>Notes  
 Quand DataTypeCompat==80, plusieurs sous-types **SSVARIANT** deviennent des chaînes. Par exemple, les valeurs de vt suivantes apparaissent dans **SSVARIANT** en tant que VT_SS_WVARSTRING :  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Lorsque DateTypeCompat == 0, ces types s'affichent sous leur forme native.  
  
 Pour plus d’informations sur SSPROP_INIT_DATATYPECOMPATIBILITY, consultez [Utilisation de mots clés de chaîne de connexion avec OLE DB Driver for SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 Le fichier msoledbsql.h contient des macros d’accès de type Variant qui simplifient le déréférencement des types de membres dans la structure **SSVARIANT**. Un exemple est V_SS_DATETIMEOFFSET, que vous pouvez utiliser comme suit :  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Pour obtenir le jeu complet de macros d'accès pour chaque membre de la structure **SSVARIANT**, consultez le fichier msoledbsql.  
  
 Le tableau suivant décrit les membres de la structure **SSVARIANT** :  
  
|Membre|Indicateur de type OLE DB|Type de données OLE DB C|Valeur vt|Commentaires|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Spécifie le type de valeur contenu dans la structure **SSVARIANT**.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Prend en charge le type de données **tinyint**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|Prend en charge le type de données **smallint**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Prend en charge le type de données **int**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Prend en charge le type de données **bigint**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Prend en charge le type de données **real**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Prend en charge le type de données **float**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Prend en charge les types de données **money** et **smallmoney**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Prend en charge le type de données **bit**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Prend en charge le type de données **uniqueidentifier**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Prend en charge le type de données **numeric**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Prend en charge le type de données **date**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Prend en charge les types de données **smalldatetime**, **datetime** et **datetime2**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Prend en charge le type de données **time**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Inclut les membres suivants :<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) Spécifie l’échelle pour la valeur *tTime2Val*.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Prend en charge le type de données **datetime2**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Inclut les membres suivants :<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) Spécifie l’échelle pour la valeur *tsDataTimeVal*.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Prend en charge le type de données **datetimeoffset**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Inclut les membres suivants :<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) Spécifie l’échelle pour la valeur *tsoDateTimeOffsetVal*.|  
|NCharVal|Aucun indicateur de type OLE DB correspondant.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Prend en charge les types de données **nchar** et **nvarchar**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Inclut les membres suivants :<br /><br /> *sActualLength* (**SHORT**) Spécifie la longueur réelle de la chaîne vers laquelle *pwchNCharVal* pointe. N'inclut pas le zéro de fin.<br /><br /> *sMaxLength* (**SHORT**) Spécifie la longueur maximale de la chaîne vers laquelle *pwchNCharVal* pointe.<br /><br /> *pwchNCharVal* (**WCHAR** \*) Pointeur vers la chaîne.<br /><br /> *rgbReserved* (**BYTE[5]** ) Spécifie les informations de classement.<br /><br /> Membres non utilisés : *dwReserved* et *pwchReserved*.|  
|CharVal|Aucun indicateur de type OLE DB correspondant.|**struct _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Prend en charge les types de données **char** et **varchar**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Inclut les membres suivants :<br /><br /> *sActualLength* (**SHORT**) Spécifie la longueur réelle de la chaîne vers laquelle *pchCharVal* pointe. N'inclut pas le zéro de fin.<br /><br /> *sMaxLength* (**SHORT**) Spécifie la longueur maximale de la chaîne vers laquelle *pchCharVal* pointe.<br /><br /> *pchCharVal* (**CHAR** \*) Pointeur vers la chaîne.<br /><br /> *rgbReserved* (**BYTE[5]** ) Spécifie les informations de classement.<br /><br /> Membres non utilisés :<br /><br /> *dwReserved* et *pwchReserved*.|  
|BinaryVal|Aucun indicateur de type OLE DB correspondant.|**struct _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Prend en charge les types de données **binary** et **varbinary**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].<br /><br /> Inclut les membres suivants :<br /><br /> *sActualLength* (**SHORT**) Spécifie la longueur réelle des données vers lesquelles *prgbBinaryVal* pointe.<br /><br /> *sMaxLength* (**SHORT**) Spécifie la longueur maximale des données vers lesquelles *prgbBinaryVal* pointe.<br /><br /> *prgbBinaryVal* (**BYTE** \*) Pointeur vers les données binaires.<br /><br /> Membre inutilisé : *dwReserved*.|  
|UnknownType|UNUSED|UNUSED|UNUSED|UNUSED|  
|BLOBType|UNUSED|UNUSED|UNUSED|UNUSED|  
| &nbsp; | &nbsp; | &nbsp; | &nbsp; | &nbsp; |
  
## <a name="known-issues"></a>Problèmes connus
### <a name="possible-narrow-string-data-corruption"></a>Risque d’altération des données de chaîne étroite
Avant la version 18.4 du pilote OLE DB, l’insertion dans une colonne `sql_variant` pouvait entraîner une altération des données sur le serveur si toutes les conditions suivantes étaient remplies :
- La page de codes de l’ordinateur client ne correspondait pas à la page de codes du classement de la base de données.
- La mémoire tampon du client contenait des caractères de chaîne étroite non ASCII codés dans la page de codes du client.
- L'une ou l'autre des conditions suivantes était remplie :
  - Le champ `pwszDataSourceType` dans la structure `DBPARAMBINDINFO` décrivant le paramètre correspondant à la colonne `sql_variant` était défini sur `L"DBTYPE_SQLVARIANT"`, `L"DBTYPE_VARIANT"` ou `L"sql_variant"`. Pour plus d’informations, consultez : [ICommandWithParameters::SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)).

    *or*
  - La requête SQL paramétrable utilisée pour l’insertion était préparée.

Plus précisément, le pilote OLE DB n’a pas translaté les données vers la page de codes de classement de base de données avant de les insérer. Toutefois, le pilote a mal indiqué au serveur que les données avaient été codées dans la page de codes du classement de la base de données. Ce comportement a entraîné une incohérence entre les données et la page de codes correspondante stockée dans la colonne `sql_variant`.

De même, lors de la récupération de la même valeur, le pilote OLE DB n’a pas translaté les chaînes dans la page de codes du client. Cependant, étant donné que les données insérées étaient déjà dans la page de codes du client (voir le paragraphe ci-dessus), l’application cliente a pu interpréter les données correctement. Même dans ce cas, les applications qui utilisent d’autres pilotes récupèrent ces valeurs dans un format endommagé. L’altération se produit parce que d’autres pilotes ont interprété la chaîne dans la page de codes du classement de la base de données et ont tenté de la translater en page de codes du client.

À partir de la version 18.4, OLE DB Driver translate les chaînes étroites en page de codes de classement de base de données avant l’insertion. De même, le pilote retranslate les données en page de codes client lors de la récupération. Par conséquent, les applications clientes qui reposent sur le bogue mentionné plus haut peuvent rencontrer des problèmes lors de la récupération des données insérées à l’aide d’une version antérieure de OLE DB Driver. La [procédure de récupération](#recovery-procedure) ci-dessous vise à vous aider à résoudre ces problèmes.

### <a name="recovery-procedure"></a>Procédure de récupération
> [!IMPORTANT]  
> Avant de suivre les étapes de récupération ci-dessous, assurez-vous de sauvegarder vos données existantes.

Si votre application rencontre des problèmes lors de la récupération de données à partir d’une colonne `sql_variant` après avoir basculé vers la version 18.4 de OLE DB Driver, les données endommagées doivent être modifiées pour avoir le même classement que la base de données dans laquelle les données sont stockées. Le script suivant peut être utilisé pour récupérer une valeur unique à partir d’une colonne `sql_variant`. Le script est un modèle et vous devez le modifier pour l’adapter à votre scénario.

> [!IMPORTANT]  
> Étant donné que la page de codes d’origine des données n’est pas stockée, vous devez indiquer au serveur la manière dont les données ont été initialement codées. Pour ce faire, exécutez le script dans le contexte d’une base de données qui a la même page de codes que la page de codes du client qui a initialement inséré les données. Par exemple, si les données endommagées ont été insérées à partir d’un client configuré avec la page de codes `932`, le script suivant doit être exécuté dans le contexte d’une base de données avec un classement japonais (par exemple, `Japanese_XJIS_100_CS_AI`).

```sql
/*
    Description:
        Template that can be used to recover the corrupted value inserted into the sql_variant column.

    Scenario:
        The database is named [YourDatabase] and it contains a table named [YourTable], which contains the corrupted value.
        Schema is named [dbo].
        The corrupted value is stored in a column of type sql_variant named [YourColumn].
        The corrupted value is sql_variant of BaseType char. For details on sql_variant properties, see:
            https://docs.microsoft.com/sql/t-sql/functions/sql-variant-property-transact-sql
*/

-- Base type in sql_variant can hold a maximum of 8000 bytes
-- For details see: 
--  https://docs.microsoft.com/sql/t-sql/data-types/sql-variant-transact-sql#remarks
DECLARE @bin VARBINARY(8000)

-- In the following lines we convert the sql_variant base type to binary.
-- <FilterExpression>
--      Is a placeholder and must be replaced with an expression that filters a single corrupted value to be recovered.
--      Therefore, the expression must result in a single value being returned only.
SET @bin = (SELECT CAST([YourColumn] AS VARBINARY(8000)) FROM [YourDatabase].[dbo].[YourTable] WHERE <FilterExpression>)

-- In the following lines we store the binary value in char(59) (a fixed-size character data type).
-- IMPORTANT NOTE: 
--      This example assumes the corrupted sql_variant's base type is char(59).
--      You MUST adjust the type (that is, char/varchar) and size to match your scenario exactly.
DECLARE @char CHAR(59)
SET @char = CAST((@bin) AS CHAR(59))
DECLARE @sqlvariant sql_variant

-- The following lines recover the corrupted value by translating the value to the collation of the database.
-- <DBCollation>
--      Must be replaced with the collation (for example, Latin1_General_100_CI_AS_SC_UTF8) of the database holding the data.
SET @sqlvariant = @char collate <DBCollation>

-- Finally, we update the corrupted value with the recovered value.
-- "<FilterExpression>"
--      Is a placeholder and must be replaced with an expression that filters a single corrupted value to be recovered.
--      Therefore, the expression must result in a single value being returned only.
UPDATE [YourDatabase].[dbo].[YourTable] SET [YourColumn] = @sqlvariant WHERE <FilterExpression>
```

## <a name="see-also"></a>Voir aussi  
 [Types de données &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
