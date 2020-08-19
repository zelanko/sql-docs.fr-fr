---
description: Utilisation de types définis par l’utilisateur dans SQL Server Native Client
title: Utilisation de types définis par l’utilisateur | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_DATASOURCEINFO property set
- UDTs [SQL Server Native Client]
- user-defined types [SQL Server], SQL Server Native Client
- SQL Server Native Client OLE DB provider, user-defined types
- DBPROPSET_SQLSERVERPARAMETER property set
- IColumnsRowset interface
- SQLNCLI, user-defined types
- SQL Server Native Client, user-defined types
- data access [SQL Server Native Client], user-defined types
- ISSCommandWithParameters interface
ms.assetid: e15d8169-3517-4323-9c9e-0f5c34aff7df
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b56a4e3446c827ecd8372876aa54cb023827a861
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88448225"
---
# <a name="using-user-defined-types-in-sql-server-native-client"></a>Utilisation de types définis par l’utilisateur dans SQL Server Native Client
[!INCLUDE[appliesto-ss-asdb-xxxx-pdw-md](../../../includes/appliesto-ss-asdb-xxxx-pdw-md.md)]

  Les types définis par l'utilisateur (UDT) ont été introduits dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Ils étendent le système de types SQL en vous permettant de stocker des objets et des structures de données personnalisées dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les UDT peuvent contenir plusieurs types de données et avoir des comportements, ce qui les différencie des types de données d'alias traditionnels qui ne comportent qu'un seul type de données système [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les UDT sont définis à l'aide de n'importe quel langage pris en charge par le CLR (Common Language Runtime) .NET capable de produire du code vérifiable, Cela inclut Microsoft Visual C#<sup>®</sup> et Visual Basic<sup>®</sup> .NET. Les données sont exposées en tant que champs et propriétés d'une classe ou d'une structure .NET, et les comportements sont définis par des méthodes de la classe ou de la structure.  
  
 Un type UDT peut être utilisé en tant que définition de colonne d’une table, en tant que variable dans un lot [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou en tant qu’argument d’une fonction ou d’une procédure stockée [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
## <a name="sql-server-native-client-ole-db-provider"></a>Fournisseur OLE DB SQL Server Native Client  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client prend en charge les UDT comme types binaires avec les informations de métadonnées, ce qui vous permet de gérer les UDT comme des objets. Les colonnes UDT sont exposées comme DBTYPE_UDT, et leurs métadonnées sont exposées via l’interface OLE DB **IColumnRowset** principale et la nouvelle interface [ISSCommandWithParameters](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md).  
  
> [!NOTE]  
>  La méthode **IRowsetFind::FindNextRow** ne fonctionne pas avec le type de données UDT. DB_E_BADCOMPAREOP est retourné si l'UDT est utilisé comme type de colonne de recherche.  
  
### <a name="data-bindings-and-coercions"></a>Liaisons de données et forçages de type  
 Le tableau suivant décrit la liaison et le forçage de type survenant lorsque vous utilisez les types de données répertoriés avec un UDT [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les colonnes UDT sont exposées par le biais du [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur OLE DB Native Client comme DBTYPE_UDT. Vous pouvez obtenir les métadonnées par le biais des ensembles de lignes de schéma appropriés et ainsi gérer en tant qu'objets vos propres types définis.  
  
|Type de données|Vers le serveur<br /><br /> **UDT**|Vers le serveur<br /><br /> **Non-UDT**|Depuis le serveur<br /><br /> **UDT**|Depuis le serveur<br /><br /> **Non-UDT**|  
|---------------|---------------------------|--------------------------------|-----------------------------|----------------------------------|  
|DBTYPE_UDT|Pris en charge<sup>6</sup>|Erreur<sup>1</sup>|Pris en charge<sup>6</sup>|Erreur<sup>5</sup>|  
|DBTYPE_BYTES|Pris en charge<sup>6</sup>|N/A<sup>2</sup>|Pris en charge<sup>6</sup>|N/A<sup>2</sup>|  
|DBTYPE_WSTR|Pris en charge<sup>3,6</sup>|N/A<sup>2</sup>|Pris en charge<sup>4.6</sup>|N/A<sup>2</sup>|  
|DBTYPE_BSTR|Pris en charge<sup>3,6</sup>|N/A<sup>2</sup>|Pris en charge<sup>4</sup>|N/A<sup>2</sup>|  
|DBTYPE_STR|Pris en charge<sup>3,6</sup>|N/A<sup>2</sup>|Pris en charge<sup>4.6</sup>|N/A<sup>2</sup>|  
|DBTYPE_IUNKNOWN|Non pris en charge|N/A<sup>2</sup>|Non pris en charge|N/A<sup>2</sup>|  
|DBTYPE_VARIANT (VT_UI1 &#124; VT_ARRAY)|Pris en charge<sup>6</sup>|N/A<sup>2</sup>|Pris en charge<sup>4</sup>|N/A<sup>2</sup>|  
|DBTYPE_VARIANT (VT_BSTR)|Pris en charge<sup>3,6</sup>|N/A<sup>2</sup>|N/A|N/A<sup>2</sup>|  
  
 <sup>1</sup>Si un type de serveur autre que DBTYPE_UDT est spécifié avec **ICommandWithParameters::SetParameterInfo** et si le type d’accesseur est DBTYPE_UDT, une erreur se produit lors de l’exécution de l’instruction (DB_E_ERRORSOCCURRED, l’état du paramètre est DBSTATUS_E_BADACCESSOR). Sinon, les données sont envoyées au serveur, mais le serveur retourne une erreur indiquant qu'il n'existe pas de conversion implicite entre l'UDT et le type de données du paramètre.  
  
 <sup>2</sup> Au-delà du cadre de cette rubrique.  
  
 <sup>3</sup> La conversion de données d’une chaîne hexadécimale en données binaires est réalisée.  
  
 <sup>4</sup> La conversion de données binaires en chaîne hexadécimale est réalisée.  
  
 <sup>5</sup>La validation peut avoir lieu au moment de créer l’accesseur ou au moment de l’extraction, l’erreur est DB_E_ERRORSOCCURRED ; l’état de la liaison est défini sur DBBINDSTATUS_UNSUPPORTEDCONVERSION.  
  
 <sup>6</sup>BY_REF peut être utilisé.  
  
 Les types DBTYPE_NULL et DBTYPE_EMPTY peuvent être liés pour des paramètres d'entrée mais pas pour des paramètres de résultats ou pour des sorties. S’ils sont liés pour des paramètres d’entrée, l’état doit être défini sur DBSTATUS_S_ISNULL ou DBSTATUS_S_DEFAULT.  
  
 DBTYPE_UDT peut également être converti en DBTYPE_EMPTY et DBTYPE_NULL, mais DBTYPE_NULL et DBTYPE_EMPTY ne peuvent pas être convertis en DBTYPE_UDT, ce qui est cohérent avec DBTYPE_BYTES.  
  
> [!NOTE]  
>  Une nouvelle interface est utilisée pour traiter les UDT comme paramètres, **ISSCommandWithParameters**, qui hérite **d’ICommandWithParameters**. Les applications doivent utiliser cette interface pour définir au moins le SSPROP_PARAM_UDT_NAME de la propriété DBPROPSET_SQLSERVERPARAMETER définie pour les paramètres UDT. Si cela n’est pas fait, **ICommand::Execute** retourne DB_E_ERRORSOCCURRED. Ce jeu d'interface et de propriété est décrit plus loin dans cette rubrique.  
  
 Si un type défini par l’utilisateur est inséré dans une colonne qui n’est pas assez grande pour contenir toutes ses données, **ICommand::Execute** retourne S_OK avec l’état DB_E_ERRORSOCCURRED.  
  
 Les conversions de données fournies par les services principaux d’OLE DB (**IDataConvert**) ne s’appliquent pas à DBTYPE_UDT. Aucune autre liaison n'est prise en charge.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Ajout et modifications dans les ensembles de lignes OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ajoute de nouvelles valeurs ou des modifications à un grand nombre d’ensembles de lignes de schéma OLE DB de base.  
  
#### <a name="the-procedure_parameters-schema-rowset"></a>Ensemble de lignes de schéma PROCEDURE_PARAMETERS  
 Les ajouts suivants ont été effectués dans l'ensemble de lignes de schéma PROCEDURE_PARAMETERS.  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Identificateur de nom en trois parties.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Identificateur de nom en trois parties.|  
|SS_UDT_NAME|DBTYPE_WSTR|Identificateur de nom en trois parties.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Le nom complet d'assembly qui inclut le nom du type et toutes les identification d'assembly nécessaires pour être référencés par le CLR.|  
  
#### <a name="the-sql_assemblies-schema-rowset"></a>Ensemble de lignes de schéma SQL_ASSEMBLIES  
 Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client expose un nouvel ensemble de lignes de schéma spécifique au fournisseur qui décrit les UDT inscrits. Le serveur ASSEMBLY peut être spécifié en tant que DBTYPE_WSTR, mais n'est pas présent dans l'ensemble de lignes. S'il n'est pas spécifié, l'ensemble de lignes aura comme valeur par défaut le serveur actuel. L'ensemble de lignes de schéma SQL_ASSEMBLIES est défini dans le tableau suivant.  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Nom de catalogue de l'assembly qui contient le type.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Nom de schéma ou de propriétaire de l'assembly qui contient le type. Bien que les assemblys aient une portée définie par base de données et non par schéma, ils conservent un propriétaire qui est indiqué ici.|  
|ASSEMBLY_NAME|DBTYPE_WSTR|Nom de l'assembly qui contient le type.|  
|ASSEMBLY_ID|DBTYPE_UI4|ID d'objet de l'assembly qui contient le type.|  
|PERMISSION_SET|DBTYPE_WSTR|Valeur qui indique la portée d'accès de l'assembly. Les valeurs incluent SAFE, EXTERNAL_ACCESS et UNSAFE.|  
|ASSEMBLY_BINARY|DBTYPE_BYTES|Représentation binaire de l'assembly.|  
  
#### <a name="the-sql_assemblies_-dependencies-schema-rowset"></a>Ensemble de lignes de schéma SQL_ASSEMBLIES_ DEPENDENCIES  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Le fournisseur OLE DB Native Client expose un nouvel ensemble de lignes de schéma spécifique au fournisseur qui décrit les dépendances d’assembly pour un serveur spécifié. ASSEMBLY_SERVER peut être spécifié par l'appelant en tant que DBTYPE_WSTR, mais n'est pas présent dans l'ensemble de lignes. S'il n'est pas spécifié, l'ensemble de lignes aura comme valeur par défaut le serveur actuel. L'ensemble de lignes de schéma SQL_ASSEMBLY_DEPENDENCIES est défini dans le tableau suivant.  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Nom de catalogue de l'assembly qui contient le type.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Nom de schéma ou de propriétaire de l'assembly qui contient le type. Bien que les assemblys aient une portée définie par base de données et non par schéma, ils conservent un propriétaire qui est indiqué ici.|  
|ASSEMBLY_ID|DBTYPE_UI4|ID d'objet de l'assembly.|  
|REFERENCED_ASSEMBLY_ID|DBTYPE_UI4|ID d'objet de l'assembly référencé.|  
  
#### <a name="the-sql_user_types-schema-rowset"></a>Ensemble de lignes de schéma SQL_USER_TYPES  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Le fournisseur OLE DB Native Client expose un nouvel ensemble de lignes de schéma, SQL_USER_TYPES, qui décrit quand les UDT inscrits pour un serveur spécifié sont ajoutés. UDT_SERVER doit être spécifié en tant que DBTYPE_WSTR par l'appelant, mais n'est pas présent dans l'ensemble de lignes. L'ensemble de lignes de schéma SQL_USER_TYPES est défini dans le tableau suivant.  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|UDT_CATALOGNAME|DBTYPE_WSTR|Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom du catalogue dans lequel le schéma UDT est défini.|  
|UDT_SCHEMANAME|DBTYPE_WSTR|Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom du schéma dans lequel le schéma UDT est défini.|  
|UDT_NAME|DBTYPE_WSTR|Nom de l'assembly contenant la classe UDT.|  
|UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Le nom de type complet (AQN) inclut le nom de type précédé, le cas échéant, de l'espace de noms.|  
  
#### <a name="the-columns-schema-rowset"></a>Ensemble de lignes de schéma COLUMNS  
 Les colonnes suivantes ont été ajoutées à l'ensemble de lignes de schéma COLUMNS.  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom du catalogue dans lequel le schéma UDT est défini.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom du schéma dans lequel le schéma UDT est défini.|  
|SS_UDT_NAME|DBTYPE_WSTR|Nom du type défini par l'utilisateur (UDT).|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Le nom de type complet (AQN) inclut le nom de type précédé, le cas échéant, de l'espace de noms.|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Ajouts et modifications effectués dans le jeu de propriétés OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ajoute de nouvelles valeurs ou des modifications à un grand nombre de jeux de propriétés de OLE DB de base.  
  
#### <a name="the-dbpropset_sqlserverparameter-property-set"></a>Jeu de propriétés DBPROPSET_SQLSERVERPARAMETER  
 Afin de prendre en charge les UDT via OLE DB, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client implémente le nouveau jeu de propriétés DBPROPSET_SQLSERVERPARAMETER qui contient les valeurs suivantes.  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|SSPROP_PARAM_UDT_CATALOGNAME|DBTYPE_WSTR|Identificateur de nom en trois parties.<br /><br /> Pour les paramètres UDT, cette propriété est une chaîne qui spécifie le nom du catalogue dans lequel le type défini par l'utilisateur est défini.|  
|SSPROP_PARAM_UDT_SCHEMANAME|DBTYPE_WSTR|Identificateur de nom en trois parties.<br /><br /> Pour les paramètres UDT, cette propriété est une chaîne qui spécifie le nom du schéma dans lequel le type défini par l'utilisateur est défini.|  
|SSPROP_PARAM_UDT_NAME|DBTYPE_WSTR|Identificateur de nom en trois parties.<br /><br /> Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom en une partie du type défini par l'utilisateur.|  
  
 SSPROP_PARAM_UDT_NAME est obligatoire. SSPROP_PARAM_UDT_CATALOGNAME et SSPROP_PARAM_UDT_SCHEMANAME sont facultatifs. Si l'une des propriétés est spécifiée de manière incorrecte, DB_E_ERRORSINCOMMAND est retourné. Si SSPROP_PARAM_UDT_CATALOGNAME et SSPROP_PARAM_UDT_SCHEMANAME ne sont pas spécifiés, le type défini par l'utilisateur (UDT) doit être défini dans la même base de données et dans le même schéma que la table. Si la définition du type défini par l'utilisateur ne se trouve pas dans le même schéma que la table (mais dans la même base de données), SSPROP_PARAM_UDT_SCHEMANAME doit être spécifié. Si la définition du type défini par l'utilisateur se trouve dans une base de données différente, SSPROP_PARAM_UDT_CATALOGNAME et SSPROP_PARAM_UDT_SCHEMANAME doivent être spécifiés.  
  
#### <a name="the-dbpropset_sqlservercolumn-property-set"></a>Jeu de propriétés DBPROPSET_SQLSERVERCOLUMN  
 Pour prendre en charge la création de tables dans l’interface **ITableDefinition** , [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ajoute les trois nouvelles colonnes suivantes au jeu de propriétés DBPROPSET_SQLSERVERCOLUMN.  
  
|Name|Description|Type|Description|  
|----------|-----------------|----------|-----------------|  
|SSPROP_COL_UDT_CATALOGNAME|UDT_CATALOGNAME|VT_BSTR|Pour les colonnes de type DBTYPE_UDT, cette propriété est une chaîne qui spécifie le nom du catalogue dans lequel le type défini par l'utilisateur (UDT) est défini.|  
|SSPROP_COL_UDT_SCHEMANAME|UDT_SCHEMANAME|VT_BSTR|Pour les colonnes de type DBTYPE_UDT, cette propriété est une chaîne qui spécifie le nom du schéma dans lequel le type défini par l'utilisateur (UDT) est défini.|  
|SSPROP_COL_UDT_NAME|UDT_NAME|VT_BSTR|Pour les colonnes de type DBTYPE_UDT, cette propriété est une chaîne qui spécifie le nom en une partie du type défini par l'utilisateur (UDT). Pour les autres types de colonnes, cette propriété retourne une chaîne vide.|  
  
> [!NOTE]  
>  Les types définis par l'utilisateur (UDT) n'apparaissent pas dans l'ensemble de lignes de schéma PROVIDER_TYPES. Toutes les colonnes ont un accès en lecture et écriture.  
  
 ADO fait référence à ces propriétés en utilisant l'entrée correspondante dans la colonne Description.  
  
 SSPROP_COL_UDTNAME est obligatoire. SSPROP_COL_UDT_CATALOGNAME et SSPROP_COL_UDT_SCHEMANAME sont facultatifs. Si l’une des propriétés est spécifiée de manière incorrecte, **DB_E_ERRORSINCOMMAND** est retourné.  
  
 Si ni SSPROP_COL_UDT_CATALOGNAME ni SSPROP_COL_UDT_SCHEMANAME n'est spécifié, le type défini par l'utilisateur (UDT) doit être défini dans la même base de données et dans le même schéma que la table.  
  
 Si la définition du type défini par l'utilisateur (UDT) ne se trouve pas dans le même schéma que la table (mais dans la même base de données), SSPROP_COL_UDT_SCHEMANAME doit être spécifié.  
  
 Si la définition du type défini par l'utilisateur (UDT) se trouve dans une base de données différente, SSPROP_COL_UDT_CATALOGNAME et SSPROP_COL_UDT_SCHEMANAME doivent être spécifiés.  
  
### <a name="ole-db-interface-additions-and-changes"></a>Ajout et modifications dans l'interface OLE DB  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ajoute de nouvelles valeurs ou des modifications à la plupart des interfaces de OLE DB principales.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Interface ISSCommandWithParameters  
 Pour prendre en charge les UDT via OLE DB, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client implémente un certain nombre de modifications, y compris l’ajout de l’interface **ISSCommandWithParameters** . Cette nouvelle interface hérite de l’interface OLE DB **ICommandWithParameters** principale. Outre les trois méthodes héritées de **ICommandWithParameters**; **GetParameterInfo**, **MapParameterNames**et **SetParameterInfo**; **ISSCommandWithParameters** fournit les méthodes **GetParameterProperties** et **SetParameterProperties** utilisées pour gérer les types de données spécifiques au serveur.  
  
> [!NOTE]  
>  L’interface **ISSCommandWithParameters** exploite également la nouvelle structure SSPARAMPROPS.  
  
#### <a name="the-icolumnsrowset-interface"></a>Interface IColumnsRowset  
 En plus de l’interface **ISSCommandWithParameters** , [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ajoute également de nouvelles valeurs à l’ensemble de lignes retourné par l’appel de la méthode **IColumnsRowset :: GetColumnRowset** , y compris les éléments suivants.  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_UDT_CATALOGNAME|DBTYPE_WSTR|Identificateur du nom de catalogue d'un type défini par l'utilisateur (UDT).|  
|DBCOLUMN_SS_UDT_SCHEMANAME|DBTYPE_WSTR|Identificateur du nom de schéma d'un type défini par l'utilisateur (UDT).|  
|DBCOLUMN_SS_UDT_NAME|DBTYPE_WSTR|Identificateur du nom d'un type défini par l'utilisateur (UDT).|  
|DBCOLUMN_SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Nom complet de l'assembly, incluant le nom du type et toutes les informations d'identification de l'assembly nécessaires pour qu'il soit référencé par le CLR.|  
  
 Vous pouvez différencier une colonne UDT de serveur d'autres types binaires lorsque DBCOLUMN_TYPE est défini sur DBTYPE_UDT en consultant les métadonnées UDT ajoutées spécifiées ci-dessus. Si ces données sont partiellement complètes, le type de serveur est un type défini par l'utilisateur (UDT). Pour les types serveur autres que des types définis par l'utilisateur (UDT), ces colonnes sont toujours retournées comme NULL.  
  
## <a name="sql-server-native-client-odbc-driver"></a>Pilote ODBC SQL Server Native Client  
 Un certain nombre de modifications ont été apportées au [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client pour la prise en charge des UDT. Le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client mappe l' [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] UDT à SQL_SS_UDT identificateur de type de données SQL spécifique au pilote. Les colonnes UDT sont signalées en tant que SQL_SS_UDT. Si vous mappez une colonne UDT explicitement à un autre type dans une instruction SQL à l’aide des méthodes **ToString** ou **TOXMLSTRING** de l’UDT ou via la fonction **Cast/Convert** , le type de la colonne dans le jeu de résultats reflète le type réel dans lequel la colonne a été convertie.  
  
### <a name="sqlcolattribute-sqldescribeparam-sqlgetdescfield"></a>SQLColAttribute, SQLDescribeParam, SQLGetDescField  
 Quatre nouveaux champs de descripteur spécifiques au pilote ont été ajoutés pour fournir des informations supplémentaires pour une colonne UDT d’un jeu de résultats, ou un paramètre UDT de la procédure stockée/requête paramétrable, à récupérer via les fonctions [SQLColAttribute](../../../relational-databases/native-client-odbc-api/sqlcolattribute.md), [SQLDescribeParam](../../../relational-databases/native-client-odbc-api/sqldescribeparam.md)et [SQLGetDescField](../../../relational-databases/native-client-odbc-api/sqlgetdescfield.md) .  
  
 Les quatre nouveaux champs de descripteur ajoutés sont SQL_CA_SS_UDT_CATALOG_NAME, SQL_CA_SS_UDT_SCHEMA_NAME, SQL_CA_SS_UDT_TYPE_NAME et SQL_CA_SS_UDT_ASSEMBLY_TYPE_NAME.  
  
### <a name="sqlcolumns-sqlprocedurecolumns"></a>SQLColumns, SQLProcedureColumns  
 En outre, trois nouvelles colonnes spécifiques au pilote sont ajoutées au jeu de résultats retourné par les fonctions [SQLColumns](../../../relational-databases/native-client-odbc-api/sqlcolumns.md) et [SQLProcedureColumns](../../../relational-databases/native-client-odbc-api/sqlprocedurecolumns.md) pour fournir des informations supplémentaires sur une colonne de jeu de résultats UDT ou un paramètre UDT. Ces trois nouvelles colonnes sont SS_UDT_CATALOG_NAME, SS_UDT_SCHEMA_NAME et SS_UDT_ASSEMBLY_TYPE_NAME.  
  
### <a name="supported-conversions"></a>Conversions prises en charge  
 Lorsque vous procédez à des conversions entre des types de données SQL vers C, SQL_C_WCHAR, SQL_C_BINARY et SQL_C_CHAR peuvent tous être convertis en SQL_SS_XML. Notez toutefois que les données binaires sont converties en chaîne hexadécimale lors de la conversion depuis les types de données SQL SQL_C_WCHAR et SQL_C_CHAR.  
  
 Lorsque vous procédez à des conversions entre des types de données C vers SQL, SQL_C_WCHAR, SQL_C_BINARY et SQL_C_CHAR peuvent tous être convertis en SQL_SS_UDT. Notez toutefois que les données binaires sont converties en une chaîne hexadécimale lors de la conversion à partir de la SQL_C_WCHAR et SQL_C_CHAR les types de données SQL.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de SQL Server Native Client](../../../relational-databases/native-client/features/sql-server-native-client-features.md)   
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
