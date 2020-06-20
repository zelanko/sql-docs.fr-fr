---
title: Prise en charge des types de paramètre table OLE DB (propriétés) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (properties)
ms.assetid: b9c4e6ed-fe4f-4ef8-9bc8-784d80d44039
author: rothja
ms.author: jroth
ms.openlocfilehash: bda93e970e933f1db604fa529133e6d023b3337e
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85043335"
---
# <a name="ole-db-table-valued-parameter-type-support-properties"></a>Prise en charge du type de paramètre table OLE DB (Propriétés)
  Cette rubrique fournit des informations sur les propriétés et les jeux de propriétés OLE DB associés aux objets d'ensemble de lignes de paramètre table.  
  
## <a name="properties"></a>Propriétés  
 Voici la liste les propriétés exposées par la méthode IRowsetInfo::GetProperties sur des objets d’ensemble de lignes de paramètre table. Notez que toutes les propriétés de l'ensemble de lignes de paramètre table sont en lecture seule. Par conséquent, toute tentative de définition des propriétés via les méthodes IOpenRowset::OpenRowset ou ITableDefinitionWithConstraints::CreateTableWithConstraints sur leurs valeurs non définies par défaut génère une erreur et aucun objet n’est créé.  
  
 Les propriétés non implémentées dans l'objet d'ensemble de lignes de paramètre table n'apparaissent pas dans cette liste. Pour obtenir une liste complète des propriétés, consultez la documentation OLE DB dans Windows Data Access Components.  
  
|ID de propriété|Valeur|  
|-----------------|-----------|  
|DBPROP_ABORTPRESERVE|VARIANT_TRUE|  
|DBPROP_ACCESSORDER|DBPROPVAL_AO_RANDOM|  
|DBPROP_BLOCKINGSTORAGEOBJECTS|VARIANT_TRUE|  
|DBPROP_BOOKMARKS<br /><br /> DBPROP_LITERALBOOKMARKS|Lecture/Écriture : lecture seule<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Description : les signets ne sont pas autorisés dans les objets d'ensemble de lignes de paramètre table.|  
|DBPROP_BOOKMARKSKIPPED|VARIANT_FALSE|  
|DBPROP_BOOKMARKTYPE|DBPROPVAL_BMK_NUMERIC|  
|DBPROP_CANHOLDROWS|VARIANT_FALSE|  
|DBPROP_CHANGEINSERTEDROWS|VARIANT_TRUE|  
|DBPROP_COLUMNRESTRICT|VARIANT_FALSE|  
|DBPROP_COMMANDTIMEOUT|0|  
|DBPROP_COMMITPRESERVE|VARIANT_TRUE|  
|DBPROP_DEFERRED|VARIANT_FALSE|  
|DBPROP_DELAYSTORAGEOBJECTS|VARIANT_FALSE|  
|DBPROP_IAccessor<br /><br /> DBPROP_IColumnsInfo<br /><br /> DBPROP_IConvertType<br /><br /> DBPROP_IRowset<br /><br /> DBPROP_IRowsetInfo<br /><br /> DBPROP_IColumnsRowset|VARIANT_TRUE|  
|DBPROP_IConnectionPointContainer<br /><br /> DBPROP_IMultipleResults<br /><br /> DBPROP_IRowsetUpdate.<br /><br /> DBPROP_IRowsetIdentity<br /><br /> DBPROP_IRowsetLocate<br /><br /> DBPROP_IRowsetScroll<br /><br /> DBPROP_IRowsetResynch|VARIANT_FALSE|  
|DBPROP_IRowsetChange|VARIANT_TRUE<br /><br /> Remarque : L’objet d’ensemble de lignes de paramètre table prend en charge les interfaces IRowsetChange.<br /><br /> Un ensemble de lignes créé en utilisant DBPROP_IRowsetChange avec la valeur VARIANT_TRUE dévoile les comportements du mode de mise à jour immédiate.<br /><br /> Toutefois, si des colonnes BLOB sont liées en tant qu’objets ISequentialStream, le consommateur doit normalement les conserver pendant toute la durée de vie de l’objet d’ensemble de lignes de paramètre table.|  
|DBPROP_ISupportErrorInfo|VARIANT_TRUE|  
|DBPROP_ISequentialStream|VARIANT_TRUE|  
|DBPROP_IMMOBILEROWS|VARIANT_TRUE|  
|DBPROP_LITERALIDENTITY|VARIANT_TRUE|  
|DBPROP_LOCKMODE|DBPROPVAL_LM_NONE|  
|DBPROP_MAXOPENROWS|0|  
|DBPROP_MAXPENDINGROWS|0|  
|DBPROP_MAXROWS|0|  
|DBPROP_NOTIFICATIONPHASES|0|  
|DBPROP_NOTIFYCOLUMNSET DBPROP_NOTIFYROWDELETE DBPROP_NOTIFYROWFIRSTCHANGE DBPROP_NOTIFYROWINSERT DBPROP_NOTIFYROWRESYNCH DBPROP_NOTIFYROWSETRELEASE DBPROP_NOTIFYROWSETFETCH-POSITIONCHANGE DBPROP_NOTIFYROWUNDOCHANGE DBPROP_NOTIFYROWUNDODELETE DBPROP_NOTIFYROWUNDOINSERT DBPROP_NOTIFYROWUPDATE|0|  
|DBPROP_OTHERINSERT DBPROP_OTHERUPDATEDELETE|VARIANT_FALSE|  
|DBPROP_OWNINSERT<br /><br /> DBPROP_OWNUPDATEDELETE|VARIANT_TRUE|  
|DBPROP_QUICKRESTART|VARIANT_TRUE|  
|DBPROP_REENTRANTEVENTS|VARIANT_FALSE|  
|DBPROP_REMOVEDELETED|VARIANT_TRUE|  
|DBPROP_RETURNPENDINGINSERTS|VARIANT_TRUE|  
|DBPROP_ROWRESTRICT|VARIANT_FALSE|  
|DBPROP_ROWTHREADMODEL|DBPROPVAL_RT_FREETHREAD|  
|DBPROP_SERVERCURSOR|VARIANT_FALSE|  
|DBPROP_SERVERDATAONINSERT|VARIANT_FALSE|  
|DBPROP_STRONGIDENTITY|VARIANT_TRUE|  
|DBPROP_TRANSACTEDOBJECT|VARIANT_FALSE|  
|DBPROP_UNIQUEROWS|VARIANT_FALSE|  
|DBPROP_UPDATABILITY|DBPROPVAL_UP_CHANGE &#124; DBPROPVAL_UP_DELETE &#124; DBPROPVAL_UP_INSERT|  
  
## <a name="property-sets"></a>Jeux de propriétés  
 Les jeux de propriétés suivants prennent en charge les paramètres table.  
  
### <a name="dbpropset_sqlservercolumn"></a>DBPROPSET_SQLSERVERCOLUMN  
 Cette propriété est utilisée par le consommateur au cours du processus de création d'un objet d'ensemble de lignes de paramètre table en utilisant ITableDefinitionWithConstraints::CreateTableWithConstraints pour chaque colonne via la structure DBCOLUMNDESC (si nécessaire).  
  
|ID de propriété|Valeur de propriété|  
|-----------------|--------------------|  
|SSPROP_COL_COMPUTED|Lecture/écriture : lecture/écriture<br /><br /> Valeur par défaut : VARIANT_FALSE<br /><br /> Tapez : VT_BOOL<br /><br /> Description : cette propriété, si elle est définie sur VARIANT_TRUE, indique que la colonne est une colonne calculée. La valeur VARIANT_FALSE indique qu'il ne s'agit pas d'une colonne calculée.|  
  
### <a name="dbpropset_sqlserverparameter"></a>DBPROPSET_SQLSERVERPARAMETER  
 Ces propriétés sont lues par le consommateur lors de la détection des informations sur le type de paramètre table lors des appels à ISSCommandWithParameters::GetParameterProperties et sont définies par le consommateur au moment de définir les propriétés spécifiques relatives au paramètre table via ISSCommandWithParameters::SetParameterProperties.  
  
 Le tableau qui suit offre des descriptions détaillées de ces propriétés.  
  
|ID de propriété|Valeur de propriété|  
|-----------------|--------------------|  
|SSPROP_PARAM_TYPE_TYPENAME|Lecture/écriture : lecture/écriture<br /><br /> Valeur par défaut : VT_EMPTY<br /><br /> Tapez : VT_BSTR<br /><br /> Description : les consommateurs utilisent cette propriété pour se procurer ou définir le type de paramètre table.<br /><br /> Vous pouvez également utiliser cette propriété avec des types CLR définis par l'utilisateur.<br /><br /> Vous pouvez, si vous le souhaitez, la spécifier afin de préciser un nom de type de table pour un paramètre table (en cas d'utilisation d'une commande de syntaxe d'appel ODBC). Cette propriété est obligatoire pour les requêtes paramétrables SQL ad hoc.|  
|SSPROP_PARAM_TYPE_SCHEMANAME|Lecture/écriture : lecture/écriture<br /><br /> Valeur par défaut : VT_EMPTY<br /><br /> Tapez : VT_BSTR<br /><br /> Description : les consommateurs utilisent cette propriété pour se procurer ou définir le nom de schéma du type de paramètre table.<br /><br /> Vous pouvez également utiliser cette propriété avec des types CLR définis par l'utilisateur.|  
|SSPROP_PARAM_TYPE_CATALOGNAME|Lecture/écriture : lecture seule<br /><br /> Valeur par défaut : VT_EMPTY<br /><br /> Tapez : VT_BSTR<br /><br /> Description : les consommateurs utilisent cette propriété pour se procurer ou définir le nom de catalogue du type de paramètre table.<br /><br /> Vous pouvez également utiliser cette propriété avec des types CLR définis par l'utilisateur. La définition de cette propriété est une erreur ; les types de tables définis par l'utilisateur doivent figurer dans la même base de données que les paramètres table qui les utilisent.|  
|SSPROP_PARAM_TABLE_DEFAULT_COLUMNS|Lecture/écriture : lecture/écriture<br /><br /> Valeur par défaut : VT_EMPTY<br /><br /> Type : VT_UI2 &#124; VT_ARRAY<br /><br /> Description : les consommateurs utilisent cette propriété pour spécifier quelles colonnes dans l'ensemble de lignes seront traitées en tant que valeurs par défaut. Aucune valeur ne sera envoyée pour ces colonnes. Au moment d'extraire des données de l'objet d'ensemble de lignes du consommateur, le fournisseur n'exige aucune liaison pour ces colonnes.<br /><br /> Chaque élément du tableau doit désigner l'ordinal d'une colonne dans l'objet d'ensemble de lignes. Les ordinaux non valides génèrent des erreurs lors de l'exécution des commandes.|  
|SSPROP_PARAM_TABLE_COLUMN_ORDER|Lecture/écriture : lecture/écriture<br /><br /> Valeur par défaut : VT_EMPTY<br /><br /> Type : VT_UI2 &#124; VT_ARRAY<br /><br /> Description : cette propriété est utilisée par le consommateur pour indiquer au serveur l'ordre de tri des données des colonnes. Le fournisseur n'effectue aucune validation et part du principe que le consommateur agit conformément à la spécification fournie. Le serveur utilise cette propriété pour procéder à des optimisations.<br /><br /> Les informations d'ordre des colonnes pour chaque colonne sont représentées par une paire d'éléments dans le tableau. Le premier élément dans la paire correspond au numéro de la colonne. Le deuxième élément dans la paire sera 1 pour l'ordre croissant ou 2 pour l'ordre décroissant.|  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en charge du type de paramètre table OLE DB](ole-db-table-valued-parameter-type-support.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](table-valued-parameters-ole-db.md)  
  
  
