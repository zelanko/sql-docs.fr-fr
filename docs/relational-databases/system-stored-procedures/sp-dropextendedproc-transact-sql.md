---
title: sp_dropextendedproc (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropextendedproc
- sp_dropextendedproc_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropextendedproc
ms.assetid: dd93af2c-1b7d-4e39-af23-2d21d270a381
author: stevestein
ms.author: sstein
ms.openlocfilehash: b12ebcfb662db9740efdf918f0857b94144e0ceb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68054298"
---
# <a name="spdropextendedproc-transact-sql"></a>sp_dropextendedproc (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une procédure stockée étendue.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Utilisez l’ [intégration CLR](../../relational-databases/clr-integration/common-language-runtime-integration-overview.md) à la place.  
  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
sp_dropextendedproc [ @functname = ] 'procedure'   
```  
  
## <a name="arguments"></a>Arguments  
`[ @functname = ] 'procedure'` Est le nom de la procédure stockée étendue à supprimer. *procédure* est **nvarchar (517)** , sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 L’exécution de **sp_dropextendedproc** supprime le nom de la procédure stockée étendue définie par l’utilisateur à partir de la [sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) vue de catalogue et supprime l’entrée à partir de la [sys.extended_procedures ](../../relational-databases/system-catalog-views/sys-extended-procedures-transact-sql.md) vue de catalogue. Cette procédure stockée peut être exécutée uniquement dans les **master** base de données.  
  
**sp_dropextendedproc** ne supprime pas les procédures stockées étendues système. Au lieu de cela, l’administrateur système doit refuser l’autorisation EXECUTE sur la procédure stockée étendue à la **public** rôle.  
  
 **sp_dropextendedproc** ne peut pas être exécutée à l’intérieur d’une transaction.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_dropextendedproc**.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant supprime la procédure stockées étendue `xp_hello`.  
  
> [!NOTE]  
>  Cette procédure doit déjà exister ; si ce n'est pas le cas, un message d'erreur est renvoyé.  
  
```  
USE master;  
GO  
EXEC sp_dropextendedproc 'xp_hello';  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_helpextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
