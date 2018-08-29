---
title: sp_helppeerrequests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_helppeerrequests_TSQL
- sp_helppeerrequests
helpviewer_keywords:
- sp_helppeerrequests
ms.assetid: 37bd503e-46c4-47c6-996e-be7ffe636fe8
caps.latest.revision: 21
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ba660dbcaf09b3df5890032ab0f1b428cce7860e
ms.sourcegitcommit: 182b8f68bfb345e9e69547b6d507840ec8ddfd8b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43028099"
---
# <a name="sphelppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur toutes les demandes d’état reçues par les participants dans une topologie de réplication d’égal à égal, où ces demandes sont lancées en exécutant [sp_requestpeerresponse &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) à tout base de données publiée dans la topologie. Cette procédure stockée est exécutée sur la base de données de publication d'un serveur de publication participant à une topologie de réplication d'égal à égal. Pour plus d'informations, consultez [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helppeerrequests [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publication**=] **'***publication***'**  
 om de la publication dans une topologie d'égal à égal pour laquelle des demandes d'état ont été envoyées. *publication* est **sysname**, sans valeur par défaut.  
  
 [ **@description**=] **'***description***'**  
 Valeur qui peut être utilisé pour identifier les demandes d’état individuelles, ce qui permet vous permettent de filtrer les réponses retournées en fonction de l’utilisateur défini par les informations fournies lors de l’appel [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md). *Description* est **nvarchar (4000)**, avec une valeur par défaut **%**. Toutes les demandes d'état sont par défaut retournées pour la publication. Ce paramètre est utilisé pour retourner uniquement les demandes d’état avec la description correspond à la valeur fournie dans *description*, où les chaînes de caractères sont mises en correspondance avec un [comme &#40;Transact-SQL&#41; ](../../t-sql/language-elements/like-transact-sql.md)clause.  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**id**|**Int**|Identifie une demande.|  
|**publication**|**sysname**|Nom de la publication pour laquelle la demande d'état a été envoyée.|  
|**sent_date**|**datetime**|Date et heure d'envoi de la demande d'état.|  
|**description**|**nvarchar(4000)**|Informations définies par l'utilisateur que vous pouvez utiliser pour identifier les demandes d'état.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helppeerrequests** est utilisé dans la réplication transactionnelle peer-to-peer.  
  
 **sp_helppeerrequests** est utilisé lors de la restauration d’une base de données publiée dans une topologie d’égal à égal.  
  
## <a name="permissions"></a>Permissions  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou le **db_owner** rôle de base de données fixe peuvent exécuter **sp_helppeerrequests**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
