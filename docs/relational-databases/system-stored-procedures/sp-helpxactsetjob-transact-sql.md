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
manager: craigg
ms.openlocfilehash: 7402fcc825e6f537703268c1fd3fead9c88b1f5e
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204678"
---
# <a name="sphelpxactsetjob-transact-sql"></a>sp_helpxactsetjob (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Affiche des informations sur le travail Xactset pour un serveur de publication Oracle. Cette procédure stockée est exécutée sur le serveur de distribution sur une base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpxactsetjob [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>Arguments  
 [**@publisher** =] **'***publisher***'**  
 Est le nom de la non - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] serveur de publication à laquelle appartient la tâche. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**numéro_travail**|**Int**|Numéro de travail Oracle.|  
|**lastdate**|**varchar(22)**|Dernière date d'exécution du travail.|  
|**thisdate**|**varchar(22)**|Heure de la modification|  
|**nextdate**|**varchar(22)**|Date de la prochaine exécution du travail.|  
|**rompu**|**varchar (1)**|Indicateur signalant si le travail est interrompu.|  
|**Intervalle**|**varchar(200)**|Intervalle du travail.|  
|**échecs**|**Int**|Nombre d'échecs du travail.|  
|**xactsetjobwhat**|**varchar(200)**|Nom de la procédure exécutée par le travail.|  
|**xactsetjob**|**varchar (1)**|État du travail, qui peut être l'un des suivants :<br /><br /> **1** -le travail est activé.<br /><br /> **0** -le travail est désactivé.|  
|**xactsetlonginterval**|**Int**|Intervalle long pour le travail.|  
|**xactsetlongthreshold**|**Int**|Seuil long pour le travail.|  
|**xactsetshortinterval**|**Int**|Intervalle court pour le travail.|  
|**xactsetshortthreshold**|**Int**|Seuil court pour le travail.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpxactsetjob** est utilisé dans la réplication d’instantané ou transactionnelle pour une publication Oracle.  
  
 **sp_helpxactsetjob** retourne toujours les paramètres actuels pour le travail Xactset (HREPL_XactSetJob) sur le serveur de publication. Si le travail Xactset est actuellement dans la file d'attente des travaux, il renvoie en outre des attributs du travail à partir de la vue du dictionnaire de données USER_JOB créée sous le compte administrateur sur le serveur de publication Oracle.  
  
## <a name="permissions"></a>Autorisations  
 Seul un membre de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_helpxactsetjob**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le travail d’un jeu de transactions pour un serveur de publication Oracle &#40;programmation Transact-SQL de la réplication&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [sp_publisherproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql.md)  
  
  
