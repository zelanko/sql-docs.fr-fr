---
title: sp_publisherproperty (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_publisherproperty
- sp_publisherproperty_TSQL
helpviewer_keywords:
- sp_publisherproperty
ms.assetid: 0ed1ebc1-a1bd-4aed-9f46-615c5cf07827
author: stevestein
ms.author: sstein
ms.openlocfilehash: 185ad0ad33419b20fffae9bff3e5562761ea7b31
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771170"
---
# <a name="sppublisherproperty-transact-sql"></a>sp_publisherproperty (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Affiche ou modifie les propriétés du serveur de [!INCLUDE[msCoName](../../includes/msconame-md.md)] publication qui ne sont pas [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des serveurs de publication. Cette procédure stockée est exécutée sur le serveur de distribution.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_publisherproperty [ @publisher = ] 'publisher'   
   [ , [ @propertyname = ] 'propertyname' ]   
   [ , [ @propertyvalue = ] 'propertyvalue' ]  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publisher** =] **«***éditeur***»**  
 Nom du serveur de publication hétérogène. *Publisher* est de **type sysname**, sans valeur par défaut.  
  
 [ **@propertyname** =] **'***PropertyName***'**  
 Nom de la propriété qui est définie. *PropertyName* est de **type sysname**et peut prendre l’une des valeurs suivantes.  
  
|Value|Description|  
|-----------|-----------------|  
|**xactsetbatching**|Si les transactions sur le serveur de publication sont regroupées en ensembles cohérents sur le plan transactionnel pour un traitement ultérieur, elles sont nommées Xactsets. La valeur **Enabled** signifie que Xactsets peut être créé, ce qui correspond à la valeur par défaut. La valeur Disabled signifie que les Xactsets existants sont traités par aucun nouveau Xactsets n’est créé.|  
|**xactsetjob**|Indique si le travail Xactset est activé pour la création des Xactsets. La valeur **Enabled** signifie que la tâche Xactset s’exécute régulièrement pour créer des Xactsets sur le serveur de publication. La valeur Disabled signifie que les Xactsets sont créés uniquement par l’agent de lecture du journal lorsqu’il interroge le serveur de publication pour y rechercher des modifications.|  
|**xactsetjobinterval**|Intervalle entre les exécutions du travail Xactset, en minutes.|  
  
 Lorsque *PropertyName* est omis, toutes les propriétés définissables sont retournées.  
  
 [ **@propertyvalue** =] **'***PropertyValue***'**  
 Nouvelle valeur du paramètre de la propriété. *PropertyValue* est de **type sysname**, avec NULL comme valeur par défaut. Lorsque *PropertyValue* est omis, le paramètre actuel de la propriété est retourné.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**propertyname**|**sysname**|Retourne les propriétés de publication suivantes qui peuvent être définies :<br /><br /> **xactsetbatching**<br /><br /> **xactsetjob**<br /><br /> **xactsetjobinterval**|  
|**Balis**|**sysname**|Est le paramètre actuel de la propriété dans la colonne **PropertyName** .|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_publisherproperty** est utilisé dans la réplication transactionnelle pour les serveurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de publication non-.  
  
 Lorsque seul le serveur de *publication* est spécifié, le jeu de résultats comprend les paramètres actuels de toutes les propriétés qui peuvent être définies.  
  
 Lorsque *PropertyName* est spécifié, seule la propriété nommée apparaît dans le jeu de résultats.  
  
 Lorsque tous les paramètres sont spécifiés, la propriété est modifiée et aucun jeu de résultats n'est retourné.  
  
 Lorsque vous modifiez la propriété **xactsetjobinterval** d’un travail en cours d’exécution, vous devez redémarrer le travail pour que le nouvel intervalle prenne effet.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** sur le serveur de distribution peuvent exécuter **sp_publisherproperty**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer le travail d’un jeu de transactions pour un serveur de publication Oracle &#40;programmation Transact-SQL de la réplication&#41;](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
