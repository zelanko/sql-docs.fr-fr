---
title: sys. sp_rda_reconcile_columns (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_reconcile_columns
- sys.sp_rda_reconcile_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_reconcile_columns stored procedure
ms.assetid: 60d9cc4e-1828-450b-9d88-5b8485800d73
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7ad2fd6c51f5b5463e4e4c10745b2ff245bd691d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083671"
---
# <a name="syssp_rda_reconcile_columns-transact-sql"></a>sys. sp_rda_reconcile_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Rapproche les colonnes de la table Azure distante des colonnes de la table de SQL Server avec Stretch.  
    
  **sp_rda_reconcile_columns** ajoute des colonnes à la table distante qui existent dans la table de SQL Server avec Stretch, mais pas dans la table distante. Ces colonnes peuvent être des colonnes que vous avez accidentellement supprimées de la table distante. Toutefois, **sp_rda_reconcile_columns** ne supprime pas les colonnes de la table distante qui existent dans la table distante, mais pas dans la table SQL Server.
  
  > [!IMPORTANT]
  > Quand **sp_rda_reconcile_columns** recrée des colonnes que vous avez supprimées par inadvertance de la table distante, les données qui se trouvaient précédemment dans les colonnes supprimées ne sont pas restaurées.
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
   
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_rda_reconcile_columns @objname = '@objname'  
  
```  
  
## <a name="arguments"></a>Arguments  
 \@objname = '*\@objname*'  
 Nom de la table de SQL Server prenant en charge Stretch.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (succès) ou >0 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Requiert db_owner autorisations.  
   
## <a name="remarks"></a>Notes  
 Si des colonnes comprises dans la table Azure distante n’existent plus dans la table SQL Server compatible Stretch, ces colonnes supplémentaires n’empêchent pas Stretch Database de fonctionner normalement. Vous pouvez éventuellement supprimer manuellement les colonnes supplémentaires.  
  
## <a name="example"></a>Exemple  
 Pour rapprocher les colonnes de la table Azure distante, exécutez l’instruction suivante.  
  
```sql  
EXEC sp_rda_reconcile_columns @objname = N'StretchEnabledTableName';  
```  
  
  
