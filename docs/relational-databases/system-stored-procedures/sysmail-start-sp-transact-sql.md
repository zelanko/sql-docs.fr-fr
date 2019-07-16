---
title: sysmail_start_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_start_sp
- sysmail_start_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_start_sp
ms.assetid: 25fd7bb6-cfdd-463f-bea8-c6fcb805d3f5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e15996a9db6e1b782875f2dd3d73d0e3e514c8f5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68044440"
---
# <a name="sysmailstartsp-transact-sql"></a>sysmail_start_sp (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Démarre la messagerie de base de données en démarrant les objets [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilisés par le programme externe.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_start_sp  
```  
  
## <a name="arguments"></a>Arguments  
 Aucun  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun  
  
## <a name="remarks"></a>Notes  
 La messagerie de base de données n'est pas activée ou installée lors de l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez l'Assistant Configuration de la messagerie de base de données pour activer et installer les objets de messagerie de base de données.  
  
 Cette procédure stockée se trouve dans le **msdb** base de données. Elle démarre la file d'attente de la messagerie de base de données contenant les demandes de messages sortants et active [!INCLUDE[ssSB](../../includes/sssb-md.md)] pour le programme externe.  
  
 Dès que les files d'attente ont démarré, le programme externe de la messagerie de base de données peut traiter les messages. Cette procédure vous permet de redémarrer les files d’attente une fois que les files d’attente ont été arrêtés avec la **sysmail_stop_sp** procédure stockée.  
  
> [!NOTE]  
>  Cette procédure stockée démarre simplement les files d'attente de la messagerie de base de données. Elle n'active pas la remise de messages [!INCLUDE[ssSB](../../includes/sssb-md.md)] dans la base de données.  
  
## <a name="permissions"></a>Autorisations  
 Autorisations d’exécution de cette procédure reviennent par défaut aux membres de la **sysadmin** rôle serveur fixe.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre à partir de la messagerie de base de données le **msdb** base de données. Il suppose que la messagerie de base de données a été activée.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_start_sp ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Messagerie de base de données](../../relational-databases/database-mail/database-mail.md)   
 [Option de Configuration de serveur de base de données Mail XPs](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md)   
 [sysmail_stop_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-stop-sp-transact-sql.md)   
 [Procédures stockées de messagerie de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
