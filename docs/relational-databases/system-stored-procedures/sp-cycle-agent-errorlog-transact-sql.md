---
title: sp_cycle_agent_errorlog (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cycle_agent_errorlog
- sp_cycle_agent_errorlog_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_cycle_agent_errorlog
ms.assetid: 8aa96182-60b7-4d7b-b2a7-ccce70378c6e
author: stevestein
ms.author: sstein
ms.openlocfilehash: c95cc2db84bdf059437a45e2719bbc63d6eb6829
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68108352"
---
# <a name="spcycleagenterrorlog-transact-sql"></a>sp_cycle_agent_errorlog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ferme actuel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cycles et fichier journal des erreurs Agent le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent numéros extension journal d’erreurs comme un redémarrage du serveur. Le nouveau journal d'erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent contient une ligne indiquant que le nouveau journal a été créé.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_cycle_agent_errorlog  
```  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 Chaque fois que [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent est démarré, en cours [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent journal d’erreurs est renommé **SQLAgent.1**; **SQLAgent.1** devient **SQLAgent.2**, **SQLAgent.2** devient **SQLAgent.3**, et ainsi de suite. **sp_cycle_agent_errorlog** vous permet de parcourir les fichiers journaux des erreurs sans arrêter et démarrer le serveur.  
  
 Cette procédure stockée doit être exécutée à partir de la **msdb** base de données.  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution **sp_cycle_agent_errorlog** sont limités aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant parcourt le journal d'erreurs de l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_cycle_agent_errorlog ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_cycle_errorlog &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-cycle-errorlog-transact-sql.md)  
  
  
