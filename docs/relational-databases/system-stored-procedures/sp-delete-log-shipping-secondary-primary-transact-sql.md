---
title: sp_delete_log_shipping_secondary_primary (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_log_shipping_secondary_primary_TSQL
- sp_delete_log_shipping_secondary_primary
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_log_shipping_secondary_primary
ms.assetid: 507fc744-73d9-4cb7-8d2a-bcff88841c6a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f389e6fa58feba189955c3ac8f654a906f61588f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68009137"
---
# <a name="sp_delete_log_shipping_secondary_primary-transact-sql"></a>sp_delete_log_shipping_secondary_primary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette procédure stockée supprime les informations sur le serveur primaire spécifié à partir du serveur secondaire. Elle supprime aussi le travail de copie et le travail de restauration à partir du serveur secondaire.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_delete_log_shipping_secondary_primary  
[ @primary_server = ] 'primary_server'  
[ @primary_database = ] 'primary_database'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @primary_server = ] 'primary_server'`Nom de l’instance principale du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] dans la configuration de la copie des journaux de session. *primary_server* est de **type sysname** et ne peut pas avoir la valeur null.  
  
`[ @primary_database = ] 'primary_database'`Nom de la base de données sur le serveur principal. *primary_database* est de **type sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 **sp_delete_log_shipping_secondary_primary** doit être exécuté à partir de la base de données **Master** sur le serveur secondaire. Elle effectue les actions suivantes :  
  
1.  Supprime la copie et restaure des travaux pour l'ID secondaire.  
  
2.  Supprime l’entrée dans **log_shipping_secondary**.  
  
3.  Appelle **sp_delete_log_shipping_alert_job** sur le serveur moniteur.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
