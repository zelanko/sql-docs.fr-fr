---
title: sp_helpxactsetjob (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpxactsetjob
- sp_helpxactsetjob_TSQL
helpviewer_keywords:
- sp_helpxactsetjob
ms.assetid: 242cea3e-e6ac-4f84-a072-b003b920eb33
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0fdd70480a63e334aa3e178d19287b30937e2f53
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056794"
---
# <a name="sp_helpxactsetjob-transact-sql"></a>sp_helpxactsetjob (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche des informations sur le travail Xactset pour un serveur de publication Oracle. Cette procédure stockée est exécutée sur n’importe quelle base de données du serveur de distribution.  
  
 ![Icône Lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône Lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpxactsetjob [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` est le nom du serveur de publication non [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] auquel appartient le travail. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**jobnumber**|**int**|Numéro de travail Oracle.|  
|**lastdate**|**varchar(22)**|Dernière date d'exécution du travail.|  
|**thisdate**|**varchar(22)**|Heure de la modification|  
|**nextdate**|**varchar(22)**|Date de la prochaine exécution du travail.|  
|**broken**|**varchar(1)**|Indicateur signalant si le travail est interrompu.|  
|**interval**|**varchar(200)**|Intervalle du travail.|  
|**failures**|**int**|Nombre d'échecs du travail.|  
|**xactsetjobwhat**|**varchar(200)**|Nom de la procédure exécutée par le travail.|  
|**xactsetjob**|**varchar(1)**|État du travail, qui peut être l'un des suivants :<br /><br /> **1** -la tâche est activée.<br /><br /> **0** -la tâche est désactivée.|  
|**xactsetlonginterval**|**int**|Intervalle long pour le travail.|  
|**xactsetlongthreshold**|**int**|Seuil long pour le travail.|  
|**xactsetshortinterval**|**int**|Intervalle court pour le travail.|  
|**xactsetshortthreshold**|**int**|Seuil court pour le travail.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpxactsetjob** est utilisé dans la réplication d’instantané et la réplication transactionnelle pour les serveurs de publication Oracle.  
  
 **sp_helpxactsetjob** retourne toujours les paramètres actuels de la tâche Xactset (HREPL_XactSetJob) sur le serveur de publication. Si le travail Xactset est actuellement dans la file d'attente des travaux, il renvoie en outre des attributs du travail à partir de la vue du dictionnaire de données USER_JOB créée sous le compte administrateur sur le serveur de publication Oracle.  
  
## <a name="permissions"></a>Autorisations  
 Seul un membre du rôle serveur fixe **sysadmin** peut exécuter **sp_helpxactsetjob**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le travail d’un jeu de transactions pour un serveur de publication Oracle &#40;programmation Transact-SQL de la réplication&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [sp_publisherproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
