---
title: sp_helppeerrequests (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppeerrequests_TSQL
- sp_helppeerrequests
helpviewer_keywords:
- sp_helppeerrequests
ms.assetid: 37bd503e-46c4-47c6-996e-be7ffe636fe8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5b9e2a370c9acc9c22dac7e5e60ceb10e08e46ba
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68137631"
---
# <a name="sp_helppeerrequests-transact-sql"></a>sp_helppeerrequests (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Retourne des informations sur toutes les demandes d’état reçues par les participants dans une topologie de réplication d’égal à égal, où ces demandes ont été lancées en exécutant [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md) dans une base de données publiée dans la topologie. Cette procédure stockée est exécutée sur la base de données de publication d'un serveur de publication participant à une topologie de réplication d'égal à égal. Pour plus d'informations, consultez [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_helppeerrequests [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication dans une topologie d’égal à égal pour laquelle des demandes d’État ont été envoyées. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @description = ] 'description'`Valeur qui peut être utilisée pour identifier des demandes d’État individuelles, ce qui vous permet de filtrer les réponses retournées en fonction des informations définies par l’utilisateur fournies lors de l’appel de [sp_requestpeerresponse &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql.md). *Description* est de **%** type **nvarchar (4000)**, avec la valeur par défaut. Toutes les demandes d'état sont par défaut retournées pour la publication. Ce paramètre est utilisé pour retourner uniquement les demandes d’État avec une description correspondant à la valeur fournie dans *Description*, où les chaînes de caractères sont mises en correspondance à l’aide d’une clause [Like &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md) .  
  
## <a name="result-sets"></a>Jeux de résultats  
  
|Nom de la colonne|Type de données|Description|  
|-----------------|---------------|-----------------|  
|**identifi**|**int**|Identifie une demande.|  
|**édition**|**sysname**|Nom de la publication pour laquelle la demande d'état a été envoyée.|  
|**sent_date**|**DATETIME**|Date et heure d'envoi de la demande d'état.|  
|**description**|**nvarchar(4000)**|Informations définies par l'utilisateur que vous pouvez utiliser pour identifier les demandes d'état.|  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_helppeerrequests** est utilisé dans la réplication transactionnelle d’égal à égal.  
  
 **sp_helppeerrequests** est utilisé lors de la restauration d’une base de données publiée dans une topologie d’égal à égal.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_helppeerrequests**.  
  
## <a name="see-also"></a>Voir aussi  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md)  
  
  
