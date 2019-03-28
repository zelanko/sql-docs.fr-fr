---
title: sp_replsetoriginator (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replsetoriginator
- sp_replsetoriginator_TSQL
helpviewer_keywords:
- sp_replsetoriginator
ms.assetid: 030e5226-0585-439f-b8cd-36f48367d86d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0f72558a573e0cee0ab7fb2ab9b762246964a884
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526181"
---
# <a name="spreplsetoriginator-transact-sql"></a>sp_replsetoriginator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Utilisée pour appeler un traitement et une détection en boucle au cours des réplications transactionnelles bidirectionnelles. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_replsetoriginator [ @server_name= ] 'server_name'   
    , [ @database_name= ] 'database_name'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @server_name = ] 'server_name'` Est le nom du serveur où la transaction est appliquée. *originating_server* est **sysname**, sans valeur par défaut.  
  
`[ @database_name = ] 'database_name'` Est le nom de la base de données où la transaction est appliquée. *originating_db* est **sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_replsetoriginator** est exécutée par l’Agent de Distribution pour enregistrer la source des transactions appliquées par réplication. Cette information est utilisée pour appeler une détection en boucle des abonnements transactionnels bidirectionnels qui possèdent le jeu de propriétés de la boucle.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du **sysadmin** rôle serveur fixe sur le serveur de publication, les membres de la **db_owner** rôle de base de données fixe sur la base de données de publication, ou les utilisateurs dans la liste d’accès aux publications (PAL) peuvent exécuter **sp_replsetoriginator**.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
