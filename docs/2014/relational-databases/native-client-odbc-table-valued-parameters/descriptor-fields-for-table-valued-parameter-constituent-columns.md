---
title: Champs de descripteur pour les colonnes constituantes des paramètres table | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields for constituent columns
ms.assetid: 944b3968-fd47-4847-98d6-b87e8ef2acdc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a31491b56e5b5cd700e744be2b7a84f10f1e0121
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63199939"
---
# <a name="descriptor-fields-for-table-valued-parameter-constituent-columns"></a>Champs de descripteur pour les colonnes constituantes des paramètres table
  Les champs de descripteur de paramètre table décrits dans cette section sont manipulés à l’aide de [SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md) et de [SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md) avec le descripteur du descripteur de paramètre d’implémentation (IPD).  
  
## <a name="remarks"></a>Notes  
 SQL_DESC_AUTO_UNIQUE_VALUE est utilisé pour les paramètres table ainsi que pour d'autres fonctionnalités.  
  
|Nom de l’attribut|Type|Description|  
|--------------------|----------|-----------------|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQLINTEGER|SQL_TRUE indique que cette colonne est une colonne d'identité.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]peut utiliser ces informations pour optimiser les performances, mais les applications ne sont pas obligées de le définir pour les colonnes d’identité.|  
  
 Les attributs suivants sont ajoutés à tous les types de paramètres du descripteur de paramètre d'application (APD, Application Parameter Descriptor) et du descripteur IPD :  
  
|Nom de l’attribut|Type|Description|  
|--------------------|----------|-----------------|  
|SQL_CA_SS_COLUMN_COMPUTED|SQLSMALLINT|SQL_TRUE indique que cette colonne est calculée.<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]peut utiliser ces informations pour optimiser les performances, mais les applications ne sont pas obligées de le définir pour les colonnes calculées.<br /><br /> Cet attribut est ignoré pour les liaisons qui ne sont pas des colonnes de paramètres table.|  
|SQL_CA_SS_COLUMN_IN_UNIQUE_KEY|SQLSMALLINT|SQL_TRUE indique qu'une colonne de paramètre table participe à une clé unique. Cela peut accroître les performances des requêtes. Cet attribut est ignoré pour les liaisons qui ne sont pas des colonnes de paramètres table.|  
|SQL_CA_SS_COLUMN_SORT_ORDER|SQLSMALLINT|Indique l'ordre de tri d'une colonne de paramètre table. Cela peut accroître les performances des requêtes. Cet attribut est ignoré pour les liaisons qui ne sont pas des colonnes de paramètres table. Les valeurs possibles sont les suivantes :<br /><br /> -SQL_SS_ASCENDING_ORDER<br />-SQL_SS_DESCENDING_ORDER<br />-SQL_SS_ORDER_UNSPECIFIED<br /><br /> Les valeurs différentes de SQL_SS_ASCENDING_ORDER et SQL_SS_DESCENDING_ORDER génèrent une erreur avec SQLSTATE HY024 et le message « Valeur d'attribut non valide » ; par ailleurs, elles sont traitées en tant que SQL_SS_ORDER_UNSPECIFIED, qui représente la valeur par défaut de cet attribut.|  
|SQL_CA_SS_COLUMN_SORT_ORDINAL|SQLSMALLINT|Indique l'ordinal d'une colonne de paramètre table dans le jeu des colonnes qui définissent l'ordre global d'un paramètre table. Cela peut accroître les performances des requêtes. Cet attribut est ignoré pour les liaisons qui ne sont pas des colonnes de paramètres table. Les ordinaux de tri commencent à 1. La valeur 0 (valeur par défaut) indique qu'une colonne de paramètre table n'a pas d'ordre de tri.|  
|SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE|SQLSMALLINT|Indique si toutes les lignes du paramètre table ont la valeur par défaut de cette colonne. Pour les paramètres table, il n'est pas possible de sélectionner la valeur par défaut ligne par ligne. Une valeur SQL_FALSE indique que les lignes ont des valeurs qui ne sont pas définies par défaut. Il s’agit de la valeur par défaut. Une valeur SQL_TRUE indique que cette colonne a des valeurs par défaut pour toutes les lignes.<br /><br /> Avec SQL_TRUE, aucune donnée n'est envoyée au serveur.<br /><br /> Ce champ peut également être utilisé avec des colonnes d'identité ou des colonnes calculées, si les valeurs de colonnes ne sont pas requises pour le traitement serveur.|  
  
 Ces attributs sont uniquement valides pour les colonnes de paramètres table. Ils sont ignorés pour les autres paramètres.  
  
 Si SQL_CA_SS_COL_HAS_DEFAULT_VALUE est défini pour une colonne de paramètre table, la valeur de SQL_DESC_DATA_PTR pour cette colonne doit être un pointeur Null. Sinon, SQLExecute ou SQLExecDirect retourne SQL_ERROR. Un enregistrement de diagnostic est généré avec SQLSTATE = 07S01 et le message « utilisation non valide du paramètre par défaut \<pour le paramètre p \<>, colonne c> \<», où p> est le \<paramètre ordinal et c> est le numéro de colonne.  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
