---
title: Paramètre et les métadonnées de l’ensemble de lignes | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- metadata [OLE DB]
ms.assetid: 31b318a4-20e7-4db0-b367-eb9938859029
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b8f54a8193586706d5fb80b19983d4ebf774940b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47640819"
---
# <a name="metadata---parameter-and-rowset"></a>Métadonnées - Paramètres et ensembles de lignes
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Cette rubrique fournit des informations sur le type et les membres de type suivants en rapport avec les améliorations de date et d'heure OLE DB.  
  
-   Structure DBBINDING  
  
-   **ICommandWithParameters::GetParameterInfo**  
  
-   **ICommandWithParameters::SetParameterInfo**  
  
-   **IColumnsRowset::GetColumnsRowset**  
  
-   **IColumnsInfo::GetColumnInfo**  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Les informations suivantes sont retournées dans la structure DBPARAMINFO via *prgParamInfo* :  
  
|Type de paramètre|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|Date|DBTYPE_DBDATE|6|10|0|Désactiver|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Définissez|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Désactiver|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|Désactiver|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19,21..27|0..7|Définissez|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26,28..34|0..7|Définissez|  
  
 Notez que, dans certains cas, les plages de valeurs ne sont pas continues. Cela est dû à l'ajout d'une virgule décimale lorsque la précision fractionnaire est supérieure à zéro.  
  
 DBPARAMFLAGS_SS_ISVARIABLESCALE est valide seulement en cas de connexion à un serveur [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou ultérieur). DBPARAMFLAGS_SS_ISVARIABLESCALE n’est jamais défini en cas de connexion à des serveurs de bas niveau.  
  
## <a name="icommandwithparameterssetparameterinfo-and-implied-parameter-types"></a>ICommandWithParameters::SetParameterInfo et types de paramètre implicites  
 Les informations fournies dans la structure DBPARAMBINDINFO doivent respecter les conditions suivantes :  
  
|*pwszDataSourceType*<br /><br /> (spécifique au fournisseur)|*pwszDataSourceType*<br /><br /> (OLE DB générique)|*ulParamSize*|*bScale*|  
|----------------------------------------------------|-------------------------------------------------|-------------------|--------------|  
||DBTYPE_DATE|6|Ignoré|  
|Date|DBTYPE_DBDATE|6|Ignoré|  
||DBTYPE_DBTIME|10|Ignoré|  
|time|DBTYPE_DBTIME2|10|0..7|  
|smalldatetime||16|Ignoré|  
|DATETIME||16|Ignoré|  
|datetime2 ou DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|16|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|0..7|  
  
 Le *bPrecision* paramètre est ignoré.  
  
 « DBPARAMFLAGS_SS_ISVARIABLESCALE » est ignoré lors de l'envoi de données au serveur. Les applications peuvent forcer l’utilisation de types TDS (Tabular Data Stream) hérités en utilisant les noms de types spécifiques au fournisseur « **datetime** » et « **smalldatetime** ». En cas de connexion à des serveurs [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou ultérieur), le format « **datetime2** » est utilisé et une conversion serveur implicite se produit si nécessaire, quand le nom de type est « **datetime2** » ou « DBTYPE_DBTIMESTAMP ». *bScale* est ignorée si les noms de types spécifiques du fournisseur «**datetime**« ou »**smalldatetime**» sont utilisés. Sinon, les applications doivent s’assurer que *bScale* est défini correctement. Applications mises à niveau à partir de MDAC et [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client à partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] qui utilisent « DBTYPE_DBTIMESTAMP » échouent si elles ne définissent pas *bScale* correctement. En cas de connexion à instances de serveur antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], une valeur *bScale* autre que 0 ou 3 avec « DBTYPE_DBTIMESTAMP » est une erreur, et E_FAIL est retourné.  
  
 Lorsque ICommandWithParameters::SetParameterInfo n’est pas appelée, le fournisseur implique le serveur de type à partir du type de liaison tel que spécifié dans IAccessor::CreateAccessor comme suit :  
  
|Type de liaison|*pwszDataSourceType*<br /><br /> (spécifique au fournisseur)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|Date|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 **IColumnsRowset::GetColumnsRowset** retourne les colonnes suivantes :  
  
|Type de colonne|DBCOLUMN_TYPE|DBCOLUM_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|DBCOLUMN_FLAGS, DBCOLUMNFLAGS_SS_ISVARIABLESCALE|  
|-----------------|--------------------|-------------------------|-------------------------|--------------------------------------------------|---------------------------------------------------------|  
|Date|DBTYPE_DBDATE|6|10|0|Désactiver|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Définissez|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Désactiver|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|Désactiver|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Définissez|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Définissez|  
  
 Dans DBCOLUMN_FLAGS, DBCOLUMNFLAGS_ISFIXEDLENGTH a toujours la valeur True pour les types date/heure et les indicateurs suivants sont toujours False :  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 Les indicateurs restants (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE et DBCOLUMNFLAGS_WRITEUNKNOWN) peuvent être définis, en fonction de la manière dont la colonne est définie et de la requête réelle.  
  
 Un nouvel indicateur DBCOLUMNFLAGS_SS_ISVARIABLESCALE est fourni dans DBCOLUMN_FLAGS pour permettre à une application de déterminer le type de serveur de colonnes, où DBCOLUMN_TYPE représente DBTYPE_DBTIMESTAMP. DBCOLUMN_SCALE ou DBCOLUMN_DATETIMEPRECISION doit également être utilisé pour identifier le type de serveur.  
  
 DBCOLUMNFLAGS_SS_ISVARIABLESCALE est valide seulement en cas de connexion à un serveur [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou ultérieur). DBCOLUMNFLAGS_SS_ISVARIABLESCALE est non défini en cas de connexion à des serveurs de bas niveau.  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 La structure DBCOLUMNINFO retourne les informations suivantes :  
  
|Type de paramètre|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------------------|  
|Date|DBTYPE_DBDATE|6|10|0|Désactiver|  
|time(1..7)|DBTYPE_DBTIME2|10|8, 10..16|0..7|Définissez|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Désactiver|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|Désactiver|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Définissez|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Définissez|  
  
 Dans *dwFlags*, DBCOLUMNFLAGS_ISFIXEDLENGTH a toujours la valeur True pour les types date/heure et les indicateurs suivants sont toujours False :  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER, MAYDEFER  
  
 Les indicateurs restants (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE et DBCOLUMNFLAGS_WRITEUNKNOWN) peuvent être définis.  
  
 Un nouvel indicateur, DBCOLUMNFLAGS_SS_ISVARIABLESCALE, est fourni dans *dwFlags* pour permettre à une application de déterminer le type de serveur des colonnes, où *wType* est DBTYPE_DBTIMESTAMP. *bScale* doit aussi être utilisé pour identifier le type de serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Métadonnées &#40;OLE DB&#41;](http://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
  
  
