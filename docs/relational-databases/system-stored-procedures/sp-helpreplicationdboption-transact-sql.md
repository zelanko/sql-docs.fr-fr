---
title: sp_helpreplicationdboption (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpreplicationdboption_TSQL
- sp_helpreplicationdboption
helpviewer_keywords:
- sp_helpreplicationdboption
ms.assetid: 143ce689-108b-49d7-9892-fd3a86897f38
author: stevestein
ms.author: sstein
ms.openlocfilehash: fe71adc1be14b40d18baf50eecd68c2bef65c836
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997571"
---
# <a name="sphelpreplicationdboption-transact-sql"></a>sp_helpreplicationdboption (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Indique si les bases de données du serveur de publication sont activées pour la réplication. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de publication. *Pas de prise en charge pour les serveurs de publication Oracle.*  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helpreplicationdboption [ [ @dbname =] 'dbname' ]  
    [ , [ @type = ] 'type' ]  
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @dbname = ] 'dbname'` Est le nom de la base de données. *dbname* est **sysname**, avec une valeur par défaut **%** . Si **%** , puis le jeu de résultats contient toutes les bases de données sur le serveur de publication, sinon seules les informations sur la base de données spécifiée sont retournées. Aucune information n'est retournée sur les bases de données pour lesquelles l'utilisateur ne possède pas les autorisations appropriées, comme décrit ci-dessous.  
  
`[ @type = ] 'type'` Restreint le jeu de résultats aux seules les bases de données sur lequel l’option de réplication spécifié *type* valeur a été activée. *type* est **sysname**, et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**publish**|Réplication transactionnelle autorisée.|  
|**publication de fusion**|Réplication de fusion autorisée.|  
|**réplication autorisée** (valeur par défaut)|Réplication autorisée, qu'elle soit transactionnelle ou de fusion.|  
  
`[ @reserved = ] reserved` Spécifie si les informations sur les abonnements et les publications existantes sont retournées. *réservé* est **bits**, valeur par défaut est 0. Si **1**, le jeu de résultats inclut des informations selon que la base de données spécifié dispose des publications ou abonnements existants.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|Nom de la base de données.|  
|**id**|**int**|Identificateur de la base de données.|  
|**transpublish**|**bit**|Si la base de données a été activée pour la publication transactionnelle ou d’instantané sachant que la valeur **1** signifie que la publication transactionnelle ou instantané est activée.|  
|**mergepublish**|**bit**|Si la base de données a été activée pour la fusion de publication ; sachant que la valeur **1** signifie que la publication de fusion est activée.|  
|**dbowner**|**bit**|Si l’utilisateur est membre de la **db_owner** fixe le rôle de base de données ; où la valeur **1** indique que l’utilisateur est un membre de ce rôle.|  
|**dbreadonly**|**bit**|Est si la base de données est marquée comme étant en lecture seule ; sachant que la valeur **1** signifie que la base de données est en lecture seule.|  
|**haspublications**|**bit**|Indique si la base de données présente toutes les publications existantes ; sachant que la valeur **1** signifie qu’il existe des publications existantes.|  
|**haspullsubscriptions**|**bit**|Indique si la base de données présente des abonnements par extraction existants ; sachant que la valeur **1** signifie qu’il existe des abonnements par extraction.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helpreplicationdboption** est utilisé dans l’instantané, transactionnelle et la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_helpreplicationdboption** pour toute base de données. Membres de la **db_owner** rôle de base de données fixe peuvent exécuter **sp_helpreplicationdboption** pour cette base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_replicationdboption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
