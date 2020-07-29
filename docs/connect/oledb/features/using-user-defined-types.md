---
title: Utilisation de types définis par l’utilisateur | Microsoft Docs
description: Utilisation de types définis par l’utilisateur avec OLE DB Driver pour SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- DBPROPSET_DATASOURCEINFO property set
- UDTs [OLE DB Driver for SQL Server]
- user-defined types [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server, user-defined types
- DBPROPSET_SQLSERVERPARAMETER property set
- IColumnsRowset interface
- MSOLEDBSQL, user-defined types
- OLE DB Driver for SQL Server, user-defined types
- data access [OLE DB Driver for SQL Server], user-defined types
- ISSCommandWithParameters interface
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 53dc061002141039a84931168cb1a4492a793c1b
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86006827"
---
# <a name="using-user-defined-types"></a>Utilisation des types définis par l'utilisateur
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Les types définis par l'utilisateur (UDT) ont été introduits dans [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. Ils étendent le système de types SQL en vous permettant de stocker des objets et des structures de données personnalisées dans une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les UDT peuvent contenir plusieurs types de données et avoir des comportements, ce qui les différencie des types de données d'alias traditionnels qui ne comportent qu'un seul type de données système [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les UDT sont définis à l'aide de n'importe quel langage pris en charge par le CLR (Common Language Runtime) .NET capable de produire du code vérifiable, Cela inclut Microsoft Visual C#<sup>®</sup> et Visual Basic<sup>®</sup> .NET. Les données sont exposées en tant que champs et propriétés d'une classe ou d'une structure .NET, et les comportements sont définis par des méthodes de la classe ou de la structure.  
  
 Un type UDT peut être utilisé en tant que définition de colonne d’une table, en tant que variable dans un lot [!INCLUDE[tsql](../../../includes/tsql-md.md)] ou en tant qu’argument d’une fonction ou d’une procédure stockée [!INCLUDE[tsql](../../../includes/tsql-md.md)].  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver pour SQL Server  
 OLE DB Driver pour SQL Server prend en charge les types UDT comme types binaires avec des informations de métadonnées, ce qui vous permet de les gérer en tant qu’objets. Les colonnes UDT sont exposées comme DBTYPE_UDT, et leurs métadonnées sont exposées via l’interface OLE DB **IColumnRowset** principale et la nouvelle interface [ISSCommandWithParameters](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md).  
  
> [!NOTE]  
>  La méthode **IRowsetFind::FindNextRow** ne fonctionne pas avec le type de données UDT. DB_E_BADCOMPAREOP est retourné si l'UDT est utilisé comme type de colonne de recherche.  
  
### <a name="data-bindings-and-coercions"></a>Liaisons de données et forçages de type  
 Le tableau suivant décrit la liaison et le forçage de type survenant lorsque vous utilisez les types de données répertoriés avec un UDT [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Les colonnes UDT sont exposées via le fournisseur OLE DB Driver pour SQL Server sous la forme DBTYPE_UDT. Vous pouvez obtenir les métadonnées par le biais des ensembles de lignes de schéma appropriés et ainsi gérer en tant qu'objets vos propres types définis.  
  
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
  
 <sup>2</sup>Non traité dans cet article.  
  
 <sup>3</sup> La conversion de données d’une chaîne hexadécimale en données binaires est réalisée.  
  
 <sup>4</sup> La conversion de données binaires en chaîne hexadécimale est réalisée.  
  
 <sup>5</sup>La validation peut avoir lieu au moment de créer l’accesseur ou au moment de l’extraction, l’erreur est DB_E_ERRORSOCCURRED ; l’état de la liaison est défini sur DBBINDSTATUS_UNSUPPORTEDCONVERSION.  
  
 <sup>6</sup>BY_REF peut être utilisé.  
  
 Les types DBTYPE_NULL et DBTYPE_EMPTY peuvent être liés pour des paramètres d'entrée mais pas pour des paramètres de résultats ou pour des sorties. S’ils sont liés pour des paramètres d’entrée, l’état doit être défini sur DBSTATUS_S_ISNULL ou DBSTATUS_S_DEFAULT.  
  
 DBTYPE_UDT peut également être converti en DBTYPE_EMPTY et DBTYPE_NULL, mais DBTYPE_NULL et DBTYPE_EMPTY ne peuvent pas être convertis en DBTYPE_UDT, ce qui est cohérent avec DBTYPE_BYTES.  
  
> [!NOTE]  
>  Une nouvelle interface est utilisée pour traiter les UDT comme paramètres, **ISSCommandWithParameters**, qui hérite **d’ICommandWithParameters**. Les applications doivent utiliser cette interface pour définir au moins le SSPROP_PARAM_UDT_NAME de la propriété DBPROPSET_SQLSERVERPARAMETER définie pour les paramètres UDT. Si cela n’est pas fait, **ICommand::Execute** retourne DB_E_ERRORSOCCURRED. Cette interface et ce jeu de propriétés sont décrits plus loin dans cet article.  
  
 Si un type défini par l’utilisateur est inséré dans une colonne qui n’est pas assez grande pour contenir toutes ses données, **ICommand::Execute** retourne S_OK avec l’état DB_E_ERRORSOCCURRED.  
  
 Les conversions de données fournies par les services principaux d’OLE DB (**IDataConvert**) ne s’appliquent pas à DBTYPE_UDT. Aucune autre liaison n'est prise en charge.  
  
### <a name="ole-db-rowset-additions-and-changes"></a>Ajout et modifications dans les ensembles de lignes OLE DB  
 OLE DB Driver pour SQL Server ajoute de nouvelles valeurs ou apporte des modifications à un grand nombre d'ensembles de lignes de schéma OLE DB principaux.  
  
#### <a name="the-procedure_parameters-schema-rowset"></a>Ensemble de lignes de schéma PROCEDURE_PARAMETERS  
 Les ajouts suivants ont été effectués dans l'ensemble de lignes de schéma PROCEDURE_PARAMETERS.  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Identificateur de nom en trois parties.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Identificateur de nom en trois parties.|  
|SS_UDT_NAME|DBTYPE_WSTR|Identificateur de nom en trois parties.|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Le nom complet d'assembly qui inclut le nom du type et toutes les identification d'assembly nécessaires pour être référencés par le CLR.|  
  
#### <a name="the-sql_assemblies-schema-rowset"></a>Ensemble de lignes de schéma SQL_ASSEMBLIES  
 OLE DB Driver pour SQL Server expose un nouvel ensemble de lignes de schéma spécifique au fournisseur qui décrit les UDT inscrits. Le serveur ASSEMBLY peut être spécifié en tant que DBTYPE_WSTR, mais n'est pas présent dans l'ensemble de lignes. S'il n'est pas spécifié, l'ensemble de lignes aura comme valeur par défaut le serveur actuel. L’ensemble de lignes de schéma SQL_ASSEMBLIES est défini dans le tableau suivant :  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Nom de catalogue de l'assembly qui contient le type.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Nom de schéma ou de propriétaire de l'assembly qui contient le type. Bien que les assemblys aient une portée définie par base de données et non par schéma, ils conservent un propriétaire qui est indiqué ici.|  
|ASSEMBLY_NAME|DBTYPE_WSTR|Nom de l'assembly qui contient le type.|  
|ASSEMBLY_ID|DBTYPE_UI4|ID d’objet de l’assembly qui contient le type.|  
|PERMISSION_SET|DBTYPE_WSTR|Valeur qui indique la portée d'accès de l'assembly. Les valeurs incluent SAFE, EXTERNAL_ACCESS et UNSAFE.|  
|ASSEMBLY_BINARY|DBTYPE_BYTES|Représentation binaire de l'assembly.|  
  
#### <a name="the-sql_assemblies_-dependencies-schema-rowset"></a>Ensemble de lignes de schéma SQL_ASSEMBLIES_ DEPENDENCIES  
 OLE DB Driver pour SQL Server expose un nouvel ensemble de lignes de schéma spécifique au fournisseur qui décrit les dépendances d’assembly d’un serveur donné. ASSEMBLY_SERVER peut être spécifié par l'appelant en tant que DBTYPE_WSTR, mais n'est pas présent dans l'ensemble de lignes. S'il n'est pas spécifié, l'ensemble de lignes aura comme valeur par défaut le serveur actuel. L’ensemble de lignes de schéma SQL_ASSEMBLY_DEPENDENCIES est défini dans le tableau suivant :  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|ASSEMBLY_CATALOG|DBTYPE_WSTR|Nom de catalogue de l'assembly qui contient le type.|  
|ASSEMBLY_SCHEMA|DBTYPE_WSTR|Nom de schéma ou de propriétaire de l'assembly qui contient le type. Bien que les assemblys aient une portée définie par base de données et non par schéma, ils conservent un propriétaire qui est indiqué ici.|  
|ASSEMBLY_ID|DBTYPE_UI4|ID d’objet de l’assembly.|  
|REFERENCED_ASSEMBLY_ID|DBTYPE_UI4|ID d’objet de l’assembly référencé.|  
  
#### <a name="the-sql_user_types-schema-rowset"></a>Ensemble de lignes de schéma SQL_USER_TYPES  
 OLE DB Driver pour SQL Server expose un nouvel ensemble de lignes de schéma, SQL_USER_TYPES, qui décrit quand sont ajoutés les types UDT inscrits pour un serveur donné. UDT_SERVER doit être spécifié en tant que DBTYPE_WSTR par l'appelant, mais n'est pas présent dans l'ensemble de lignes. L'ensemble de lignes de schéma SQL_USER_TYPES est défini dans le tableau suivant.  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|UDT_CATALOGNAME|DBTYPE_WSTR|Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom du catalogue dans lequel le type UDT est défini.|  
|UDT_SCHEMANAME|DBTYPE_WSTR|Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom du schéma dans lequel le type UDT est défini.|  
|UDT_NAME|DBTYPE_WSTR|Nom de l'assembly contenant la classe UDT.|  
|UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Le nom de type complet (AQN) inclut le nom de type précédé, le cas échéant, de l'espace de noms.|  
  
#### <a name="the-columns-schema-rowset"></a>Ensemble de lignes de schéma COLUMNS  
 Les ajouts réalisés dans l’ensemble de lignes de schéma COLUMNS incluent les colonnes suivantes :  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|SS_UDT_CATALOGNAME|DBTYPE_WSTR|Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom du catalogue dans lequel le type UDT est défini.|  
|SS_UDT_SCHEMANAME|DBTYPE_WSTR|Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom du schéma dans lequel le type UDT est défini.|  
|SS_UDT_NAME|DBTYPE_WSTR|Nom du type défini par l'utilisateur (UDT).|  
|SS_UDT_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Le nom de type complet (AQN) inclut le nom de type précédé, le cas échéant, de l'espace de noms.|  
  
### <a name="ole-db-property-set-additions-and-changes"></a>Ajouts et modifications effectués dans le jeu de propriétés OLE DB  
 OLE DB Driver pour SQL Server ajoute de nouvelles valeurs ou apporte des modifications à un grand nombre d'ensembles de propriétés OLE DB principaux.  
  
#### <a name="the-dbpropset_sqlserverparameter-property-set"></a>Jeu de propriétés DBPROPSET_SQLSERVERPARAMETER  
 Pour permettre la prise en charge des types UDT via OLE DB, OLE DB Driver pour SQL Server implémente le nouveau jeu de propriétés DBPROPSET_SQLSERVERPARAMETER qui contient les valeurs suivantes :  
  
|Name|Type|Description|  
|----------|----------|-----------------|  
|SSPROP_PARAM_UDT_CATALOGNAME|DBTYPE_WSTR|Identificateur de nom en trois parties.<br /><br /> Pour les paramètres UDT, cette propriété est une chaîne qui spécifie le nom du catalogue dans lequel le type défini par l'utilisateur est défini.|  
|SSPROP_PARAM_UDT_SCHEMANAME|DBTYPE_WSTR|Identificateur de nom en trois parties.<br /><br /> Pour les paramètres UDT, cette propriété est une chaîne qui spécifie le nom du schéma dans lequel le type défini par l'utilisateur est défini.|  
|SSPROP_PARAM_UDT_NAME|DBTYPE_WSTR|Identificateur de nom en trois parties.<br /><br /> Pour les colonnes UDT, cette propriété est une chaîne qui spécifie le nom en une partie du type défini par l'utilisateur.|  
  
 SSPROP_PARAM_UDT_NAME est obligatoire. SSPROP_PARAM_UDT_CATALOGNAME et SSPROP_PARAM_UDT_SCHEMANAME sont facultatifs. Si l’une des propriétés est spécifiée de manière incorrecte, DB_E_ERRORSINCOMMAND est retourné. Si SSPROP_PARAM_UDT_CATALOGNAME et SSPROP_PARAM_UDT_SCHEMANAME ne sont pas spécifiés, le type défini par l'utilisateur (UDT) doit être défini dans la même base de données et dans le même schéma que la table. Si la définition du type défini par l'utilisateur ne se trouve pas dans le même schéma que la table (mais dans la même base de données), SSPROP_PARAM_UDT_SCHEMANAME doit être spécifié. Si la définition du type défini par l’utilisateur se trouve dans une base de données différente, SSPROP_PARAM_UDT_CATALOGNAME et SSPROP_PARAM_UDT_SCHEMANAME doivent être spécifiés.  
  
#### <a name="the-dbpropset_sqlservercolumn-property-set"></a>Jeu de propriétés DBPROPSET_SQLSERVERCOLUMN  
 Pour prendre en charge la création de tables dans l’interface **ITableDefinition**, OLE DB Driver pour SQL Server ajoute les trois nouvelles colonnes suivantes au jeu de propriétés DBPROPSET_SQLSERVERCOLUMN.  
  
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
 OLE DB Driver pour SQL Server ajoute de nouvelles valeurs ou apporte des modifications à un grand nombre d'interfaces OLE DB principales.  
  
#### <a name="the-isscommandwithparameters-interface"></a>Interface ISSCommandWithParameters  
 Pour prendre en charge les types UDT via OLE DB, OLE DB Driver pour SQL Server implémente plusieurs modifications, notamment l’ajout de l’interface **ISSCommandWithParameters**. Cette nouvelle interface hérite de l’interface OLE DB **ICommandWithParameters** principale. Outre les trois méthodes héritées **d’ICommandWithParameters** (**GetParameterInfo**, **MapParameterNames** et **SetParameterInfo**), **ISSCommandWithParameters** fournit les méthodes **GetParameterProperties** et **SetParameterProperties** employées pour la gestion des types de données spécifiques au serveur.  
  
> [!NOTE]  
>  L’interface **ISSCommandWithParameters** exploite également la nouvelle structure SSPARAMPROPS.  
  
#### <a name="the-icolumnsrowset-interface"></a>Interface IColumnsRowset  
 Outre l’interface **ISSCommandWithParameters**, OLE DB Driver pour SQL Server ajoute également de nouvelles valeurs à l’ensemble de lignes retourné en appelant la méthode **IColumnsRowset::GetColumnRowset**, notamment les valeurs suivantes.  
  
|Nom de la colonne|Type|Description|  
|-----------------|----------|-----------------|  
|DBCOLUMN_SS_UDT_CATALOGNAME|DBTYPE_WSTR|Identificateur du nom de catalogue d'un type défini par l'utilisateur (UDT).|  
|DBCOLUMN_SS_UDT_SCHEMANAME|DBTYPE_WSTR|Identificateur du nom de schéma d'un type défini par l'utilisateur (UDT).|  
|DBCOLUMN_SS_UDT_NAME|DBTYPE_WSTR|Identificateur du nom d'un type défini par l'utilisateur (UDT).|  
|DBCOLUMN_SS_ASSEMBLY_TYPENAME|DBTYPE_WSTR|Nom complet de l'assembly, incluant le nom du type et toutes les informations d'identification de l'assembly nécessaires pour qu'il soit référencé par le CLR.|  
  
 Vous pouvez différencier une colonne UDT de serveur d’autres types binaires quand DBCOLUMN_TYPE a la valeur DBTYPE_UDT en consultant les métadonnées UDT ajoutées spécifiées dans le tableau précédent. Si ces données sont partiellement complètes, le type de serveur est un type défini par l'utilisateur (UDT). Pour les types serveur autres que des types définis par l'utilisateur (UDT), ces colonnes sont toujours retournées comme NULL.  
 
  
## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités OLE DB Driver pour SQL Server](../../oledb/features/oledb-driver-for-sql-server-features.md)    
 [ISSCommandWithParameters &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
  
