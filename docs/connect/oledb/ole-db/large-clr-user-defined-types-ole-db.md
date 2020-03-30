---
title: Types CLR volumineux définis par l'utilisateur (OLE DB) | Microsoft Docs
description: Types CLR volumineux définis par l'utilisateur (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- large CLR user-defined types [OLE DB]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 228054b56d6b26bf4439c01363d6cad24422f938
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "68015224"
---
# <a name="large-clr-user-defined-types-ole-db"></a>Types CLR volumineux définis par l'utilisateur (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Cette rubrique traite des modifications apportées au pilote OLE DB pour SQL Server pour prendre en charge les types volumineux définis par l’utilisateur du CLR (Common Language Runtime).  
  
 Pour plus d’informations sur la prise en charge d’un grand nombre d’UDT CLR dans OLE DB Driver pour SQL Server, consultez [Types CLR volumineux définis par l’utilisateur](../../oledb/features/large-clr-user-defined-types.md). Pour un exemple, consultez [Utiliser des types CLR volumineux &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-large-clr-udts-ole-db.md).  
  
## <a name="data-format"></a>Format de données  
 Le pilote OLE DB pour SQL Server utilise ~0 pour représenter la longueur des valeurs qui sont de taille illimitée pour les types volumineux. ~0 représente également la taille des types UDT du CLR supérieurs à 8 000 octets.  
  
 Le tableau suivant montre le mappage des types de données dans les paramètres et les ensembles de lignes :  
  
|Type de données SQL Server|Type de données OLE DB|Disposition en mémoire|Valeur|  
|--------------------------|----------------------|-------------------|-----------|  
|UDT CLR|DBTYPE_UDT|BYTE[](tableau d’octets\)|132 (oledb.h)|  
  
 Les valeurs UDT sont représentées sous la forme de tableaux d'octets. Les conversions en chaînes hexadécimales de même que les conversions depuis des chaînes hexadécimales sont prises en charge. Les valeurs littérales sont représentées sous forme de chaînes hexadécimales avec le préfixe « 0x ». Une chaîne hexadécimale est la représentation textuelle de données binaires en base 16. Un exemple est une conversion du type serveur **varbinary(10)** en DBTYPE_STR, ce qui se traduit par une représentation hexadécimale de 20 caractères, où chaque paire de caractères représente un seul octet.  
  
## <a name="parameter-properties"></a>Propriétés de paramètre  
 Le jeu de propriétés DBPROPSET_SQLSERVERPARAMETER prend en charge les types UDT via OLE DB. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../../oledb/features/using-user-defined-types.md).  
  
## <a name="column-properties"></a>Propriétés de colonne  
 Le jeu de propriétés DBPROPSET_SQLSERVERCOLUMN prend en charge la création de tables via OLE DB. Pour plus d’informations, consultez [Types CLR définis par l’utilisateur](../../oledb/features/using-user-defined-types.md).  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a>Mappage des types de données dans ITableDefinition::CreateTable  
 Les informations suivantes sont utilisées dans les structures **DBCOLUMNDESC** utilisées par ITableDefinition::CreateTable quand des colonnes UDT sont nécessaires :  
  
|Type de données OLE DB (*wType*)|*pwszTypeName*|Type de données SQL Server|*rgPropertySets*|  
|----------------------------------|--------------------|--------------------------|----------------------|  
|DBTYPE_UDT|Ignoré|UDT|Doit inclure un jeu de propriétés DBPROPSET_SQLSERVERCOLUMN.|  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Les informations retournées dans la structure DBPARAMINFO via **prgParamInfo** sont les suivantes :  
  
|Type de paramètre|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|-------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (longueur inférieure ou égale à 8 000 octets)|"DBTYPE_UDT"|*n*|non défini|non défini|clear|  
|DBTYPE_UDT<br /><br /> (longueur supérieure à 8 000 octets)|"DBTYPE_UDT"|~0|non défini|non défini|set|  
  
## <a name="icommandwithparameterssetparameterinfo"></a>ICommandWithParameters::SetParameterInfo  
 Les informations fournies dans la structure DBPARAMBINDINFO doivent respecter les conditions suivantes :  
  
|Type de paramètre|*pwszDataSourceType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags* DBPARAMFLAGS_ISLONG|  
|--------------------|--------------------------|-------------------|------------------|--------------|------------------------------------|  
|DBTYPE_UDT<br /><br /> (longueur inférieure ou égale à 8 000 octets)|DBTYPE_UDT|*n*|ignoré|ignoré|Doit être défini si le paramètre doit être passé à l'aide de DBTYPE_IUNKNOWN.|  
|DBTYPE_UDT<br /><br /> (longueur supérieure à 8 000 octets)|DBTYPE_UDT|~0|ignoré|ignoré|ignoré|  
  
## <a name="isscommandwithparameters"></a>ISSCommandWithParameters  
 Les applications utilisent **ISSCommandWithParameters** pour obtenir et définir les propriétés de paramètre définies dans la section Propriétés du paramètre.  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Les colonnes retournées sont les suivantes :  
  
|Type de colonne|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE|DBCOLUMN_FLAGS_ISLONG|DBCOLUMNS_ISSEARCHABLE|DBCOLUMN_OCTETLENGTH|  
|-----------------|--------------------|--------------------------|-------------------------|---------------------|-----------------------------|-----------------------------|---------------------------|  
|DBTYPE_UDT<br /><br /> (longueur inférieure ou égale à 8 000 octets)|DBTYPE_UDT|*n*|NULL|NULL|Désactiver|DB_ALL_EXCEPT_LIKE|n|  
|DBTYPE_UDT<br /><br /> (longueur supérieure à 8 000 octets)|DBTYPE_UDT|~0|NULL|NULL|Définissez|DB_ALL_EXCEPT_LIKE|0|  
  
 Les colonnes suivantes sont également définies pour les types UDT :  
  
|Identificateur de colonne|Type|Description|  
|-----------------------|----------|-----------------|  
|DBCOLUMN_UDT_CATALOGNAME|DBTYPE_WSTR|Pour les colonnes UDT, il s'agit du nom du catalogue où le type UDT est défini.|  
|DBCOLUMN_UDT_SCHEMANAME|DBTYPE_WSTR|Pour les colonnes UDT, il s'agit du nom du schéma où le type UDT est défini.|  
|DBCOLUMN_UDT_NAME|DBTYPE_WSTR|Pour les colonnes UDT, il s'agit du nom en une partie du type UDT.|  
|DBCOLUMN_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Pour les colonnes UDT, il s’agit du nom de type complet du type UDT. Le nom complet du type d'assembly vous permet d'instancier un objet de ce type à l'aide de la méthode Type.GetType.|  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 Les informations retournées dans la structure DBCOLUMNINFO sont les suivantes :  
  
|Type de paramètre|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBCOLUMNFLAGS_ISLONG|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------|  
|DBTYPE_UDT<br /><br /> (longueur inférieure ou égale à 8 000 octets)|DBTYPE_UDT|*n*|~0|~0|Désactiver|  
|DBTYPE_UDT<br /><br /> (longueur supérieure à 8 000 octets)|DBTYPE_UDT|~0|~0|~0|Définissez|  
  
## <a name="columns-rowset-schema-rowsets"></a>Ensemble de lignes COLUMNS (ensembles de lignes de schéma)  
 Les valeurs de colonnes suivantes sont retournées pour les types UDT :  
  
|Type de colonne|DATA_TYPE|COLUMN_FLAGS, DBCOLUMFLAGS_ISLONG|CHARACTER_OCTET_LENGTH|  
|-----------------|----------------|-----------------------------------------|------------------------------|  
|DBTYPE_UDT<br /><br /> (longueur inférieure ou égale à 8 000 octets)|DBTYPE_UDT|Désactiver|*n*|  
|DBTYPE_UDT<br /><br /> (longueur supérieure à 8 000 octets)|DBTYPE_UDT|Définissez|0|  
  
 Les colonnes supplémentaires suivantes sont définies pour les types UDT :  
  
|Identificateur de colonne|Type|Description|  
|-----------------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Pour les colonnes UDT, il s'agit du nom du catalogue où le type UDT est défini.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Pour les colonnes UDT, il s'agit du nom du schéma où le type UDT est défini.|  
|SS_UDT_NAME|DBTYPE_WSTR|Pour les colonnes UDT, il s'agit du nom en une partie du type UDT.|  
|SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Pour les colonnes UDT, il s'agit du nom de type complet du type UDT. Le nom complet du type d'assembly vous permet d'instancier un objet de ce type à l'aide de la méthode Type.GetType.|  
  
 En ce qui concerne l'ensemble de lignes PROCEDURE_PARAMETERS, DATA_TYPE contient les mêmes valeurs que l'ensemble de lignes de schéma COLUMNS et TYPE_NAME contient UDT. Les mêmes colonnes supplémentaires sont également définies.  
  
 Les types définis par l'utilisateur n'apparaîtront pas dans l'ensemble de lignes de schéma PROVIDER_TYPES.  
  
## <a name="bindings-and-conversions"></a>Liaisons et conversions  
  
|Type de données de liaison|UDT vers serveur|Non-UDT vers serveur|UDT à partir du serveur|Non-UDT à partir du serveur|  
|----------------------|-------------------|------------------------|---------------------|--------------------------|  
|DBTYPE_UDT|Pris en charge (5)|Erreur (1)|Pris en charge (5)|Erreur (4)|  
|DBTYPE_BYTES|Pris en charge (5)|N/A|Pris en charge (5)|N/A|  
|DBTYPE_WSTR|Pris en charge (2), (5)|N/A|Pris en charge (3), (5), (6)|N/A|  
|DBTYPE_BSTR|Pris en charge (2), (5)|N/A|Pris en charge (3), (5)|N/A|  
|DBTYPE_STR|Pris en charge (2), (5)|N/A|Pris en charge (3), (5)|N/A|  
|DBTYPE_IUNKNOWN|Pris en charge (6)|N/A|Pris en charge (6)|N/A|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Pris en charge (5)|N/A|Pris en charge (3), (5)|N/A|  
|DBTYPE_VARIANT (VT_BSTR)|Pris en charge (2), (5)|N/A|N/A|N/A|  
  
### <a name="key-to-symbols"></a>Liste des symboles  
  
|Symbole|Signification|  
|------------|-------------|  
|1|Si un type serveur autre que DBTYPE_UDT est spécifié avec **ICommandWithParameters::SetParameterInfo** et que le type d’accesseur est DBTYPE_UDT, une erreur se produit quand l’instruction est exécutée.  L'erreur sera DB_E_ERRORSOCCURRED et l'état du paramètre sera DBSTATUS_E_BADACCESSOR.<br /><br /> Le fait de spécifier un paramètre de type UDT pour un paramètre serveur qui n'est pas un type UDT constitue une erreur.|  
|2|Les données sont converties d'une chaîne hexadécimale en données binaires.|  
|3|Les données sont converties données binaires en chaîne hexadécimale.|  
|4|La validation peut se produire lors de l’utilisation de **CreateAccessor** ou de **GetNextRows**. L'erreur est DB_E_ERRORSOCCURRED. L'état de liaison a la valeur DBBINDSTATUS_UNSUPPORTEDCONVERSION.|  
|5|BY_REF peut être utilisé.|  
|6|Les paramètres UDT peuvent être liés en tant que DBTYPE_IUNKNOWN dans le DBBINDING. La liaison à DBTYPE_IUNKNOWN indique que l’application veut traiter les données en tant que flux avec l’interface ISequentialStream. Lorsqu'un consommateur spécifie *wType* dans une liaison en tant que type DBTYPE_IUNKNOWN, et que la colonne ou le paramètre de sortie correspondant de la procédure stockée est un type UDT, OLE DB Driver pour SQL Server retournera ISequentialStream. Pour un paramètre d’entrée, OLE DB Driver pour SQL Server interroge l’interface ISequentialStream.<br /><br /> Vous pouvez choisir de ne pas lier la longueur de données UDT à l'aide de la liaison DBTYPE_IUNKNOWN en cas types UDT volumineux. Toutefois, la longueur doit être liée pour de petits types UDT. Un paramètre DBTYPE_UDT peut être spécifié en tant que type UDT volumineux si une ou plusieurs des conditions suivantes sont réunies :<br />*ulParamParamSize* vaut ~0.<br />DBPARAMFLAGS_ISLONG est défini dans le struct DBPARAMBINDINFO.<br /><br /> Pour les données de ligne, la liaison DBTYPE_IUNKNOWN est uniquement autorisée pour les types UDT volumineux. Vous pouvez déterminer si une colonne est un type UDT volumineux à l’aide de la méthode IColumnsInfo::GetColumnInfo sur l’interface IColumnsInfo d’un ensemble de lignes ou d’un objet de commande. Une colonne DBTYPE_UDT est une colonne UDT volumineuse si une ou plusieurs des conditions suivantes sont réunies :<br />L’indicateur DBCOLUMNFLAGS_ISLONG est défini sur le membre *dwFlags* de la structure DBCOLUMNINFO. <br />Le membre *ulColumnSize* de DBCOLUMNINFO vaut ~0.|  
  
 DBTYPE_NULL et DBTYPE_EMPTY peuvent être liés pour des paramètres d'entrée, mais pas pour des résultats ou des paramètres de sortie. S'ils sont liés pour des paramètres d'entrée, l'état doit avoir la valeur DBSTATUS_S_ISNULL pour DBTYPE_NULL ou DBSTATUS_S_DEFAULT pour DBTYPE_EMPTY. DBTYPE_BYREF ne peut pas être utilisé avec DBTYPE_NULL ou DBTYPE_EMPTY.  
  
 DBTYPE_UDT peut également être converti en DBTYPE_EMPTY et en DBTYPE_NULL. Toutefois, DBTYPE_NULL et DBTYPE_EMPTY ne peuvent pas être convertis en DBTYPE_UDT, ce qui est cohérent avec DBTYPE_BYTES. **ISSCommandWithParameters** est utilisé pour traiter les types UDT en tant que paramètres.  
  
 Les conversions de données fournies par les services principaux d’OLE DB (**IDataConvert**) ne s’appliquent pas à DBTYPE_UDT.  
  
 Aucune autre liaison n'est prise en charge.  
  
## <a name="comparability-for-irowsetfind"></a>Comparabilité pour IRowsetFind  
 Pour les types UDT, seules les comparaisons suivantes sont prises en charge :  
  
-   EQ  
  
-   NE  
  
-   IGNORE  
  
 Si une autre comparaison est tentée, DB_E_BADCOMPAREOP est retourné.  
  
## <a name="bcp-support-for-udts"></a>Prise en charge des UDT par BCP  
 Les valeurs UDT peuvent être uniquement importées et exportées en tant que valeurs de caractère ou valeurs binaires.  
  
## <a name="down-level-client-behavior-for-udts"></a>Comportement client de bas niveau pour les types UDT  
 Les UDT sont mappés aux clients de niveau inférieur de la manière suivante :  
  
|Version du client|DBTYPE_UDT<br /><br /> (longueur inférieure ou égale à 8 000 octets)|DBTYPE_UDT<br /><br /> (longueur supérieure à 8 000 octets)|  
|--------------------|------------------------------------------------------------------|---------------------------------------------------------|  
|SQL Server 2005|UDT|varbinary(max)|  
|SQL Server 2008 et ultérieur|UDT|UDT|  
  
 Quand **DataTypeCompatibility** (SSPROP_INIT_DATATYPECOMPATIBILITY) est défini sur 80, les types UDT volumineux apparaissent aux clients de la même façon que pour les clients de bas niveau.  
  
## <a name="see-also"></a>Voir aussi  
 [Types CLR volumineux définis par l’utilisateur](../../oledb/features/large-clr-user-defined-types.md)  
  
  

