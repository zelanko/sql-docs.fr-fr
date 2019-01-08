---
title: sp_dropanonymousagent (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropanonymousagent
- sp_dropanonymousagent_TSQL
helpviewer_keywords:
- sp_dropanonymousagent
ms.assetid: 4cb96efa-9358-44a3-a8ee-a7e181bed089
ms.author: vanto
manager: craigg
ms.openlocfilehash: dc5cc9c4d7bb7ca9b2d758e33142d140bf6fc6fa
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52818981"
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
 Est l’identificateur global d’un abonnement anonyme. *sub_id* est **uniqueidentifier**, sans valeur par défaut. Cet identificateur peut être récupéré sur l’abonné à l’aide de **sp_helppullsubscription**. La valeur dans le **subid** champ de jeu de résultats retourné est cet identificateur global.  
  
 [  **@type=**] *type*  
 Est le type d’abonnement. *type* est **int**, sans valeur par défaut. Les valeurs valides sont **1** ou **2**. Spécifiez **1**, si la réplication d’instantané ou réplication transactionnelle à l’aide de l’Agent de Distribution. Spécifiez **2**, si à l’aide de l’Agent de fusion de réplication de fusion.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropanonymousagent** est utilisée dans tous les types de réplication.  
  
 Cette procédure stockée permet de supprimer uniquement les Agents d'abonnement anonymes et ne permet pas de supprimer les abonnements connus.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **db_owner** du rôle fixe de base de données dans la base de données de distribution peuvent exécuter **sp_dropanonymousagent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
