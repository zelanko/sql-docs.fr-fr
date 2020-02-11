---
title: sp_requestpeertopologyinfo (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_requestpeertopologyinfo
- sp_requestpeertopologyinfo_TSQL
helpviewer_keywords:
- sp_requestpeertopologyinfo
ms.assetid: 15cd28bd-5a72-41fb-ae1b-726baaa6fad5
author: stevestein
ms.author: sstein
ms.openlocfilehash: d137706da49f666ce66abea52249796a0094c7e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129663"
---
# <a name="sp_requestpeertopologyinfo-transact-sql"></a>sp_requestpeertopologyinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Remplit la table système [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) avec des informations sur une topologie de réplication transactionnelle d’égal à égal. Exécutez [sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md) pour obtenir des informations à partir de la table au format XML.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_requestpeertopologyinfo [ @publication = ] 'publication'  
        [ ,[ @requestid=] request_id OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
 [ @publication= ] «*publication*»  
 Nom de la publication pour laquelle effectuer une demande de statut à l'échelle de la topologie. *publication* est de **type sysname**, sans valeur par défaut.  
  
 [ @request_id= ] *request_id*  
 Numéro d'identification affecté à la demande de statut de topologie. *request_id* est de **type int**, avec NULL comme valeur par défaut. Cet ID peut être utilisé par [sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md).  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 sp_requestpeertopologyinfo est utilisé dans la réplication transactionnelle d'égal à égal. Exécutez sp_requestpeertopologyinfo avant d’exécuter [sp_gettopologyinfo](../../relational-databases/system-stored-procedures/sp-gettopologyinfo-transact-sql.md). Ces procédures sont utilisées par l'Assistant Configurer la topologie d'égal à égal, mais ils peuvent également être utilisés directement si vous avez besoin d'informations de topologie dans un format XML. Si vous préférez des résultats tabulaires, interrogez la table système [MSpeer_topologyresponse](../../relational-databases/system-tables/mspeer-topologyresponse-transact-sql.md) .  
  
## <a name="permissions"></a>Autorisations  
 Requiert l'appartenance au rôle serveur fixe sysadmin ou au rôle de base de données fixe db_owner.  
  
## <a name="see-also"></a>Voir aussi  
 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
