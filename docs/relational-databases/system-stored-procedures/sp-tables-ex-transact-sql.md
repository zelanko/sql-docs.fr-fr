---
title: sp_tables_ex (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_tables_ex
- sp_tables_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables_ex
ms.assetid: 33755c33-7e1e-4ef7-af14-a9cebb1e2ed4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f034b1247f9865b83077ed11f644d6fdbbc4cecd
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/18/2018
ms.locfileid: "53589384"
---
# <a name="sptablesex-transact-sql"></a>sp_tables_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations de table sur les tables provenant du serveur lié spécifié.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_tables_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]  
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @table_type = ] 'table_type' ]   
     [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@table_server=** ] **'**_serveur_de_la_table_**'**  
 Nom du serveur lié pour lequel sont retournées les informations de table. *serveur_de_la_table* est **sysname**, sans valeur par défaut.  
  
 [ **,** [  **@table_name=** ] **'**_table_name_**'**]  
 Nom de la table dans laquelle sont retournées les informations de type de données. *table_name*est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@table_schema=** ] **'**_table_schema_**'**]  
 Schéma de la table. *table_schema*est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@table_catalog=** ] **'**_table_catalog_**'**  
 Est le nom de la base de données dans laquelle le texte spécifié *table_name* réside. *table_catalog* est **sysname**, avec NULL comme valeur par défaut.  
  
 [  **@table_type=** ] **'**_table_type_**'**  
 Type de la table à retourner. *TABLE_TYPE* est **sysname**, avec NULL comme valeur par défaut et peut avoir l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**ALIAS**|Nom d'un alias.|  
|**TEMPORAIRE GLOBALE**|Nom d'une table temporaire disponible au niveau du système.|  
|**FICHIER TEMPORAIRE LOCAL**|Nom d'une table temporaire disponible uniquement au niveau du travail en cours.|  
|**SYNONYM**|Nom d'un synonyme.|  
|**(TABLE SYSTÈME)**|Nom d'une table système.|  
|**VUE SYSTÈME**|Nom d'une vue système.|  
|**TABLE**|Nom d'une table utilisateur.|  
|**VIEW**|Nom d'une vue.|  
  
 [  **@fUsePattern=** ] **'**_fUsePattern_**'**  
 Détermine si les caractères **_**, **%**, **[**, et **]** sont interprétés comme des caractères génériques. Les valeurs valides sont 0 (critères spéciaux désactivés) et 1 (critères spéciaux activés). *fUsePattern* est **bits**, avec 1 comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 None  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|Nom du qualificateur de table. Divers produits SGBD prennent en charge la dénomination en trois parties pour les tables (_qualificateur_**.** _propriétaire_**.** _nom_). Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette colonne représente le nom de la base de données. Dans d’autres produits, elle représente le nom du serveur de l’environnement de base de données de la table. Ce champ peut contenir la valeur NULL.|  
|**TABLE_SCHEM**|**sysname**|Nom du propriétaire de la table. Dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], cette colonne représente le nom de l'utilisateur de la base de données qui a créé la table. Ce champ retourne toujours une valeur.|  
|**TABLE_NAME**|**sysname**|Nom de la table. Ce champ retourne toujours une valeur.|  
|**TABLE_TYPE**|**varchar(32)**|Table, table système ou vue.|  
|**REMARQUES**|**varchar(254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne retourne pas de valeur pour cette colonne.|  
  
## <a name="remarks"></a>Notes  
 **sp_tables_ex** est exécuté en interrogeant l’ensemble de lignes de TABLES de la **IDBSchemaRowset** interface du fournisseur OLE DB correspondant à *serveur_de_la_table*. Le *table_name*, *table_schema*, *table_catalog*, et *colonne* paramètres sont passés à cette interface pour limiter les lignes retourné.  
  
 **sp_tables_ex** retourne un résultat vide si le fournisseur OLE DB du serveur lié spécifié ne prend pas en charge l’ensemble de lignes de TABLES de la **IDBSchemaRowset** interface.  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l'autorisation SELECT sur le schéma.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des informations sur les tables contenues dans le schéma `HumanResources` de la base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], sur le serveur lié `LONDON2`.  
  
```  
EXEC sp_tables_ex @table_server = 'LONDON2',   
@table_catalog = 'AdventureWorks2012',   
@table_schema = 'HumanResources',   
@table_type = 'TABLE';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Distribué des procédures stockées de requêtes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_columns_ex &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_table_privileges &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
