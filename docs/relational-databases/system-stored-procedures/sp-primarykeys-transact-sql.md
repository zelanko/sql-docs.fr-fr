---
title: sp_primarykeys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_primarykeys_TSQL
- sp_primarykeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_primarykeys
ms.assetid: 0f76dd31-5b7b-4209-9e2e-b9ed5cac164d
author: stevestein
ms.author: sstein
ms.openlocfilehash: ccae0385ef8c9305f4972ff6dcbd7a7960200370
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68056313"
---
# <a name="sp_primarykeys-transact-sql"></a>sp_primarykeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les colonnes de clés primaires, une ligne par colonne clé, pour la table distante spécifiée.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_primarykeys [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]   
     [ , [ @table_catalog = ] 'table_catalog' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @table_server = ] 'table_server'_`Nom du serveur lié à partir duquel les informations de clé primaire doivent être retournées. *table_server* est de **type sysname**, sans valeur par défaut.  
  
`[ @table_name = ] 'table_name'`Nom de la table pour laquelle les informations de clé primaire sont fournies. *table_name*est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @table_schema = ] 'table_schema'`Est le schéma de la table. *TABLE_SCHEMA* est de **type sysname**, avec NULL comme valeur par défaut. Dans l'environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ceci correspond au propriétaire de la table.  
  
`[ @table_catalog = ] 'table_catalog'`Nom du catalogue dans lequel le *table_name* spécifié réside. Dans l'environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cet argument correspond au nom de la base de données. *TABLE_CATALOG* est de **type sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Catalogue de la table|  
|**TABLE_SCHEM**|**sysname**|Schéma de la table|  
|**TABLE_NAME**|**sysname**|Nom de la table.|  
|**COLUMN_NAME**|**sysname**|Nom de la colonne.|  
|**KEY_SEQ**|**int**|Numéro de séquence de la colonne dans une clé primaire multicolonne.|  
|**PK_NAME**|**sysname**|Identificateur de clé primaire. Retourne NULL s'il n'est pas applicable à la source de données.|  
  
## <a name="remarks"></a>Notes  
 **sp_primarykeys** est exécuté en interrogeant l’ensemble de lignes PRIMARY_KEYS de l’interface **IDBSchemaRowset** du fournisseur OLE DB correspondant à *table_server*. Les paramètres *table_name*, *TABLE_SCHEMA*, *TABLE_CATALOG*et *Column* sont passés à cette interface pour limiter les lignes retournées.  
  
 **sp_primarykeys** retourne un jeu de résultats vide si le fournisseur de OLE DB du serveur lié spécifié ne prend pas en charge l’ensemble de lignes PRIMARY_KEYS de l’interface **IDBSchemaRowset** .  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation SELECT sur le schéma.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des colonnes de clé primaires du serveur `LONDON1` pour la table `HumanResources.JobCandidate` dans la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
EXEC sp_primarykeys @table_server = N'LONDON1',   
   @table_name = N'JobCandidate',  
   @table_catalog = N'AdventureWorks2012',   
   @table_schema = N'HumanResources';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de requêtes distribuées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
