---
title: sp_refresh_log_shipping_monitor (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refresh_log_shipping_monitor
- sp_refresh_log_shipping_monitor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refresh_log_shipping_monitor
ms.assetid: edefb912-31c5-4d99-9aba-06629afd0171
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4382dc4de4010944e60cb37640759e91a0fc2727
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47851557"
---
# <a name="sprefreshlogshippingmonitor-transact-sql"></a>sp_refresh_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette procédure stockée actualise les tables de moniteurs distants avec les dernières informations provenant d'un serveur principal ou secondaire spécifique pour l'Agent de copie des journaux de transaction. La procédure est appelée sur le serveur principal ou secondaire.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_refresh_log_shipping_monitor  
[ @agent_id = ] 'agent_id',  
[ @agent_type = ] 'agent_type'  
[ @database = ] 'database'  
[ @mode ] n  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@agent_id=** ] **'***agent_id***'**  
 ID principal pour la sauvegarde ou ID secondaire pour la copie ou la restauration. *éléments agent_id* est **uniqueidentifier** et ne peut pas être NULL.  
  
 [  **@agent_type=** ] **'***agent_type***'**  
 Type d'opération de copie des journaux de transaction.  
  
 0 = Sauvegarde.  
  
 1 = Copie.  
  
 2 = Restauration.  
  
 *agent_type* est **tinyint** et ne peut pas être NULL.  
  
 [  **@database=** ] **'***base de données***'**  
 Base de données primaire ou secondaire utilisée pour la connexion par des agents de sauvegarde ou de restauration.  
  
 [ **@mode** ] *n*  
 Spécifie s'il faut actualiser les données du moniteur ou les effacer. Le type de données de *m* est de type tinyint et les valeurs prises en charge sont :  
  
 1 = actualisation (Il s'agit de la valeur par défaut.)  
  
 2 = delete  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Aucun.  
  
## <a name="remarks"></a>Notes  
 **sp_refresh_log_shipping_monitor** actualise le **log_shipping_monitor_primary**, **log_shipping_monitor_secondary**, **log_shipping_monitor_history_detail** , et **log_shipping_monitor_error_detail** tables avec toutes les informations de session qui n’a pas déjà été transférées. Vous pouvez ainsi synchroniser le serveur moniteur avec un serveur principal ou secondaire lorsque sa dernière synchronisation remonte à un certain temps et vous pouvez si nécessaire y nettoyer les informations de moniteur.  
  
 **sp_refresh_log_shipping_monitor** doit être exécuté à partir de la **master** base de données sur le serveur principal ou secondaire.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe peut exécuter cette procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [À propos de la copie des journaux des transactions &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
