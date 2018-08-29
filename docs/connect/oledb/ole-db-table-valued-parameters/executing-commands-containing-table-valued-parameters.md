---
title: Exécution de commandes contenant des paramètres table | Microsoft Docs
description: Exécution de commandes contenant des paramètres table
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-table-valued-parameters
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, executing commands containing
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: e2d6df92bf4ddc101e1df0607ca745c7ec232485
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43022338"
---
# <a name="executing-commands-containing-table-valued-parameters"></a>Exécution de commandes contenant des paramètres table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Deux phases sont nécessaires pour l’exécution d’une commande contenant des paramètres table :  
  
1.  Spécifier les types de paramètres.  
  
2.  Lier les données des paramètres.  
  
## <a name="table-valued-parameter-specification"></a>Spécification des paramètres table  
 Le consommateur peut spécifier le type du paramètre table. Ces informations incluent le nom du type du paramètre table. Elles incluent aussi le nom du schéma et indiquent si le type de table défini par l’utilisateur pour le paramètre table ne figure pas dans l’actuel schéma par défaut de la connexion. En fonction de la prise en charge du serveur, le consommateur peut également spécifier des informations de métadonnées facultatives, telles que la classification des colonnes, et indiquer que toutes les lignes de colonnes particulières ont des valeurs par défaut.  
  
 Pour spécifier un paramètre table, le consommateur appelle ISSCommandWithParamter::SetParameterInfo et appelle éventuellement ISSCommandWithParameters::SetParameterProperties. Pour un paramètre table, le champ *pwszDataSourceType* de la structure DBPARAMBINDINFO a la valeur DBTYPE_TABLE. Le champ *ulParamSize* est défini avec la valeur ~0 pour indiquer que la longueur est inconnue. Propriétés particulières des paramètres table, telles que le nom de schéma, un nom de type, ordre des colonnes et les colonnes par défaut, peuvent être définies via ISSCommandWithParameters::SetParameterProperties.  
  
## <a name="table-valued-parameter-binding"></a>Liaison de paramètre table  
 Un paramètre table peut être n'importe quel objet d'ensemble de lignes. Le fournisseur effectue la lecture à partir de cet objet tout en envoyant les paramètres table au serveur pendant l'exécution.  
  
 Pour lier le paramètre table, le consommateur appelle IAccessor::CreateAccessor. Le champ *wType* de la structure DBBINDING du paramètre table est défini avec la valeur DBTYPE_TABLE. Le membre *pObject* de la structure DBBINDING n’est pas Null et le membre *iid* de *pObject* est défini avec la valeur IID_IRowset ou autre interface d’objets d’ensemble de lignes de paramètres table. Les champs restants de la structure DBBINDING doivent être définis de la même façon qu’ils le sont pour les BLOB transmis en continu.  
  
 Dans les liaisons du paramètre table et de l'objet d'ensemble de lignes associé à un paramètre table, les restrictions suivantes s'appliquent :  
  
-   Les seules valeurs d'état autorisées pour les données de colonnes d'ensembles de lignes de paramètres table sont DBSTATUS_S_ISNULL et DBSTATUS_S_OK. DBSTATUS_S_DEFAULT se traduit par un échec et la valeur d'état liée est DBSTATUS_E_BADSTATUS.  
  
-   Un paramètre table peut être marqué avec l'état DBSTATUS_S_DEFAULT. Les seules valeurs valides sont DBSTATUS_S_DEFAULT et DBSTATUS_S_OK. Quand l'état est défini sur DBSTATUS_S_DEFAULT, la valeur du paramètre table correspond à une table vide.  
  
-   Les colonnes en lecture seule des paramètres table (colonnes d'identité ou colonnes calculées) doivent être marquées comme valeur par défaut à l'aide de la propriété SSPROP_PARAM_TABLE_DEFAULT_COLUMNS. Les colonnes qui ont une valeur par défaut doivent aussi être marquées comme valeur par défaut via la propriété SSPROP_PARAM_TABLE_DEFAULT_COLUMNS pour autoriser l'utilisation de la valeur par défaut pour les valeurs de données de la colonne d'un paramètre table particulier. Le fournisseur ignore les valeurs de données liées pour les colonnes marquées par défaut.  
  
-   Les données sont envoyées au serveur pour les colonnes avec DBPROP_COL_AUTOINCREMENT ou SSPROP_COL_COMPUTED, à moins que SSPROP_PARAM_TABLE_DEFAULT ne soit également défini.  
  
## <a name="see-also"></a> Voir aussi  
 [Paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [Utiliser les paramètres table &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
