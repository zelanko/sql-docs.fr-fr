---
title: sp_kill_filestream_non_transacted_handles (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_kill_filestream_non_transacted_handles_TSQL
- sp_kill_filestream_non_transacted_handles
dev_langs:
- TSQL
helpviewer_keywords:
- sp_kill_filestream_non_transacted_handles
ms.assetid: 7188353e-ab29-49a0-8f25-7fb8ab122589
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98c986c26c8d0d0cc6e2b8ff3573f0a20d938975
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942264"
---
# <a name="spkillfilestreamnontransactedhandles-transact-sql"></a>sp_kill_filestream_non_transacted_handles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ferme des descripteurs de fichiers non transactionnels aux données de FileTable.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
sp_kill_filestream_non_transacted_handles [[ @table_name = ] 'table_name', [[ @handle_id = ] @handle_id]]  
```  
  
## <a name="arguments"></a>Arguments  
 *table_name*  
 Nom de la table dans laquelle fermer des descripteurs non transactionnels.  
  
 Vous pouvez transmettre *table_name* sans *handle_id* pour fermer tous les descripteurs non transactionnels d’ouverts pour le FileTable.  
  
 Vous pouvez passer NULL pour la valeur de *table_name* pour fermer tous les descripteurs non transactionnels d’ouverts pour tous les FileTables dans la base de données actuelle. NULL est la valeur par défaut.  
  
 *handle_id*  
 ID facultatif du descripteur individuel à fermer. Vous pouvez obtenir le *handle_id* à partir de la [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md) vue de gestion dynamique. Chaque ID est unique dans une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous spécifiez *handle_id*, vous devez également fournir une valeur pour *table_name*.  
  
 Vous pouvez passer NULL pour la valeur de *handle_id* pour fermer tous les descripteurs non transactionnels d’ouverts pour le FileTable spécifié par *table_name*. NULL est la valeur par défaut.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucune.  
  
## <a name="general-remarks"></a>Remarques d'ordre général  
 Le *handle_id* requis par **sp_kill_filestream_non_transacted_handles** n’est pas lié à session_id ni à l’unité de travail qui est utilisé dans d’autres **kill** commandes.  
  
 Pour plus d’informations, consultez [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md).  
  
## <a name="metadata"></a>Métadonnées  
 Pour plus d’informations sur les descripteurs de fichiers non transactionnels ouverts, interrogez la vue de gestion dynamique [sys.dm_filestream_non_transacted_handles &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md).  
  
## <a name="security"></a>Sécurité  
  
### <a name="permissions"></a>Autorisations  
 Vous devez avoir **VIEW DATABASE STATE** autorisation pour obtenir des handles de fichier à partir de la **sys.dm_FILESTREAM_non_transacted_handles** vue de gestion dynamique et d’exécuter **sp_kill_filestream_non_ transacted_handles**.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants montrent comment appeler **sp_kill_filestream_non_transacted_handles** pour fermer des descripteurs de fichiers non transactionnels pour les données FileTable.  
  
```sql  
-- Close all open handles in the current database.  
sp_kill_filestream_non_transacted_handles  
  
-- Close all open handles in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable'  
  
-- Close a specific handle in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = 'myFileTable', @handle_id = 0xFFFAAADD  
```  
  
 L’exemple suivant montre comment utiliser un script pour obtenir un *handle_id* et fermez-le.  
  
```sql  
DECLARE @handle_id varbinary(16);  
DECLARE @table_name sysname;  
  
SELECT TOP 1 @handle_id = handle_id, @table_name = Object_name(table_id)  
FROM sys.dm_FILESTREAM_non_transacted_handles;  
  
EXEC sp_kill_filestream_non_transacted_handles @dbname, @table_name, @handle_id;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Gérer des FileTables](../../relational-databases/blob/manage-filetables.md)  
 [FileStream et les vues de gestion dynamique FileTable (Transact-SQL)](../system-dynamic-management-views/filestream-and-filetable-dynamic-management-views-transact-sql.md)
 <br>[FileStream et les affichages catalogue FileTable (Transact-SQL)](../system-catalog-views/filestream-and-filetable-catalog-views-transact-sql.md)
 <br>[sp_filestream_force_garbage_collection (Transact-SQL)](filestream-and-filetable-sp-filestream-force-garbage-collection.md)
  
