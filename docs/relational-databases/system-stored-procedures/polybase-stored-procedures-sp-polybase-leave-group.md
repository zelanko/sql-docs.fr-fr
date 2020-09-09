---
title: sp_polybase_leave_group (Transact-SQL) | Microsoft Docs
description: La commande sp_polybase_leave_group Transact-SQL supprime une instance de SQL Server d’un groupe Polybase pour le calcul avec montée en puissance parallèle.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
f1_keywords:
- sp_polybase_leave_group
- sp_polybase_leave_group_TSQL
helpviewer_keywords:
- sp_polybase_leave_group
ms.assetid: ef87a8f1-5407-47b5-b8bf-bd7d08c0f0fe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 2ce2e2ad16277c6ae5e21939976ede8ac89c8843
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89546247"
---
# <a name="sp_polybase_leave_group-transact-sql"></a>sp_polybase_leave_group (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Supprime une instance de SQL Server d’un groupe Polybase pour le calcul avec montée en puissance parallèle. 
 
 La fonctionnalité du  [Guide Polybase](../../relational-databases/polybase/polybase-guide.md) doit être installée sur l’instance SQL Server.  Polybase permet l’intégration de sources de données non SQL Server, telles que Hadoop et le stockage d’objets BLOB Azure. Voir aussi [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="permissions"></a>Autorisations  
 Nécessite l’autorisation CONTROL SERVER.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez uniquement supprimer un nœud de calcul d’un groupe.  
  
 Après l’exécution de la procédure stockée, redémarrez le moteur Polybase et le service Mouvement de données PolyBase sur l’ordinateur. Pour vérifier l’exécution de la DMV suivante sur le nœud principal : **sys. dm_exec_compute_nodes**.  
  
## <a name="example"></a>Exemple  
 L’exemple supprime l’ordinateur actuel d’un groupe Polybase.  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main de PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
