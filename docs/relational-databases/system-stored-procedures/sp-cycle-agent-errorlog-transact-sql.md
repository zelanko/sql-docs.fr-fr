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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 8fcb9bad5548107ef3a9294f22696abeacbdedcd
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826245"
---
# <a name="sp_cycle_agent_errorlog-transact-sql"></a>sp_cycle_agent_errorlog (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ferme le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fichier journal des erreurs de l’agent en cours et parcourt les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] numéros d’extension du journal des erreurs de l’agent tout comme un redémarrage du serveur. Le nouveau journal d'erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent contient une ligne indiquant que le nouveau journal a été créé.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_cycle_agent_errorlog  
```  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 Chaque fois que l' [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] agent est démarré, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Journal des erreurs de l’agent en cours est renommé **sqlagent. 1**; **Sqlagent. 1** devient **sqlagent. 2**, **sqlagent. 2** devient **sqlagent. 3**, et ainsi de suite. **sp_cycle_agent_errorlog** vous permet de parcourir les fichiers journaux d’erreurs sans arrêter ni redémarrer le serveur.  
  
 Cette procédure stockée doit être exécutée à partir de la base de données **msdb** .  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution pour **sp_cycle_agent_errorlog** sont limitées aux membres du rôle serveur fixe **sysadmin** .  
  
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
  
  
