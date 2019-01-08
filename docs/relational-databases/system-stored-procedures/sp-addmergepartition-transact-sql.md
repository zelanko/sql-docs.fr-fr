---
title: sp_addmergepartition (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepartition
- sp_addmergepartition_TSQL
helpviewer_keywords:
- sp_addmergepartition
ms.assetid: 02a5f46b-e5ff-4932-a3ff-7f0fd82d0981
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 486faeb7d46ee32b40923cd54a018c2005c44621
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52760511"
---
# <a name="spaddmergepartition-transact-sql"></a>sp_addmergepartition (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Crée une partition filtrée dynamiquement pour un abonnement filtré par les valeurs de [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) ou [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) sur l’abonné. Cette procédure stockée, exécutée sur le serveur de publication dans la base de données en cours de publication, est utilisée pour générer manuellement des partitions.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_addmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>Arguments  
 [ **@publication**=] **'***publication***'**  
 Publication de fusion sur laquelle la partition est créée. *publication* est **sysname**, sans valeur par défaut. Si *suser_sname* est spécifié, la valeur de *nom d’hôte* doit être NULL.  
  
 [ **@suser_sname**=] **'***suser_sname***'**  
 Valeur utilisée lors de la création de la partition pour un abonnement qui est filtré par la valeur de la [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) fonction sur l’abonné. *SUSER_SNAME* est **sysname**, sans valeur par défaut.  
  
 [ **@host_name**=] **'***host_name***'**  
 Valeur utilisée lors de la création de la partition pour un abonnement qui est filtré par la valeur de la [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) fonction sur l’abonné. *HOST_NAME* est **sysname**, sans valeur par défaut.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_addmergepartition** est utilisé dans la réplication de fusion.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-addmergepartition-tra_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** rôle serveur fixe ou **db_owner** rôle de base de données fixe peuvent exécuter **sp_addmergepartition**.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un instantané d’une Publication de fusion avec des filtres paramétrés](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Filtres de lignes paramétrés](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
