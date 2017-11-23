---
title: "Support de Type paramètre table OLE DB (méthodes) | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-table-valued-parameters
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: table-valued parameters (OLE DB), API support (methods)
ms.assetid: e3c2a450-8fd4-44cb-93d8-affe1b65c68e
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 9b020147ef141d08fa1064564e10616c1faef87f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2017
---
# <a name="ole-db-table-valued-parameter-type-support-methods"></a>Prise en charge des types de paramètre table OLE DB (méthodes)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Les méthodes OLE DB standard suivantes prennent en charge les paramètres table :  
  
|Méthode|Prise en charge des paramètres table|  
|------------|-------------------------------------|  
|ITableDefinitionWithConstraints::CreateTableWithConstraints|Utilisée lorsque vous connaissez les informations de type du paramètre table, et que vous souhaitez instancier un objet d'ensemble de lignes de paramètre table en fonction des informations de type.<br /><br /> Pour plus d’informations, consultez « Scénario statique » dans [la création de lignes de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|IOpenRowset::OpenRowset|Utilisée lorsque vous ne connaissez pas les informations de type d'un paramètre table, et que vous souhaitez instancier un objet d'ensemble de lignes de paramètre table en fonction des informations de métadonnées extraites du serveur.<br /><br /> Pour plus d’informations, consultez « Scénario dynamique » dans [la création de lignes de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md).|  
|ISSCommandWithParameters::SetParameterInfo|Pour spécifier un paramètre de commande de paramètre table, le consommateur Spécifie le type du paramètre en tant que « table » ou « DBTYPE_TABLE » dans le *pwszName* membre de la structure DBPARAMBINDINFO. Le *ulParamSize* est défini sur ~ 0. Pour plus d’informations, consultez « Spécification de paramètre table » dans [Executing Commands Containing Table-Valued paramètres](../../relational-databases/native-client-ole-db-table-valued-parameters/executing-commands-containing-table-valued-parameters.md).|  
|ISSCommandWithParameters::SetParameterProperties|Définit les propriétés spécifiques aux paramètres table, telles que le nom de schéma, le nom de type, l'ordre des colonnes et les colonnes par défaut.<br /><br /> Le consommateur Spécifie l’ordinal du paramètre dans le *iOrdinal* de la structure SSPARAMPROPS. Le jeu de propriétés demandé est DBPROPSET_SQLSERVERPARAMETER.|  
|ISSCommandWithParameters::GetParameterInfo|Obtient les types de tous les paramètres d'une commande spécifiée.<br /><br /> Pour les paramètres table, le *wType* champ de la structure DBPARAMINFO possède le type DBTYPE_TABLE. Le *ulParamSize* champ sera défini sur ~ 0 pour indiquer une longueur inconnue.|  
|ISSCommandWithParameters::GetParameterProperties|Obtient des informations de type supplémentaires pour les paramètres du type DBTYPE_TABLE.<br /><br /> Le consommateur Spécifie l’ordinal du paramètre dans le *iOrdinal* membre de la structure SSPARAMPROPS. Le consommateur peut demander des propriétés qui sont répertoriées sous ISSCommandWithParameters::SetParameterProperties dans le jeu de propriétés DBPROPSET_SQLSERVERPARAMETER.<br /><br /> Dans la mesure où le consommateur ne connaît pas le type de paramètre table, le fournisseur doit définir SSPROP_PARAM_TYPE_TYPENAME, SSPROP_PARAM_TYPE_SCHEMANAME et SSPROP_PARAM_TYPE_CATALOGNAME sur leurs valeurs correctes. Les propriétés restantes, SSPROP_PARAM_TABLE_DEFAULT_COLUMNS et SSPROP_PARAM_TABLE_COLUMN_SORT_ORDER, utilisent leurs valeurs par défaut. Une fois que le consommateur a découvert le nom de type de paramètre table, il utilise IOpenRowset::OpenRowset pour créer une instance de ce paramètre table, en spécifiant le nom du type de paramètre table. Pour plus d’informations, consultez [détection de Type de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-type-discovery.md).|  
|IRowsetInfo::GetProperties|Obtient les propriétés de l'ensemble de lignes de paramètre table. Le consommateur peut utiliser ces propriétés pour optimiser la configuration des liaisons.|  
|IColumnsRowset::GetColumnsRowset|Récupère les informations de métadonnées relatives une table [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour les paramètres table, cette même interface fournit des informations de métadonnées détaillées à propos de chaque colonne, notamment les suivantes :<br /><br /> DBCOLUMN_FLAGS indique la possibilité de valeur NULL via le bit DBCOLUMNFLAGS_ISNULLABLE.<br /><br /> DBCOLUMN_ISUNIQUE indique si la colonne est une colonne d'identité.<br /><br /> DBCOLUMN_COMPUTEMODE indique si la colonne est calculée.|  
|IAccessor::CreateAccessor|Pour lier un objet d’ensemble de lignes de paramètre table à un paramètre de commande, vous créez un accesseur avec son *wType* membre a la valeur DBTYPE_TABLE. La structure DBOBJECT contiendra IID_IRowset ou toute autre interface objet ensemble de lignes valide dans le *iid* membre. Les autres champs sont traités de la même façon que DBTYPE_IUNKNOWN.|  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge de Type de paramètre table OLE DB](../../relational-databases/native-client-ole-db-table-valued-parameters/ole-db-table-valued-parameter-type-support.md)   
 [Création de lignes de paramètre table](../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameter-rowset-creation.md)   
 [Utilisez la Table-Valued paramètres &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
