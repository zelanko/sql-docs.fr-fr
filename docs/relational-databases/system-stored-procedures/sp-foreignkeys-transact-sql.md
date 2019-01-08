---
title: sp_foreignkeys (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_foreignkeys_TSQL
- sp_foreignkeys
dev_langs:
- TSQL
helpviewer_keywords:
- sp_foreignkeys
ms.assetid: 935fe385-19ff-41a4-8d0b-30618966991d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b0fc8552157e9864ed45306ec268fefb4eec87bf
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589943"
---
# <a name="spforeignkeys-transact-sql"></a>sp_foreignkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne les clés étrangères faisant référence aux clés primaires de la table du serveur lié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_foreignkeys [ @table_server = ] 'table_server'   
     [ , [ @pktab_name = ] 'pktab_name' ]   
     [ , [ @pktab_schema = ] 'pktab_schema' ]   
     [ , [ @pktab_catalog = ] 'pktab_catalog' ]   
     [ , [ @fktab_name = ] 'fktab_name' ]   
     [ , [ @fktab_schema = ] 'fktab_schema' ]   
     [ , [ @fktab_catalog = ] 'fktab_catalog' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@table_server =** ] **'**_serveur_de_la_table_**'**  
 Nom du serveur lié pour lequel sont retournées les informations de table. *serveur_de_la_table* est **sysname**, sans valeur par défaut.  
  
 [  **@pktab_name =** ] **'**_l’argument nom_table_pk_**'**  
 Nom de la table contenant une clé primaire. *l’argument nom_table_pk* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@pktab_schema =** ] **'**_schéma_table_pk_**'**  
 Nom du schéma contenant une clé primaire. *schéma_table_pk*est **sysname**, avec NULL comme valeur par défaut. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il contient le nom du propriétaire.  
  
 [  **@pktab_catalog =** ] **'**_l’argument catalogue_table_pk_**'**  
 Nom du catalogue contenant une clé primaire. *l’argument catalogue_table_pk*est **sysname**, avec NULL comme valeur par défaut. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], il contient le nom de la base de données.  
  
 [  **@fktab_name =** ] **'**_l’argument nom_table_fk_**'**  
 Nom de la table contenant une clé étrangère. *l’argument nom_table_fk*est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@fktab_schema =** ] **'**_l’argument schema_table_fk_**'**  
 Nom du schéma contenant une clé étrangère. *l’argument schema_table_fk*est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@fktab_catalog =** ] **'**_l’argument catalogue_table_fk_**'**  
 Nom du catalogue contenant une clé étrangère. *l’argument catalogue_table_fk*est **sysname**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
 Divers produits SGBD prennent en charge la dénomination en trois parties pour les tables (_catalogue_**.** _schéma_**.** _table_), qui est représenté dans le jeu de résultats.  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**PKTABLE_CAT**|**sysname**|Catalogue de la table contenant la clé primaire.|  
|**PKTABLE_SCHEM**|**sysname**|Schéma de la table contenant la clé primaire.|  
|**NOM_DE_LA_PKTABLE**|**sysname**|Nom de la table (contenant la clé primaire). Ce champ retourne toujours une valeur.|  
|**PKCOLUMN_NAME**|**sysname**|Nom de la colonne de clé primaire ou de colonnes, pour chaque colonne de la **TABLE_NAME** retourné. Ce champ retourne toujours une valeur.|  
|**FKTABLE_CAT**|**sysname**|Catalogue de la table contenant la clé étrangère.|  
|**FKTABLE_SCHEM**|**sysname**|Schéma de la table contenant la clé étrangère.|  
|**FKTABLE_NAME**|**sysname**|Nom de la table (contenant une clé étrangère). Ce champ retourne toujours une valeur.|  
|**FKCOLUMN_NAME**|**sysname**|Nom des colonnes de clé étrangère, pour chacune des colonnes de la table TABLE_NAME retournées. Ce champ retourne toujours une valeur.|  
|**KEY_SEQ**|**smallint**|Numéro de séquence de la colonne dans une clé primaire multicolonne. Ce champ retourne toujours une valeur.|  
|**UPDATE_RULE**|**smallint**|Action appliquée à la clé étrangère lorsque l'opération SQL est une mise à jour. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne 0, 1 ou 2 pour ces colonnes :<br /><br /> 0=Modifications de type CASCADE apportées à la clé étrangère.<br /><br /> 1=Modifications de type NO ACTION en présence de clé étrangère.<br /><br /> 2=SET_NULL ; affectation de NULL à la clé étrangère.|  
|**DELETE_RULE**|**smallint**|Action appliquée à la clé étrangère lorsque l'opération SQL est une suppression. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne 0, 1 ou 2 pour ces colonnes :<br /><br /> 0=Modifications de type CASCADE apportées à la clé étrangère.<br /><br /> 1=Modifications de type NO ACTION en présence de clé étrangère.<br /><br /> 2=SET_NULL ; affectation de NULL à la clé étrangère.|  
|**FK_NAME**|**sysname**|Identificateur de clé étrangère. NULL si non applicable à la source de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne le nom de la contrainte FOREIGN KEY.|  
|**PK_NAME**|**sysname**|Identificateur de clé primaire. NULL si non applicable à la source de données. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne le nom de la contrainte PRIMARY KEY.|  
|**DEFERRABILITY**|**smallint**|Indique si la vérification des contraintes peut être différée.|  
  
 Dans le jeu de résultats, les colonnes FK_NAME et PK_NAME retournent toujours une valeur NULL.  
  
## <a name="remarks"></a>Notes  
 **sp_foreignkeys** interroge l’ensemble de lignes Foreign_Keys contenu dans le **IDBSchemaRowset** interface du fournisseur OLE DB qui correspond à *serveur_de_la_table*. Le *table_name*, *table_schema*, *table_catalog*, et *colonne* paramètres sont passés à cette interface pour limiter les lignes retourné.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation SELECT sur le schéma.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne les informations de clé étrangère relatives à la table `Department` de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] située sur le serveur lié `Seattle1`.  
  
```  
EXEC sp_foreignkeys @table_server = N'Seattle1',   
   @pktab_name = N'Department',   
   @pktab_catalog = N'AdventureWorks2012';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_primarykeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-primarykeys-transact-sql.md)   
 [sp_tables_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-ex-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
