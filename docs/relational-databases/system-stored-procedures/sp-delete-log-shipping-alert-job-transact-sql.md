---
title: sp_delete_log_shipping_alert_job (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_log_shipping_alert_job
- sp_delete_log_shipping_alert_job_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_alert_job
ms.assetid: 5d6c7f07-a163-48fa-8c1f-abc252043dde
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e413b677062841dbd25e2c57e0437efe566ccf98
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085318"
---
# <a name="spdeletelogshippingalertjob-transact-sql"></a>sp_delete_log_shipping_alert_job (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une alerte de travail du serveur de surveillance de la copie des journaux de transaction si le travail existe, et s'il n'existe aucune base de données primaire ou secondaire à analyser.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_log_shipping_alert_job  
  
```  
  
## <a name="arguments"></a>Arguments  
 Aucune.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucune.  
  
## <a name="remarks"></a>Notes  
 **sp_delete_log_shipping_alert_job** doit être exécuté à partir de la **master** base de données sur le serveur moniteur.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe peut exécuter cette procédure.  
  
## <a name="examples"></a>Exemples  
 Cet exemple illustre l’exécution de **sp_delete_log_shipping_alert_job** pour supprimer un travail d’alerte.  
  
```  
USE master;  
GO  
EXEC sp_delete_log_shipping_alert_job;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
