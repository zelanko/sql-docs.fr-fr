---
title: Champ descripteur pour paramètre de table-évalué
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields for constituent columns
ms.assetid: 944b3968-fd47-4847-98d6-b87e8ef2acdc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 08074ad57ca4f0e4f7c2c56d9eca595baf595b5f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297851"
---
# <a name="descriptor-fields-for-table-valued-parameter-constituent-columns"></a>Champs de descripteur pour les colonnes constituantes des paramètres table
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les champs descripteur de paramètres de valeur de table décrits dans cette section sont manipulés en utilisant [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md) et [SQLSetDescField](../../relational-databases/native-client-odbc-api/sqlsetdescfield.md) avec la poignée pour le descripteur de paramètre de mise en œuvre (IPD).  
  
## <a name="remarks"></a>Notes  
 SQL_DESC_AUTO_UNIQUE_VALUE est utilisé pour les paramètres table ainsi que pour d'autres fonctionnalités.  
  
|Nom de l’attribut|Type|Description|  
|--------------------|----------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|SQL_TRUE indique que cette colonne est une colonne d'identité.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]peuvent utiliser ces informations pour optimiser les performances, mais les applications ne sont pas nécessaires pour les définir pour les colonnes d’identité.|  
||||

 Les attributs suivants sont ajoutés à tous les types de paramètres du descripteur de paramètre d'application (APD, Application Parameter Descriptor) et du descripteur IPD :  
  
|Nom de l’attribut|Type|Description|  
|--------------------|----------|-----------------|  
|SQL_CA_SS_COLUMN_COMPUTED|SQLSMALLINT|SQL_TRUE indique que cette colonne est calculée.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]peuvent utiliser ces informations pour optimiser les performances, mais les applications ne sont pas nécessaires pour les définir pour les colonnes calculées.<br /><br /> Cet attribut est ignoré pour les liaisons qui ne sont pas des colonnes de paramètres table.|  
|SQL_CA_SS_COLUMN_IN_UNIQUE_KEY|SQLSMALLINT|SQL_TRUE indique qu'une colonne de paramètre table participe à une clé unique. Cela peut accroître les performances des requêtes. Cet attribut est ignoré pour les liaisons qui ne sont pas des colonnes de paramètres table.|  
|SQL_CA_SS_COLUMN_SORT_ORDER|SQLSMALLINT|Indique l'ordre de tri d'une colonne de paramètre table. Cela peut accroître les performances des requêtes. Cet attribut est ignoré pour les liaisons qui ne sont pas des colonnes de paramètres table. Les valeurs possibles sont les suivantes : <br />**SQL_SS_ASCENDING_ORDER**<br />**SQL_SS_DESCENDING_ORDER**<br />**SQL_SS_ORDER_UNSPECIFIED**<br /><br /> Des valeurs autres que **SQL_SS_ASCENDING_ORDER** et **SQL_SS_DESCENDING_ORDER** génèrent une erreur avec **SQLSTATE HY024** et le message 'Valeur d’attribut invalide' et sont traitées comme **SQL_SS_ORDER_UNSPECIFIED**, ce qui est la valeur par défaut de cet attribut.|  
|SQL_CA_SS_COLUMN_SORT_ORDINAL|SQLSMALLINT|Indique l'ordinal d'une colonne de paramètre table dans le jeu des colonnes qui définissent l'ordre global d'un paramètre table. Cela peut accroître les performances des requêtes. Cet attribut est ignoré pour les liaisons qui ne sont pas des colonnes de paramètres table. Les ordinaux de tri commencent à 1. La valeur 0 (valeur par défaut) indique qu'une colonne de paramètre table n'a pas d'ordre de tri.|  
|SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE|SQLSMALLINT|Indique si toutes les lignes du paramètre table ont la valeur par défaut de cette colonne. Pour les paramètres table, il n'est pas possible de sélectionner la valeur par défaut ligne par ligne. Une valeur SQL_FALSE indique que les lignes ont des valeurs qui ne sont pas définies par défaut. Il s’agit de la valeur par défaut. Une valeur SQL_TRUE indique que cette colonne a des valeurs par défaut pour toutes les lignes.<br /><br /> Avec SQL_TRUE, aucune donnée n'est envoyée au serveur.<br /><br /> Ce champ peut également être utilisé avec des colonnes d'identité ou des colonnes calculées, si les valeurs de colonnes ne sont pas requises pour le traitement serveur.|  
||||

 Ces attributs sont uniquement valides pour les colonnes de paramètres table. Ils sont ignorés pour les autres paramètres.  
  
 Si SQL_CA_SS_COL_HAS_DEFAULT_VALUE est défini pour une colonne de paramètre table, la valeur de SQL_DESC_DATA_PTR pour cette colonne doit être un pointeur Null. Dans le cas contraire, SQLExecute ou SQLExecDirect retourneront SQL_ERROR. Un enregistrement diagnostique sera généré avec SQLSTATE-07S01 et le message \<"Utilisation invalide \<du paramètre \<par défaut pour le paramètre p \<>, colonne c>", où p> est le paramètre ordinaire et c> est la colonne ordinaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres évalués par la table &#40;&#41;ODBC](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
  
