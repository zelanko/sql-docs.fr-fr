---
title: sp_script_synctran_commands (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_script_synctran_commands
- sp_script_synctran_commands_TSQL
helpviewer_keywords:
- sp_script_synctran_commands
ms.assetid: f132694a-dd05-405b-9d84-21acce9e564a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a9ee35eb4c5d67ff50f4f08c1cfa29596e27aec2
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536174"
---
# <a name="spscriptsynctrancommands-transact-sql"></a>sp_script_synctran_commands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Génère un script qui contienne le **sp_addsynctrigger** appels à appliquer aux abonnés pour les abonnements d’être mise à jour. Il y a un **sp_addsynctrigger** appeler pour chaque article de la publication. Le script généré contient également le **sp_addqueued_artinfo** appels qui créent le **MSsubsciption_articles** table qui est nécessaire pour traiter les publications en file d’attente. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_script_synctran_commands [@publication = ] 'publication'  
    [ , [@article = ] 'article']  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` Est le nom de la publication à écrire. *publication* est **sysname**, sans valeur par défaut.  
  
`[ @article = ] 'article'` Est le nom de l’article à écrire. *article* est **sysname**, avec une valeur par défaut **tous les**, qui spécifie tous les articles sont écrites.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="results-set"></a>Ensemble de résultats  
 **sp_script_synctran_commands** retourne un jeu de résultats qui se compose d’un seul **nvarchar (4000)** colonne. Le jeu de résultats forme les scripts complets nécessaires pour créer les le **sp_addsynctrigger** et **sp_addqueued_artinfo** appels à appliquer aux abonnés.  
  
## <a name="remarks"></a>Notes  
 **sp_script_synctran_commands** est utilisé dans la réplication transactionnelle et d’instantané.  
  
 **sp_addqueued_artinfo** est utilisé pour les abonnements de mettre à jour en file d’attente.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_script_synctran_commands**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_addsynctriggers &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsynctriggers-transact-sql.md)   
 [sp_addqueued_artinfo &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addqueued-artinfo-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
