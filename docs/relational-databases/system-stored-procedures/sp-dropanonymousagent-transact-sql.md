---
title: sp_dropanonymousagent (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 53f1cf56d422f615bca142276cf94306ada58a16
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="spdropanonymousagent-transact-sql"></a>sp_dropanonymousagent (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime du serveur de publication un Agent anonyme destiné à la surveillance de la réplication sur le serveur de distribution. Cette procédure stockée est exécutée sur n'importe quelle base de données du serveur de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropanonymousagent [ @subid= ] sub_id    , [ @type= ] type  
```  
  
## <a name="arguments"></a>Arguments  
 [  **@subid=**] *sub_id*  
 Est l’identificateur global d’un abonnement anonyme. *sub_id* est **uniqueidentifier**, sans valeur par défaut. Cet identificateur peut être récupéré sur l’abonné à l’aide de **sp_helppullsubscription**. La valeur de la **subid** champ du jeu de résultats retourné est à cet identificateur global.  
  
 [  **@type=**] *type*  
 Est le type d’abonnement. *type* est **int**, sans valeur par défaut. Les valeurs valides sont **1** ou **2**. Spécifiez **1**, si la réplication d’instantané ou réplication transactionnelle à l’aide de l’Agent de Distribution. Spécifiez **2**, si à l’aide de l’Agent de fusion de réplication de fusion.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropanonymousagent** est utilisée dans tous les types de réplication.  
  
 Cette procédure stockée permet de supprimer uniquement les Agents d'abonnement anonymes et ne permet pas de supprimer les abonnements connus.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **db_owner** du rôle de base de données fixe dans la base de données de distribution permettre exécuter **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
