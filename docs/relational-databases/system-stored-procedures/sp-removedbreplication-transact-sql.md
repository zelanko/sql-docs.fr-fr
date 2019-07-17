---
title: sp_removedbreplication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_removedbreplication
- sp_removedbreplication_TSQL
helpviewer_keywords:
- sp_removedbreplication
ms.assetid: cb98d571-d1eb-467b-91f7-a6e091009672
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7d3931ff867ef1475165eb6cbac97f4ba4564bf9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006958"
---
# <a name="spremovedbreplication-transact-sql"></a>sp_removedbreplication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Cette procédure stockée supprime tous les objets de réplication sur la base de données de publication de l'instance de serveur de publication de SQL Server ou sur la base de données d'abonnement de l'instance de l'abonné de SQL Server. Procédez à l'exécution dans la base de données appropriée, ou si l'exécution est dans le contexte d'une autre base de données sur la même instance, spécifiez la base de données où les objets de réplication doivent être supprimés. Cette procédure ne supprime pas les objets à partir d'autres bases de données, telles que la base de données de distribution.  
  
> [!NOTE]  
>  Cette procédure ne doit être utilisée que si les autres méthodes de suppression d'objets de réplication ont échoué.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_removedbreplication [ [ @dbname = ] 'dbname' ]  
    [ , [ @type = ] type ]   
```  
  
## <a name="arguments"></a>Arguments  
`[ @dbname = ] 'dbname'` Est le nom de la base de données. *dbname* est de type **sysname**, avec NULL comme valeur par défaut. Lorsque la valeur est NULL, la base de données actuelle est utilisée.  
  
`[ @type = ] type` Est le type de réplication pour la base de données des objets doivent être supprimés. *type* est **nvarchar (5)** et peut prendre l’une des valeurs suivantes.  
  
|||  
|-|-|  
|**tran**|Supprime les objets de publication dans une réplication transactionnelle.|  
|**merge**|Supprime les objets de publication dans une réplication de fusion.|  
|**les deux** (valeur par défaut)|Supprime tous les objets de publication de la réplication.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_removedbreplication** est utilisée dans tous les types de réplication.  
  
 **sp_removedbreplication** est utile lorsque vous restaurez une base de données répliquée qui ne comporte aucun objet de réplication doit être restauré.  
  
 **sp_removedbreplication** ne peut pas être utilisé sur une base de données est marquée comme étant en lecture seule.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/sp-removedbreplication-t_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_removedbreplication**.  
  
## <a name="example"></a>Exemple  
  
```  
-- Remove replication objects from the subscription database on MYSUB.  
DECLARE @subscriptionDB AS sysname  
SET @subscriptionDB = N'AdventureWorksReplica'  
  
-- Remove replication objects from a subscription database (if necessary).  
USE master  
EXEC sp_removedbreplication @subscriptionDB  
GO  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Désactiver la publication et la distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
