---
title: Type de paramètre table OLE DB (méthodes)
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (methods)
ms.assetid: e3c2a450-8fd4-44cb-93d8-affe1b65c68e
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 15c9e3e713b1fae8176a864b01e82846f1dc9384
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "75242762"
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>Prise en charge des types de paramètre table OLE DB (méthodes)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les méthodes OLE DB standard suivantes prennent en charge les paramètres table :  
  
|Méthode|Prise en charge des paramètres table|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|Utilisée lorsque vous connaissez les informations de type du paramètre table, et que vous souhaitez instancier un objet d'ensemble de lignes de paramètre table en fonction des informations de type.<br /><br /> Pour plus d’informations, consultez « Scénario statique » dans [création d’un ensemble de lignes de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|IOpenRowset::OpenRowset|Utilisée lorsque vous ne connaissez pas les informations de type d'un paramètre table, et que vous souhaitez instancier un objet d'ensemble de lignes de paramètre table en fonction des informations de métadonnées extraites du serveur.<br /><br /> Pour plus d’informations, consultez « Scénario dynamique » dans [création d’un ensemble de lignes de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|ISSCommandWithParameters::SetParameterInfo|Pour spécifier un paramètre de commande de paramètre table, le consommateur spécifie le type de paramètre « table » ou « DBTYPE_TABLE » dans le membre *pwszName* de la structure DBPARAMBINDINFO. *UlParamSize* a la valeur ~ 0. Pour plus d’informations, consultez « Spécification de paramètre table » dans [exécution de commandes contenant des paramètres table](../../relational-databases/native-client-ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md).|  
|ISSCommandWithParameters::SetParameterProperties|Définit les propriétés spécifiques aux paramètres table, telles que le nom de schéma, le nom de type, l'ordre des colonnes et les colonnes par défaut.<br /><br /> Le consommateur spécifie l’ordinal du paramètre dans le membre *iOrdinal* de la structure SSPARAMPROPS. Le jeu de propriétés demandé est DBPROPSET_SQLSERVERPARAMETER.|  
|ISSCommandWithParameters::GetParameterInfo|Obtient les types de tous les paramètres d'une commande spécifiée.<br /><br /> Pour les paramètres table, le champ *wType* de la structure DBPARAMINFO a la valeur DBTYPE_TABLE. Le champ *ulParamSize* est défini sur ~0 pour indiquer une longueur inconnue.|  
|ISSCommandWithParameters::GetParameterProperties|Obtient des informations de type supplémentaires pour les paramètres du type DBTYPE_TABLE.<br /><br /> Le consommateur spécifie l’ordinal du paramètre dans le membre *iOrdinal* de la structure SSPARAMPROPS. Le consommateur peut demander toutes les propriétés dans le jeu de propriétés DBPROPSET_SQLSERVERPARAMETER qui sont répertoriées sous ISSCommandWithParameters :: SetParameterProperties.<br /><br /> Dans la mesure où le consommateur ne connaît pas le type de paramètre table, le fournisseur doit définir SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME et SSPROP_PARAM_TYPE_CATALOGNAME sur leurs valeurs correctes. Les propriétés restantes, SSPROP_PARAM_TABLE_DEFAULT_COLUMNS et SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER, utilisent leurs valeurs par défaut. Une fois que le consommateur a découvert le nom du type de paramètre table, il utilise IOpenRowset::OpenRowset pour créer une instance de ce paramètre table, en spécifiant le nom du type de paramètre table. Pour plus d’informations, consultez [découverte de type de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md).|  
|IRowsetInfo::GetProperties|Obtient les propriétés de l'ensemble de lignes de paramètre table. Le consommateur peut utiliser ces propriétés pour optimiser la configuration des liaisons.|  
|IColumnsRowset::GetColumnsRowset|Récupère les informations de métadonnées relatives une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour les paramètres table, cette même interface fournit des informations de métadonnées détaillées à propos de chaque colonne, notamment les suivantes :<br /><br /> DBCOLUMN_FLAGS indique la possibilité de valeur NULL via le bit DBCOLUMNFLAGS_ISNULLABLE.<br /><br /> DBCOLUMN_ISUNIQUE indique si la colonne est une colonne d'identité.<br /><br /> DBCOLUMN_COMPUTEMODE indique si la colonne est calculée.|  
|IAccessor::CreateAccessor|Pour lier un objet d’ensemble de lignes de paramètre table à un paramètre de commande, créez un accesseur dont le membre *wType* a la valeur DBTYPE_TABLE. La structure DBOBJECT contiendra IID_IRowset ou toute autre interface d’objet d’ensemble de lignes valide dans le membre *iid*. Les autres champs sont traités de la même façon que DBTYPE_IUNKNOWN.|  
|||

## <a name="see-also"></a>Voir aussi  
 [Prise en charge du type de paramètre table OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [Création d’un ensemble de lignes de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
