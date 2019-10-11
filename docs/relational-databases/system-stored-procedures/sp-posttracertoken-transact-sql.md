---
title: sp_posttracertoken (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- posttracerttoken
- posttracerttoken_TSQL
- sp_posttracertoken
- sp_posttracertoken_TSQL
helpviewer_keywords:
- sp_posttracertoken
ms.assetid: 24da5cd2-1c45-475e-93db-5bdf660f1c2c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7629c25264f0b45d68e29e947b1d5c40d02707e7
ms.sourcegitcommit: 512acc178ec33b1f0403b5b3fd90e44dbf234327
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72041182"
---
# <a name="sp_posttracertoken-transact-sql"></a>sp_posttracertoken (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette procédure publie un jeton de suivi dans le journal des transactions sur le serveur de publication et commence le processus de suivi des statistiques de latence. Les informations sont enregistrées lorsque le jeton de suivi est écrit dans le journal des transactions, lorsqu'il est repris par l'Agent de lecture du journal et lorsqu'il est appliqué par l'Agent de distribution. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication. Pour plus d’informations, voir [Mesurer la latence et valider les connexions pour la réplication transactionnelle](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md).  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_posttracertoken [ @publication = ] 'publication'   
    [ , [ @tracer_token_id = ] tracer_token_id OUTPUT  
    [ , [ @publisher = ] 'publisher'   
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'` est le nom de la publication pour laquelle la latence est mesurée. *publication* est de **type sysname**, sans valeur par défaut.  
  
`[ @tracer_token_id = ] _tracer_token_id OUTPUT` est l’ID du jeton de suivi inséré. *tracer_token_id* est de **type int** avec NULL comme valeur par défaut et il s’agit d’un paramètre OUTPUT. Cette valeur peut être utilisée pour exécuter [sp_helptracertokenhistory &#40;Transact-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-helptracertokenhistory-transact-sql.md) ou [sp_deletetracertokenhistory &#40;Transact&#41; ](../../relational-databases/system-stored-procedures/sp-deletetracertokenhistory-transact-sql.md) -SQL sans d’abord exécuter [sp_helptracertokens &#40;Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sp-helptracertokens-transact-sql.md).  
  
`[ @publisher = ] 'publisher'` spécifie un serveur de publication non-[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *Publisher* est de **type sysname**, avec NULL comme valeur par défaut et ne doit pas être spécifié pour un serveur de publication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_posttracertoken** est utilisé dans la réplication transactionnelle.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_tracertokens](../../relational-databases/replication/codesnippet/tsql/sp-posttracertoken-trans_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_posttracertoken**.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesurer la latence et valider les connexions pour la réplication transactionnelle](../../relational-databases/replication/monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
