---
title: sp_help_fulltext_tables_cursor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_tables_cursor
- sp_help_fulltext_tables_cursor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_tables_cursor
ms.assetid: 155791eb-8832-4596-8487-7fc70dfba5b9
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d43903af7a4626c7d9645e1b750696b15cc692ec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62660453"
---
# <a name="sphelpfulltexttablescursor-transact-sql"></a>sp_help_fulltext_tables_cursor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Utilise un curseur pour retourner une liste des tables inscrites pour l'indexation de texte intégral.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez la nouvelle **sys.fulltext_indexes** vue de catalogue à la place. Pour plus d’informations, consultez [sys.fulltext_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_fulltext_tables_cursor [ @cursor_return = ] @cursor_variable OUTPUT   
     [ , [ @fulltext_catalog_name = ] 'fulltext_catalog_name' ]   
     [ , [ @table_name = ] 'table_name' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @cursor_return = ] @cursor_variable OUTPUT` Variable de sortie de type **curseur**. Le curseur est en lecture seule, dynamique et permet les défilements.  
  
`[ @fulltext_catalog_name = ] 'fulltext_catalog_name'` Est le nom du catalogue de texte intégral. *fulltext_catalog_name* est **sysname**, avec NULL comme valeur par défaut. Si *fulltext_catalog_name* est omis ou a la valeur NULL, toutes les tables indexées en texte intégral associés à la base de données sont retournées. Si *fulltext_catalog_name* est spécifié, mais *table_name* est omis ou a la valeur NULL, les informations d’index de recherche en texte intégral sont récupérées pour chaque table indexée en texte intégral associé à ce catalogue. Si les deux *fulltext_catalog_name* et *table_name* sont spécifiés, une ligne est retournée si *table_name* associé *fulltext_catalog_name*; Sinon, une erreur est générée.  
  
`[ @table_name = ] 'table_name'` Est le nom de table d’une ou deux parties pour laquelle les métadonnées de recherche en texte intégral sont demandées. *table_name* est **nvarchar (517)**, avec NULL comme valeur par défaut. Si seuls *table_name* est spécifié, la ligne concernant *table_name* est retourné.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (succès) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_OWNER**|**sysname**|Propriétaire de la table. Nom de l'utilisateur de la base de données qui a créé la table.|  
|**TABLE_NAME**|**sysname**|Nom de la table.|  
|**FULLTEXT_KEY_INDEX_NAME**|**sysname**|Index imposant la contrainte UNIQUE dans la colonne désignée comme colonne clé unique.|  
|**FULLTEXT_KEY_COLID**|**Int**|ID de colonne de l'index unique identifié par FULLTEXT_KEY_NAME.|  
|**FULLTEXT_INDEX_ACTIVE**|**Int**|Indique si les colonnes de cette table marquées pour l'indexation de texte intégral peuvent faire l'objet de requêtes :<br /><br /> 0 = Inactif<br /><br /> 1 = Actif|  
|**FULLTEXT_CATALOG_NAME**|**sysname**|Catalogue de texte intégral contenant les données d'index sur le texte intégral.|  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d'exécution reviennent par défaut aux membres du rôle **public** .  
  
## <a name="examples"></a>Exemples  
 Cet exemple retourne le nom des tables indexées sur le texte intégral associées au catalogue de texte intégral `Cat_Desc`.  
  
```  
USE AdventureWorks2012;  
GO  
DECLARE @mycursor CURSOR;  
EXEC sp_help_fulltext_tables_cursor @mycursor OUTPUT, 'Cat_Desc';  
FETCH NEXT FROM @mycursor;  
WHILE (@@FETCH_STATUS <> -1)  
   BEGIN  
      FETCH NEXT FROM @mycursor;  
   END;  
CLOSE @mycursor;  
DEALLOCATE @mycursor;  
GO   
```  
  
## <a name="see-also"></a>Voir aussi  
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [OBJECTPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/objectproperty-transact-sql.md)   
 [sp_fulltext_table &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-fulltext-table-transact-sql.md)   
 [sp_help_fulltext_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-fulltext-tables-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
