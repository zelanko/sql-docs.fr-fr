---
title: Sys.sp_rda_reconcile_columns (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-stretch
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6bae454caa630025bb4470dc69da7fa4a97f6307
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2018
---
# <a name="syssprdareconcilecolumns-transact-sql"></a>Sys.sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Rapproche les colonnes dans la table Azure distante les colonnes dans la la table SQL Server compatible Stretch.  
    
  **sp_rda_reconcile_columns** ajoute des colonnes à la table distante qui existent dans la table SQL Server compatible Stretch mais pas dans la table distante. Ces colonnes peuvent être des colonnes que vous avez accidentellement supprimé de la table distante. Toutefois, **sp_rda_reconcile_columns** ne supprime pas les colonnes de la table distante qui existent dans la table distante, mais pas dans la table SQL Server.
  
  > [!IMPORTANT]
  > Quand **sp_rda_reconcile_columns** recrée des colonnes que vous avez supprimées par inadvertance de la table distante, les données qui se trouvaient précédemment dans les colonnes supprimées ne sont pas restaurées.
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Arguments  
 @objname = '*@objname*'  
 Le nom de la table SQL Server compatible Stretch.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou >0 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Nécessite les autorisations db_owner.  
   
## <a name="remarks"></a>Notes   
 Si des colonnes comprises dans la table Azure distante n’existent plus dans la table SQL Server compatible Stretch, ces colonnes supplémentaires n’empêchent pas Stretch Database de fonctionner normalement. Vous pouvez éventuellement supprimer manuellement les colonnes supplémentaires.  
  
## <a name="example"></a> Exemple  
 Pour rapprocher les colonnes dans la table Azure distante, exécutez l’instruction suivante.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
