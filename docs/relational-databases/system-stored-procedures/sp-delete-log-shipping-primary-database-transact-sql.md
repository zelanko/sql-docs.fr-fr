---
title: sp_delete_log_shipping_primary_database (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_log_shipping_primary_database
- sp_delete_log_shipping_primary_database_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_primary_database
ms.assetid: cb1d5d00-2805-4d47-bd04-545232067345
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4689151d8552d50657239173338a473933ac5aa2
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67586402"
---
# <a name="spdeletelogshippingprimarydatabase-transact-sql"></a>sp_delete_log_shipping_primary_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Cette procédure stockée supprime la copie des journaux de transactions de la base de données primaire, y compris les travaux de sauvegarde, ainsi que les historiques locaux et distants. Utilisez uniquement cette procédure stockée après avoir supprimé les bases de données secondaire à l’aide de **sp_delete_log_shipping_primary_secondary**.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_log_shipping_primary_database  
[ @database = ] 'database'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @database = ] 'database'` Est le nom du journal de transaction base de données primaire. *base de données* est **sysname**, sans valeur par défaut, et ne peut pas être NULL.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 **sp_delete_log_shipping_primary_database** doit être exécuté à partir de la **master** base de données sur le serveur principal. Elle effectue les actions suivantes :  
  
1.  Supprime le travail de sauvegarde de la base de données primaire spécifiée.  
  
2.  Supprime l’enregistrement du moniteur local dans **log_shipping_monitor_primary** sur le serveur principal.  
  
3.  Supprime les entrées correspondantes dans **log_shipping_monitor_history_detail** et **log_shipping_monitor_error_detail**.  
  
4.  Si le serveur moniteur est différent du serveur principal, supprime l’enregistrement du moniteur dans **log_shipping_monitor_primary** sur le serveur moniteur.  
  
5.  Supprime les entrées correspondantes dans **log_shipping_monitor_history_detail** et **log_shipping_monitor_error_detail** sur le serveur moniteur.  
  
6.  Supprime l’entrée dans **log_shipping_primary_databases** pour cette base de données primaire.  
  
7.  Appels **sp_delete_log_shipping_alert_job** sur le serveur moniteur.  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe peut exécuter cette procédure.  
  
## <a name="examples"></a>Exemples  
 Cet exemple illustre l’utilisation de **sp_delete_log_shipping_primary_database** pour supprimer la base de données primaire **AdventureWorks2012**.  
  
```  
EXEC master.dbo.sp_delete_log_shipping_primary_database @database = N'AdventureWorks2012';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
