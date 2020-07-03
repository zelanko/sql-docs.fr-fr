---
title: sysmail_stop_sp (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_stop_sp_TSQL
- sysmail_stop_sp
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_stop_sp
ms.assetid: 045ee36f-5bf0-4626-b5ee-e84db06ce16f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e503667d51da42f5d103ae479dba3b4a1cba7fce
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85890866"
---
# <a name="sysmail_stop_sp-transact-sql"></a>sysmail_stop_sp (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Arrête la messagerie de base de données en arrêtant les objets [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilisés par le programme externe.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sysmail_stop_sp  
```  
  
## <a name="arguments"></a>Arguments  
 None  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Remarques  
 Cette procédure stockée se trouve dans la base de données **msdb** .  
  
 Elle arrête la file d'attente de la messagerie de base de données contenant les demandes de messages sortants et désactive [!INCLUDE[ssSB](../../includes/sssb-md.md)] pour le programme externe.  
  
 Dès que les files d'attente sont arrêtées, le programme externe de la messagerie de base de données ne traite plus les messages. Cette procédure stockée vous permet d'arrêter la messagerie de base de données pour résoudre des problèmes ou effectuer des tâches de maintenance.  
  
 Pour démarrer Database Mail, utilisez **sysmail_start_sp**. Notez que **sp_send_dbmail** accepte toujours le courrier lorsque les [!INCLUDE[ssSB](../../includes/sssb-md.md)] objets sont arrêtés.  
  
> [!NOTE]  
>  Cette procédure stockée arrête simplement les files d'attente de la messagerie de base de données. Elle ne désactive pas la remise de messages [!INCLUDE[ssSB](../../includes/sssb-md.md)] dans la base de données. Cette procédure stockée ne désactive pas les procédures stockées étendues de la messagerie de base de données pour réduire la zone de surface. Pour désactiver les procédures stockées étendues, consultez l' [option Database mail XPS](../../database-engine/configure-windows/database-mail-xps-server-configuration-option.md) de la procédure stockée système **sp_configure** .  
  
## <a name="permissions"></a>Autorisations  
 Les autorisations d’exécution pour cette procédure sont octroyées par défaut aux membres du rôle serveur fixe **sysadmin** .  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant montre l’arrêt d’Database Mail dans la base de données **msdb** . Il suppose que la messagerie de base de données a été activée.  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sysmail_stop_sp ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Database Mail](../../relational-databases/database-mail/database-mail.md)   
 [sysmail_start_sp &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sysmail-start-sp-transact-sql.md)   
 [Database Mail des procédures stockées &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
