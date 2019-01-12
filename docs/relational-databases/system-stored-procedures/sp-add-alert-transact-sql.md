---
title: sp_add_alert (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_alert
- sp_add_alert_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_alert
ms.assetid: d9b41853-e22d-4813-a79f-57efb4511f09
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 4193e073f4ad4c52d6b2c7f6b82c6246107e85a1
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54127069"
---
# <a name="spaddalert-transact-sql"></a>sp_add_alert (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée une alerte.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_alert [ @name = ] 'name'   
     [ , [ @message_id = ] message_id ]   
     [ , [ @severity = ] severity ]   
     [ , [ @enabled = ] enabled ]  
     [ , [ @delay_between_responses = ] delay_between_responses ]   
     [ , [ @notification_message = ] 'notification_message' ]   
     [ , [ @include_event_description_in = ] include_event_description_in ]   
     [ , [ @database_name = ] 'database' ]   
     [ , [ @event_description_keyword = ] 'event_description_keyword_pattern' ]   
     [ , { [ @job_id = ] job_id | [ @job_name = ] 'job_name' } ]   
     [ , [ @raise_snmp_trap = ] raise_snmp_trap ]   
     [ , [ @performance_condition = ] 'performance_condition' ]   
     [ , [ @category_name = ] 'category' ]   
     [ , [ @wmi_namespace = ] 'wmi_namespace' ]  
     [ , [ @wmi_query = ] 'wmi_query' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@name =** ] **'**_nom_**'**  
 Le nom de l'alerte. Ce nom apparaît dans le message envoyé par courrier électronique ou par radiomessagerie en réponse à l'alerte. Il doit être unique et peut contenir le pourcentage (**%**) caractères. *nom* est **sysname**, sans valeur par défaut.  
  
 [  **@message_id =** ] *message_id*  
 Numéro du message d'erreur définissant l'alerte. (Il correspond normalement à un numéro d’erreur dans le **sysmessages** table.) *message_id* est **int**, avec une valeur par défaut **0**. Si *gravité* est utilisé pour définir l’alerte, *message_id* doit être **0** ou NULL.  
  
> [!NOTE]  
>  Uniquement **sysmessages** erreurs écrites dans le journal des applications Microsoft Windows peuvent provoquer une alerte doit être envoyé.  
  
 [  **@severity =** ] *gravité*  
 Le niveau de gravité (à partir de **1** via **25**) qui définit l’alerte. N’importe quel [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] message stocké dans le **sysmessages** table envoyé à la [!INCLUDE[msCoName](../../includes/msconame-md.md)] journal des applications Windows avec le niveau de gravité indiqué provoque l’envoi de l’alerte. *gravité* est **int**, avec 0 comme valeur par défaut. Si *message_id* est utilisé pour définir l’alerte, *gravité* doit être **0**.  
  
 [  **@enabled =** ] *activé*  
 Indique l'état actuel de l'alerte. *activé* est **tinyint**, avec une valeur par défaut de 1 (activé). Si **0**, l’alerte n’est pas activé et ne se déclenche pas.  
  
 [  **@delay_between_responses =** ] *délai_entre_réponses*  
 Le délai d’attente, en secondes, entre les réponses à l’alerte. *délai_entre_réponses*est **int**, avec une valeur par défaut **0**, ce qui signifie qu’il n’existe aucun délai d’attente entre les réponses (chaque occurrence de l’alerte génère une réponse). La réponse peut prendre l'une des formes suivantes, ou les deux :  
  
-   Une ou plusieurs notifications envoyées par courrier électronique ou par radiomessagerie  
  
-   Un travail à exécuter  
  
 En définissant cette valeur, il est possible d'éviter, par exemple, l'envoi d'un flot de messages par courrier électronique lorsqu'une alerte se produit à plusieurs reprises en peu de temps.  
  
 [  **@notification_message =** ] **'**_message_notification_**'**  
 Est un message supplémentaire facultatif envoyé à l’opérateur en tant que partie du message électronique, **envoi réseau**, ou par radiomessagerie. *message_notification* est **nvarchar (512)**, avec NULL comme valeur par défaut. Spécification *message_notification* est utile pour l’ajout de remarques particulières telles que des procédures correctives.  
  
 [  **@include_event_description_in =** ] *inclure_description_événement_dans*  
 Argument à utiliser si la description de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être incluse dans le message de notification. *inclure_description_événement_dans*est **tinyint**, avec une valeur par défaut **5** (courrier électronique et **net send**) et peut avoir une ou plusieurs de ces valeurs combinées avec un **Ou** opérateur logique.  
  
> [!IMPORTANT]
>  Les options du récepteur de radiomessagerie et **net send** seront supprimées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans une version future de [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Évitez d'utiliser ces fonctionnalités dans une nouvelle tâche de développement et prévoyez de modifier les applications qui les utilisent actuellement.  
  
|Value|Description|  
|-----------|-----------------|  
|**0**|None|  
|**1**|Messagerie électronique|  
|**2**|Radiomessagerie|  
|**4**|**net send**|  
  
 [  **@database_name =** ] **'**_base de données_**'**  
 Base de données dans laquelle l'erreur doit survenir pour que l'alerte soit déclenchée. Si *base de données*n’est pas fourni, l’alerte se déclenche, quel que soit l’endroit où l’erreur s’est produite. *base de données* est **sysname**. Les noms placés entre crochets ([ ]) ne sont pas autorisés. La valeur par défaut est NULL.  
  
 [  **@event_description_keyword =** ] **'**_modèle_mots_clés_description_événement_**'**  
 Séquence de caractères à laquelle la description de l'erreur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] doit être conforme. Les caractères correspondant au modèle d'expression [!INCLUDE[tsql](../../includes/tsql-md.md)] LIKE sont admis. *modèle_mots_clés_description_événement* est **nvarchar (100)**, avec NULL comme valeur par défaut. Ce paramètre est utile pour filtrer les noms d’objets (par exemple, **% customer_table %**).  
  
 [  **@job_id =** ] *job_id*  
 Numéro d'identification du travail à exécuter en réponse à l'alerte. *job_id* est **uniqueidentifier**, avec NULL comme valeur par défaut.  
  
 [  **@job_name =** ] **'**_nom_travail_**'**  
 Nom du travail à exécuter en réponse à cette alerte. *job_name*est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Soit *job_id* ou *nom_travail* doit être spécifié, mais ne peut pas être spécifiés.  
  
 [  **@raise_snmp_trap =** ] *raise_snmp_trap*  
 Non implémenté dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 7.0. *raise_snmp_trap* est **tinyint**, avec 0 comme valeur par défaut.  
  
 [  **@performance_condition =** ] **'**_l’argument condition_performances_**'**  
 Est une valeur exprimée dans le format '*itemcomparatorvalue*». *l’argument condition_performances* est **nvarchar (512)** avec une valeur par défaut NULL et se compose de ces éléments.  
  
|Élément de format|Description|  
|--------------------|-----------------|  
|*Élément*|Objet de performances, compteur de performances ou instance nommée du compteur.|  
|*Comparateur*|Un des opérateurs suivants : >, < ou =|  
|*Valeur*|Valeur numérique du compteur.|  
  
 [  **@category_name =** ] **'**_catégorie_**'**  
 Nom de la catégorie d'alerte. *catégorie* est **sysname**, avec NULL comme valeur par défaut.  
  
 [ **@wmi_namespace**=] **'**_wmi_namespace_**'**  
 Espace de noms WMI permettant de rechercher des événements via des requêtes. *wmi_namespace* est **sysname**, avec NULL comme valeur par défaut. Seuls les espaces de noms situés sur le serveur local sont pris en charge.  
  
 [ **@wmi_query**=] **'**_wmi_query_**'**  
 Requête spécifiant l'événement WMI pour l'alerte. *wmi_query* est **nvarchar (512)**, avec NULL comme valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="remarks"></a>Notes  
 **sp_add_alert** doit être exécuté à partir de la **msdb** base de données.  
  
 La liste suivante indique les circonstances pour lesquelles les erreurs ou les messages générés par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les applications [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont transmis au journal des applications Windows et peuvent dès lors déclencher des alertes :  
  
-   Niveau de gravité égal ou supérieur à 19 **sys.messages** erreurs  
  
-   toute instruction RAISERROR appelée avec la syntaxe WITH LOG ;  
  
-   N’importe quel **sys.messages** erreur modifiée ou créée avec **sp_altermessage**  
  
-   Tout événement consigné avec **xp_logevent**  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] est un outil simple, fonctionnant en mode graphique, qui permet de gérer tout le système d'alerte. Son utilisation est recommandée pour configurer une infrastructure d'alertes.  
  
 Si une alerte ne fonctionne pas correctement, vérifiez que :  
  
-   Le service Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est en cours d'exécution.  
  
-   L'événement est consigné dans le journal des applications Windows.  
  
-   L'alerte est activée.  
  
-   Les événements créés à l’aide de **xp_logevent** surviennent dans la base de données master. Ainsi, la procédure **xp_logevent** ne déclenche pas d’alerte sauf si la valeur de **@database_name** pour l’alerte est **'master'** ou NULL.  
  
## <a name="permissions"></a>Autorisations  
 Par défaut, seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter la procédure **sp_add_alert**.  
  
## <a name="examples"></a>Exemples  
 L'exemple suivant ajoute une alerte (Test Alert) qui exécute le travail `Back up the AdventureWorks2012 Database` lorsqu'elle se déclenche.  
  
> [!NOTE]  
>  Dans cet exemple, on suppose que le message 55001 et le travail `Back up the AdventureWorks2012 Database` existent déjà. L’exemple est présenté à titre d’illustration uniquement.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_alert  
    @name = N'Test Alert',  
    @message_id = 55001,   
   @severity = 0,   
   @notification_message = N'Error 55001 has occurred. The database will be backed up...',   
   @job_name = N'Back up the AdventureWorks2012 Database' ;  
GO  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_add_notification &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-notification-transact-sql.md)   
 [sp_altermessage &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-altermessage-transact-sql.md)   
 [sp_delete_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-alert-transact-sql.md)   
 [sp_help_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-alert-transact-sql.md)   
 [sp_update_alert &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-alert-transact-sql.md)   
 [sys.sysperfinfo &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysperfinfo-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
