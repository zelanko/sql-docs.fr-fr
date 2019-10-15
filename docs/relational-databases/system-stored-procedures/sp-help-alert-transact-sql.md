---
title: sp_help_alert (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_alert
- sp_help_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_alert
ms.assetid: 850cef4e-6348-4439-8e79-fd1bca712091
author: stevestein
ms.author: sstein
ms.openlocfilehash: a4b430884a497d9a8926f16f387b3608300f037c
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304837"
---
# <a name="sp_help_alert-transact-sql"></a>sp_help_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Fournit des informations sur les alertes définies pour le serveur.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_help_alert [ [ @alert_name = ] 'alert_name' ]   
     [ , [ @order_by = ] 'order_by' ]   
     [ , [ @alert_id = ] alert_id ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @legacy_format = ] legacy_format ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @alert_name = ] 'alert_name'` nom de l’alerte. *alert_name* est **de type nvarchar (128)** . Si *alert_name* n’est pas spécifié, des informations sur toutes les alertes sont retournées.  
  
`[ @order_by = ] 'order_by'` l’ordre de tri à utiliser pour produire les résultats. *order_by*est de **type sysname**, avec N'*Name*'comme valeur par défaut.  
  
`[ @alert_id = ] alert_id` Numéro d’identification de l’alerte pour laquelle signaler des informations. *alert_id*est de **type int**, avec NULL comme valeur par défaut.  
  
`[ @category_name = ] 'category'` la catégorie de l’alerte. *Category* est de **type sysname**, avec NULL comme valeur par défaut.  
  
`[ @legacy_format = ] legacy_format` indique s’il faut générer un jeu de résultats hérité. *legacy_format* est de valeur de **bit**, avec **0**comme valeur par défaut. Lorsque *legacy_format* a la valeur **1**, **sp_help_alert** retourne le jeu de résultats retourné par **sp_help_alert** dans Microsoft SQL Server 2000.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 Lorsque **\@legacy_format** a la valeur **0**, **sp_help_alert** produit le jeu de résultats suivant.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|Identificateur entier unique attribué par le système.|  
|**name**|**sysname**|Nom de l’alerte (par exemple, Demo : Journal **msdb** complet).|  
|**event_source**|**nvarchar(100)**|Source de l'événement. Il s’agira toujours de **MSSQLSERVER** pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7,0|  
|**event_category_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**Int**|Numéro du message d'erreur définissant l'alerte (Correspond généralement à un numéro d’erreur dans la table **sysmessages** ). Si le niveau de gravité est utilisé pour définir l’alerte, la valeur de **message_id** est **0** ou null.|  
|**severity**|**Int**|Niveau de gravité (compris entre **9** et **25**, **110**, **120**, **130**ou **140**) qui définit l’alerte.|  
|**enabled**|**tinyint**|État indiquant si l’alerte est actuellement activée (**1**) ou non (**0**). Une alerte non activée ne peut pas être envoyée.|  
|**delay_between_responses**|**Int**|Délai d'attente, en secondes, entre les réponses à l'alerte.|  
|**last_occurrence_date**|**Int**|Date de la dernière apparition de l'alerte.|  
|**last_occurrence_time**|**Int**|Heure de la dernière apparition de l'alerte.|  
|**last_response_date**|**Int**|Date à laquelle le service **SQLServerAgent** a répondu pour la dernière fois à l’alerte.|  
|**last_response_time**|**Int**|Heure à laquelle le service **SQLServerAgent** a répondu pour la dernière fois à l’alerte.|  
|**notification_message**|**nvarchar(512)**|Message supplémentaire facultatif qui sera envoyé à l'opérateur avec la notification par courrier électronique ou radiomessagerie.|  
|**include_event_description**|**tinyint**|Indique si la description de l'erreur de SQL Server contenue dans le journal des applications Windows doit apparaître dans le message de notification.|  
|**database_name**|**sysname**|Base de données dans laquelle l'erreur doit apparaître pour que l'alerte soit déclenchée. Si le nom de la base de données est NULL, l'alerte se déclenche où que se soit produite l'erreur.|  
|**event_description_keyword**|**nvarchar(100)**|Description de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le journal des applications Windows qui doit être identique à la séquence de caractères fournie.|  
|**occurrence_count**|**Int**|Nombre de déclenchements de l'alerte.|  
|**count_reset_date**|**Int**|Date de la dernière réinitialisation du **occurrence_count** .|  
|**count_reset_time**|**Int**|Heure de la dernière réinitialisation du **occurrence_count** .|  
|**job_id**|**uniqueidentifier**|Numéro d'identification du travail à exécuter en réponse à une alerte.|  
|**job_name**|**sysname**|Nom du travail à exécuter en réponse à une alerte.|  
|**has_notification**|**Int**|Différent de zéro si un ou plusieurs opérateurs sont notifiés pour cette alerte. Le paramètre peut avoir les valeurs suivantes (liées par OR) :<br /><br /> **1**= a une notification par courrier électronique<br /><br /> **2**= notification de radiomessagerie<br /><br /> **4**= notification d' **envoi réseau** .|  
|**flags**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**performance_condition**|**nvarchar(512)**|Si le **type** est **2**, cette colonne indique la définition de la condition de performance ; dans le cas contraire, la colonne a la valeur NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] Sera toujours '[Uncategorized]' pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0.|  
|**wmi_namespace**|**sysname**|Si le **type** est **3**, cette colonne indique l’espace de noms pour l’événement WMI.|  
|**wmi_query**|**nvarchar(512)**|Si le **type** est **3**, cette colonne affiche la requête pour l’événement WMI.|  
|**type**|**Int**|Type de l'événement :<br /><br /> alerte d’événement **1** =  @ no__t-2<br /><br /> **2** =  @ no__t-2 alerte de performance<br /><br /> **3** = alerte d’événement WMI|  
  
 Lorsque **\@legacy_format** a la valeur **1**, **sp_help_alert** produit le jeu de résultats suivant.  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|Identificateur entier unique attribué par le système.|  
|**name**|**sysname**|Nom de l’alerte (par exemple, Demo : Journal **msdb** complet).|  
|**event_source**|**nvarchar(100)**|Source de l'événement. Il s’agira toujours de **MSSQLSERVER** pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7,0|  
|**event_category_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**event_id**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**message_id**|**Int**|Numéro du message d'erreur définissant l'alerte (Correspond généralement à un numéro d’erreur dans la table **sysmessages** ). Si le niveau de gravité est utilisé pour définir l’alerte, la valeur de **message_id** est **0** ou null.|  
|**severity**|**Int**|Niveau de gravité (compris entre **9** et **25**, **110**, **120**, **130**ou 1**40**) qui définit l’alerte.|  
|**enabled**|**tinyint**|État indiquant si l’alerte est actuellement activée (**1**) ou non (**0**). Une alerte non activée ne peut pas être envoyée.|  
|**delay_between_responses**|**Int**|Délai d'attente, en secondes, entre les réponses à l'alerte.|  
|**last_occurrence_date**|**Int**|Date de la dernière apparition de l'alerte.|  
|**last_occurrence_time**|**Int**|Heure de la dernière apparition de l'alerte.|  
|**last_response_date**|**Int**|Date à laquelle le service **SQLServerAgent** a répondu pour la dernière fois à l’alerte.|  
|**last_response_time**|**Int**|Heure à laquelle le service **SQLServerAgent** a répondu pour la dernière fois à l’alerte.|  
|**notification_message**|**nvarchar(512)**|Message supplémentaire facultatif qui sera envoyé à l'opérateur avec la notification par courrier électronique ou radiomessagerie.|  
|**include_event_description**|**tinyint**|Indique si la description de l'erreur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenue dans le journal des applications Windows doit apparaître dans le message de notification.|  
|**database_name**|**sysname**|Base de données dans laquelle l'erreur doit apparaître pour que l'alerte soit déclenchée. Si le nom de la base de données est NULL, l'alerte se déclenche où que se soit produite l'erreur.|  
|**event_description_keyword**|**nvarchar(100)**|Description de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans le journal des applications Windows qui doit être identique à la séquence de caractères fournie.|  
|**occurrence_count**|**Int**|Nombre de déclenchements de l'alerte.|  
|**count_reset_date**|**Int**|Date de la dernière réinitialisation du **occurrence_count** .|  
|**count_reset_time**|**Int**|Heure de la dernière réinitialisation du **occurrence_count** .|  
|**job_id**|**uniqueidentifier**|Numéro d’identification du travail.|  
|**job_name**|**sysname**|Nom d'un travail à la demande exécuté en réponse à une alerte.|  
|**has_notification**|**Int**|Différent de zéro si un ou plusieurs opérateurs sont notifiés pour cette alerte. Le paramètre peut avoir une ou plusieurs des valeurs suivantes (combinées avec OR) :<br /><br /> **1**= a une notification par courrier électronique<br /><br /> **2**= notification de radiomessagerie<br /><br /> **4**= notification d' **envoi réseau** .|  
|**flags**|**Int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] .|  
|**performance_condition**|**nvarchar(512)**|Si le **type** est **2**, cette colonne indique la définition de la condition de performance. Si le **type** est **3**, cette colonne affiche la requête pour l’événement WMI. Dans les autres cas, cette colonne est NULL.|  
|**category_name**|**sysname**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] sera toujours « [n’appartenant à aucune**catégorie]** » pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7,0.|  
|**type**|**Int**|Type d'alerte :<br /><br /> alerte d’événement **1** =  @ no__t-2<br /><br /> **2** =  @ no__t-2 alerte de performance<br /><br /> **3** = alerte d’événement WMI|  
  
## <a name="remarks"></a>Notes  
 **sp_help_alert** doit être exécuté à partir de la base de données **msdb** .  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, les membres du rôle serveur fixe **sysadmin** peuvent exécuter cette procédure stockée. Les autres utilisateurs doivent disposer du rôle de base de données fixe **SQLAgentOperatorRole** dans la base de données **msdb** .  
  
 Pour plus d’informations sur les **SQLAgentOperatorRole**, consultez [SQL Server Agent des rôles de base de données fixes](../../ssms/agent/sql-server-agent-fixed-database-roles.md).  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant retourne des informations sur l'alerte `Demo: Sev. 25 Errors`.  
  
```  
USE msdb ;  
GO  
  
EXEC sp_help_alert @alert_name = 'Demo: Sev. 25 Errors';  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-alert-transact-sql.md)   
 [sp_update_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
