---
title: sp_addsubscriber (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addsubscriber
- sp_addsubscriber_TSQL
helpviewer_keywords:
- sp_addsubscriber
ms.assetid: b8a584ea-2a26-4936-965b-b84f026e39c0
author: stevestein
ms.author: sstein
ms.openlocfilehash: cb21731dd02fee4ec3779affed56f85e5dbc0e9b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079227"
---
# <a name="spaddsubscriber-transact-sql"></a>sp_addsubscriber (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un nouvel Abonné à un serveur de publication, lui permettant ainsi de recevoir des publications. Pour les publications transactionnelles et d'instantanés, cette procédure stockée s'exécute à partir du serveur de publication sur la base de données de publication. Pour les publications de fusion, elle s'exécute au niveau d'un serveur de distribution distant.  
  
> [!IMPORTANT]  
>  Cette procédure stockée est désormais déconseillée. Vous n'avez donc plus besoin d'enregistrer un Abonné de façon explicite auprès du serveur de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addsubscriber [ @subscriber = ] 'subscriber'  
    [ , [ @type = ] type ]   
    [ , [ @login = ] 'login' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @commit_batch_size = ] commit_batch_size ]  
    [ , [ @status_batch_size = ] status_batch_size ]  
    [ , [ @flush_frequency = ] flush_frequency ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @description = ] 'description' ]  
    [ , [ @security_mode = ] security_mode ]  
    [ , [ @encrypted_password = ] encrypted_password ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @subscriber = ] 'subscriber'` Est le nom du serveur à ajouter comme un abonné valide aux publications sur ce serveur. *abonné* est **sysname**, sans valeur par défaut.  
  
`[ @type = ] type` Est le type d’abonné. *type* est **tinyint**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**0** (valeur par défaut)|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonné|  
|**1**|Serveur de la source de données ODBC.|  
|**2**|Base de données [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet|  
|**3**|Fournisseur OLE DB|  
  
`[ @login = ] 'login'` ID de connexion pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification. *login* est de type **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @password = ] 'password'` Mot de passe [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification. *mot de passe* est **nvarchar (524)** , avec NULL comme valeur par défaut.  
  
> [!IMPORTANT]  
>  N'utilisez pas de mot de passe vide. Utilisez un mot de passe fort.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @commit_batch_size = ] commit_batch_size` Ce paramètre a été déconseillé et est conservé pour compatibilité descendante des scripts.  
  
> [!NOTE]  
>  Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @status_batch_size = ] status_batch_size` Ce paramètre a été déconseillé et est conservé pour compatibilité descendante des scripts.  
  
> [!NOTE]  
>  Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @flush_frequency = ] flush_frequency` Ce paramètre a été déconseillé et est conservé pour compatibilité descendante des scripts.  
  
> [!NOTE]  
>  Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @frequency_type = ] frequency_type` Est la fréquence de planification de l’agent de réplication. *frequency_type* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|À la demande|  
|**4**|Tous les jours|  
|**8**|Semaine|  
|**16**|Mois|  
|**32**|Mensuelle relative|  
|**64** (valeur par défaut)|Démarrage automatique|  
|**128**|Périodique|  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
 [ **@frequency_interval=** ] *frequency_interval*  
 Valeur appliquée à la fréquence définie *frequency_type*. *frequency_interval* est **int**, avec 1 comme valeur par défaut.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @frequency_relative_interval = ] frequency_relative_interval` Est la date de l’agent de réplication. Ce paramètre est utilisé lorsque *frequency_type* a la valeur **32** (fréquence mensuelle relative). *frequency_relative_interval* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1** (par défaut)|Première|  
|**2**|Seconde|  
|**4**|Troisième|  
|**8**|Quatrième|  
|**16**|Dernière|  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @frequency_recurrence_factor = ] frequency_recurrence_factor` Facteur de récurrence utilisé par *frequency_type*. *frequency_recurrence_factor* est **int**, avec une valeur par défaut **0**.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @frequency_subday = ] frequency_subday` Est la fréquence de replanification nécessaire pendant la période définie. *frequency_subday* est **int**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**1**|Une fois|  
|**2**|Seconde|  
|**4** (valeur par défaut)|Minute|  
|**8**|Heure|  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @frequency_subday_interval = ] frequency_subday_interval` Intervalle de *frequency_subday*. *frequency_subday_interval* est **int**, avec une valeur par défaut **5**.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @active_start_time_of_day = ] active_start_time_of_day` Est l’heure de la journée à laquelle l’agent de réplication est la première planifié, au format HHMMSS. *active_start_time_of_day* est **int**, avec une valeur par défaut **0**.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @active_end_time_of_day = ] active_end_time_of_day` L’heure de la journée à laquelle l’agent de réplication cesse d’être planifié, représentée au format HHMMSS. *active_end_time_of_day*est **int**, avec 235959 par défaut, qui correspond à 11:59:59 P.M. comme sur une horloge de 24 heures.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @active_start_date = ] active_start_date` Est la date à laquelle l’agent de réplication est premier planifiée, au format AAAAMMJJ. *active_start_date* est **int**, avec 0 comme valeur par défaut.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @active_end_date = ] active_end_date` Date à laquelle l’agent de réplication cesse d’être planifié, représentée au format AAAAMMJJ. *active_end_date* est **int**, avec 99991231 par défaut, ce qui signifie que le 31 décembre 9999.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @description = ] 'description'` Est une description de l’abonné. *Description* est **nvarchar (255)** , avec NULL comme valeur par défaut.  
  
`[ @security_mode = ] security_mode` Est le mode de sécurité implémenté. *security_mode* est **int**, avec 1 comme valeur par défaut. **0** spécifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification. **1** Spécifie l’authentification Windows.  
  
> [!NOTE]  
>  Ce paramètre est déconseillé et n'est maintenu que dans un but de compatibilité ascendante avec les scripts déjà établis. La propriété est maintenant spécifiée sur une base par abonnement lors de l’exécution [sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md). Lorsqu'une valeur est spécifiée, elle sert alors de valeur par défaut au moment de la création des abonnements pour cet Abonné et un message d'avertissement s'affiche.  
  
`[ @encrypted_password = ] encrypted_password` Ce paramètre est déconseillé et est fourni pour la compatibilité descendante uniquement définissant *encrypted_password* à n’importe quelle valeur mais **0** entraîne une erreur.  
  
`[ @publisher = ] 'publisher'` Spécifie un non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être utilisé lors de la publication à partir d’un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addsubscriber** est utilisé dans la réplication de capture instantanée, la réplication transactionnelle et la réplication de fusion.  
  
 **sp_addsubscriber** n’est pas nécessaire lors de l’abonné dispose uniquement d’abonnements anonymes aux publications de fusion.  
  
 **sp_addsubscriber** écrit dans le [MSsubscriber_info](../../relational-databases/system-tables/mssubscriber-info-transact-sql.md) table dans le **distribution** base de données.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_addsubscriber**.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Créer un abonnement par extraction de données ](../../relational-databases/replication/create-a-pull-subscription.md)   
 [sp_changesubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpsubscriberinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)  
  
  
