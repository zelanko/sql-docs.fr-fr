---
title: sp_help_log_shipping_alert_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_alert_job_TSQL
- sp_help_log_shipping_alert_job
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_alert_job
ms.assetid: 4d4b4577-c393-4961-b2d3-b56e980b787b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20b946ba96e1c4fa8830b79a43f1568e866acf7b
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715881"
---
# <a name="sp_help_log_shipping_alert_job-transact-sql"></a>sp_help_log_shipping_alert_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Cette procédure stockée renvoie l'ID du travail d'alerte à partir du moniteur de copie des journaux de transaction.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_log_shipping_alert_job  
  
```  
  
## <a name="arguments"></a>Arguments  
 None  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Cette procédure stockée renvoie l' [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ID de travail de l’agent du travail d’alerte de l’envoi de journaux. S'il n'existe aucun travail d'alerte de l'envoi de journaux, il renvoie un jeu de résultats vide.  
  
## <a name="remarks"></a>Remarques  
 **sp_help_log_shipping_alert_job** doit être exécuté à partir de la base de données **Master** sur le serveur moniteur.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
