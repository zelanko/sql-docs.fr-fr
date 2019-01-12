---
title: sp_changesubscriber_schedule (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_changesubscriber_schedule
- sp_changesubscriber_schedule_TSQL
helpviewer_keywords:
- sp_changesubscriber_schedule
ms.assetid: ff84e8e2-d496-482c-b23e-38a6626596e6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 83edeb0c94276e10528b05bc5a1cd8d9474d07aa
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54127909"
---
# <a name="spchangesubscriberschedule-transact-sql"></a>sp_changesubscriber_schedule (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Modifie la planification de l'Agent de distribution ou de fusion pour un abonné. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_changesubscriber_schedule [ @subscriber = ] 'subscriber', [ @agent_type = ] type  
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
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@subscriber=**] **'**_abonné_**'**  
 Nom de l'Abonné. *abonné* est **sysname**. Le nom de l'Abonné doit être unique dans la base de données, ne doit pas déjà exister et ne peut pas avoir la valeur NULL.  
  
 [  **@agent_type=**] *type*  
 Type de l'Agent. *type* est **smallint**, avec une valeur par défaut **0**. **0** indique un Agent de Distribution. **1** indique un Agent de fusion.  
  
 [  **@frequency_type=**] *frequency_type*  
 Fréquence de planification de la tâche de distribution. *frequency_type* est **int**, avec une valeur par défaut **64**. Il y a 10 colonnes de planification.  
  
 [  **@frequency_interval=**] *frequency_interval*  
 Valeur appliquée à la fréquence définie *frequency_type*. *frequency_interval* est **int**, avec une valeur par défaut **1**.  
  
 [  **@frequency_relative_interval=**] *frequency_relative_interval*  
 Date de la tâche de distribution. *frequency_relative_interval* est **int**, avec une valeur par défaut **1**.  
  
 [  **@frequency_recurrence_factor=**] *frequency_recurrence_factor*  
 Facteur de récurrence utilisé par *frequency_type*. *frequency_recurrence_factor* est **int**, avec une valeur par défaut **0**.  
  
 [  **@frequency_subday=**] *frequency_subday*  
 Indique, en minutes, la fréquence de replanification pendant la période définie. *frequency_subday* est **int**, avec une valeur par défaut **4**.  
  
 [  **@frequency_subday_interval=**] *frequency_subday_interval*  
 Intervalle de *frequency_subday*. *frequency_subday_interval* est **int**, avec une valeur par défaut **5**.  
  
 [  **@active_start_time_of_day=**] *active_start_time_of_day*  
 Heure de première planification de la tâche de distribution. *active_start_time_of_day* est **int**, avec une valeur par défaut **0**.  
  
 [  **@active_end_time_of_day=**] *active_end_time_of_day*  
 Heure à laquelle la tâche de distribution cesse d'être planifiée. *active_end_time_of_day* est **int**, avec une valeur par défaut **235959**, ce qui signifie que 11:59:59 P.M. avec un affichage horaire au format 24 heures).  
  
 [  **@active_start_date=**] *active_start_date*  
 Date de première planification de la tâche de distribution, au format AAAAMMJJ. *active_start_date* est **int**, avec une valeur par défaut **0**.  
  
 [  **@active_end_date=**] *active_end_date*  
 Date à laquelle la tâche de distribution cesse d'être planifiée, exprimée au format AAAAMMJJ. *active_end_date* est **int**, avec une valeur par défaut **99991231**, qui correspond au 31 décembre 9999.  
  
 [ **@publisher**=] **'**_publisher_**'**  
 Spécifie un non - [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication. *serveur de publication* est **sysname**, avec NULL comme valeur par défaut.  
  
> [!NOTE]  
>  *serveur de publication* ne doit pas être utilisé lors de la modification des propriétés de l’article sur un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_changesubscriber_schedule** est utilisée dans tous les types de réplication.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_changesubscriber_schedule**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addsubscriber_schedule &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-schedule-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
