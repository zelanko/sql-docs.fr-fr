---
title: sp_validatemergepublication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_validatemergepublication
- sp_validatemergepublication_TSQL
helpviewer_keywords:
- sp_validatemergepublication
ms.assetid: 5a862f1a-2be1-4758-9954-4cdc8c77d149
author: stevestein
ms.author: sstein
ms.openlocfilehash: 02ffdd0facfedd1b9eb6d8eee083f819566d818d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72006103"
---
# <a name="sp_validatemergepublication-transact-sql"></a>sp_validatemergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Effectue une validation sur l'ensemble d'une publication, dans laquelle tous les abonnements (par envoi de données, par extraction de données et anonymes) sont validés une fois. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_validatemergepublication [@publication=] 'publication'  
        , [ @level = ] level  
```  
  
## <a name="arguments"></a>Arguments  
 [**\@publication =**] **«***publication***»**  
 Nom de la publication. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @level = ] level`Type de validation à effectuer. *Level* est de **type tinyint**, sans valeur par défaut. Le paramètre « level » peut avoir l'une des valeurs suivantes :  
  
|Valeur de level (niveau)|Description|  
|-----------------|-----------------|  
|**1**|Validation du décompte de lignes uniquement.|  
|**2**|Validation du nombre de lignes et de la somme de contrôle. Pour [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]les abonnés, cette valeur est automatiquement définie sur **3**.|  
|**3**|Il s'agit de la valeur recommandée.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_validatemergepublication** est utilisé dans la réplication de fusion.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_validatemergepublication**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Valider les données répliquées](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [sp_validatemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-validatemergesubscription-transact-sql.md)  
  
  
