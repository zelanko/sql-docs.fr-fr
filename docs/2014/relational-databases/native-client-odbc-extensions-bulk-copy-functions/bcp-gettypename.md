---
title: bcp_gettypename | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: rothja
ms.author: jroth
ms.openlocfilehash: 0341d9ba11cd66fdbfb72a05521028098c56c400
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85019437"
---
# <a name="bcp_gettypename"></a>bcp_gettypename
  Retourne le nom de type de SQL pour un jeton de type BCP spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a>Arguments  
 *token*  
 Valeur indiquant un jeton de type BCP.  
  
 *case*  
 Indique si le jeton demandé possède le type max.  
  
## <a name="returns"></a>Retours  
 Chaîne contenant le nom de type SQL qui correspond au type BCP. Si un type BCP non valide est spécifié, une chaîne vide est retournée.  
  
## <a name="remarks"></a>Remarques  
 Les jetons de type de BCP sont définis dans le fichier d'en-tête sqlncli.h et la bibliothèque sqlncli11.lib.  
  
 Le tableau suivant spécifie les types BCP possibles, s'ils sont ou pas de type max et la sortie attendue.  
  
|Nom du type BCP|MaxType|Output|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|Vous pouvez soit utiliser|**decimal**|  
|`SQLNUMERIC`|Vous pouvez soit utiliser|**numeric**|  
|`SQLINT1`|Vous pouvez soit utiliser|**tinyint**|  
|`SQLINT2`|Vous pouvez soit utiliser|**smallint**|  
|`SQLINT4`|Vous pouvez soit utiliser|**int**|  
|`SQLMONEY`|Vous pouvez soit utiliser|**money**|  
|`SQLFLT8`|Vous pouvez soit utiliser|**float**|  
|`SQLDATETIME`|Vous pouvez soit utiliser|**datetime**|  
|`SQLBITN`|Vous pouvez soit utiliser|**bit-null**|  
|`SQLBIT`|Vous pouvez soit utiliser|**bit**|  
|`SQLBIGCHAR`|Non|**char**|  
|`SQLCHARACTER`|Non|**char**|  
|`SQLBIGVARCHAR`|Non|**varchar**|  
|`SQLVARCHAR`|Non|**varchar**|  
|`SQLTEXT`|Vous pouvez soit utiliser|**text**|  
|`SQLBIGBINARY`|Non|**binary**|  
|`SQLBINARY`|Non|**Binaire**|  
|`SQLBIGVARBINARY`|Non|**Varbinary**|  
|`SQLVARBINARY`|Non|**Varbinary**|  
|`SQLIMAGE`|Vous pouvez soit utiliser|**Image**|  
|`SQLINTN`|Vous pouvez soit utiliser|**int-null**|  
|`SQLDATETIMN`|Vous pouvez soit utiliser|**datetime-null**|  
|`SQLMONEYN`|Vous pouvez soit utiliser|**money-null**|  
|`SQLFLTN`|Vous pouvez soit utiliser|**float-null**|  
|`SQLAOPSUM`|Vous pouvez soit utiliser|**Checksum**|  
|`SQLAOPAVG`|Vous pouvez soit utiliser|**AVG**|  
|`SQLAOPCNT`|Vous pouvez soit utiliser|**Count**|  
|`SQLAOPMIN`|Vous pouvez soit utiliser|**Min**|  
|`SQLAOPMAX`|Vous pouvez soit utiliser|**Max**|  
|`SQLDATETIM4`|Vous pouvez soit utiliser|**smalldatetime**|  
|`SQLMONEY4`|Vous pouvez soit utiliser|**Smallmoney**|  
|`SQLFLT4`|Vous pouvez soit utiliser|**Non**|  
|`SQLUNIQUEID`|Vous pouvez soit utiliser|**uniqueidentifier**|  
|`SQLNCHAR`|Non|**NCHAR**|  
|`SQLNVARCHAR`|Non|**Nvarchar**|  
|`SQLNTEXT`|Vous pouvez soit utiliser|**Text**|  
|`SQLVARIANT`|Vous pouvez soit utiliser|**sql_variant**|  
|`SQLINT8`|Vous pouvez soit utiliser|**Comportant**|  
|`SQLCHARACTER`|Oui|**varchar(max)**|  
|`SQLBIGCHAR`|Oui|**varchar(max)**|  
|`SQLBIGVARCHAR`|Oui|**varchar(max)**|  
|`SQLVARCHAR`|Oui|**varchar(max)**|  
|`SQLBINARY`|Oui|**varbinary(max)**|  
|`SQLBIGBINARY`|Oui|**varbinary(max)**|  
|`SQLBIGVARBINARY`|Oui|**varbinary(max)**|  
|`SQLVARBINARY`|Oui|**varbinary(max)**|  
|`SQLNCHAR`|Oui|**nvarchar(max)**|  
|`SQLNVARCHAR`|Oui|**nvarchar(max)**|  
|`SQLXML`|Oui|**Langage**|  
|`SQLUDT`|Vous pouvez soit utiliser|**Assorti**|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a>Prise en charge des fonctionnalités de date et heure améliorées par bcp_gettypename  
 Les valeurs de paramètre de jeton pour les types date/time sont décrites dans la colonne « type dans sqlncli. h » de la table dans les [modifications de copie en bloc pour les types de date et d’heure améliorés &#40;OLE DB et ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). La valeur retournée est dans la ligne correspondante de la colonne « Type de stockage de fichier ».  
  
 Pour plus d’informations, consultez améliorations de la [date et de l’heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Bulk Copy Functions](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
