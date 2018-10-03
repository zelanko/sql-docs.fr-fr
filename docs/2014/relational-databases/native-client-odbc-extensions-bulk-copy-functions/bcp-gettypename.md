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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5bc7caa063d14967e576fd009a23110b9647836b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086809"
---
# <a name="bcpgettypename"></a>bcp_gettypename
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
 *Jeton*  
 Valeur indiquant un jeton de type BCP.  
  
 *field*  
 Indique si le jeton demandé possède le type max.  
  
## <a name="returns"></a>Valeur renvoyée  
 Chaîne contenant le nom de type SQL qui correspond au type BCP. Si un type BCP non valide est spécifié, une chaîne vide est retournée.  
  
## <a name="remarks"></a>Notes  
 Les jetons de type de BCP sont définis dans le fichier d'en-tête sqlncli.h et la bibliothèque sqlncli11.lib.  
  
 Le tableau suivant spécifie les types BCP possibles, s'ils sont ou pas de type max et la sortie attendue.  
  
|Nom du type BCP|MaxType|Sortie|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|Avant ou après|**decimal**|  
|`SQLNUMERIC`|Avant ou après|**numeric**|  
|`SQLINT1`|Avant ou après|**tinyint**|  
|`SQLINT2`|Avant ou après|**smallint**|  
|`SQLINT4`|Avant ou après|**Int**|  
|`SQLMONEY`|Avant ou après|**money**|  
|`SQLFLT8`|Avant ou après|**float**|  
|`SQLDATETIME`|Avant ou après|**datetime**|  
|`SQLBITN`|Avant ou après|**bit-null**|  
|`SQLBIT`|Avant ou après|**bit**|  
|`SQLBIGCHAR`|non|**char**|  
|`SQLCHARACTER`|non|**char**|  
|`SQLBIGVARCHAR`|non|**varchar**|  
|`SQLVARCHAR`|non|**varchar**|  
|`SQLTEXT`|Avant ou après|**texte**|  
|`SQLBIGBINARY`|non|**binaire**|  
|`SQLBINARY`|non|**Binaire**|  
|`SQLBIGVARBINARY`|non|**varbinary**|  
|`SQLVARBINARY`|non|**varbinary**|  
|`SQLIMAGE`|Avant ou après|**Image**|  
|`SQLINTN`|Avant ou après|**int null**|  
|`SQLDATETIMN`|Avant ou après|**datetime-null**|  
|`SQLMONEYN`|Avant ou après|**valeur null de l’argent**|  
|`SQLFLTN`|Avant ou après|**float-null**|  
|`SQLAOPSUM`|Avant ou après|**Sum**|  
|`SQLAOPAVG`|Avant ou après|**Avg**|  
|`SQLAOPCNT`|Avant ou après|**Count**|  
|`SQLAOPMIN`|Avant ou après|**Min**|  
|`SQLAOPMAX`|Avant ou après|**Max**|  
|`SQLDATETIM4`|Avant ou après|**smalldatetime**|  
|`SQLMONEY4`|Avant ou après|**smallmoney**|  
|`SQLFLT4`|Avant ou après|**réel**|  
|`SQLUNIQUEID`|Avant ou après|**uniqueidentifier**|  
|`SQLNCHAR`|non|**NCHAR**|  
|`SQLNVARCHAR`|non|**Nvarchar**|  
|`SQLNTEXT`|Avant ou après|**ntext**|  
|`SQLVARIANT`|Avant ou après|**sql_variant**|  
|`SQLINT8`|Avant ou après|**Bigint**|  
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
|`SQLXML`|Oui|**Xml**|  
|`SQLUDT`|Avant ou après|**UDT**|  
  
## <a name="bcpgettypename-support-for-enhanced-date-and-time-features"></a>Prise en charge des fonctionnalités de date et heure améliorées par bcp_gettypename  
 Les valeurs de paramètre de jeton pour les types date/heure sont décrites dans la colonne « Type dans sqlncli.h » de la table dans [modifications de copie en bloc pour les Types améliorées de Date / heure &#40;OLE DB et ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md). La valeur retournée est dans la ligne correspondante de la colonne « Type de stockage de fichier ».  
  
 Pour plus d’informations, consultez [améliorations Date / heure &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctions de copie en bloc](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
