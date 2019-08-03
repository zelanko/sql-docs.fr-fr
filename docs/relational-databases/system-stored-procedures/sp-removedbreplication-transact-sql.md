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
ms.openlocfilehash: fdae843c3918013ec850c5d807853c10a8f3f190
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771039"
---
# <a name="spremovedbreplication-transact-sql"></a>sp_removedbreplication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

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
`[ @dbname = ] 'dbname'`Nom de la base de données. *dbname* est de type **sysname**, avec NULL comme valeur par défaut. Lorsque la valeur est NULL, la base de données actuelle est utilisée.  
  
`[ @type = ] type`Type de réplication pour lequel les objets de base de données sont supprimés. le *type* est **nvarchar (5)** et peut prendre l’une des valeurs suivantes.  
  
|||  
|-|-|  
|**tran**|Supprime les objets de publication dans une réplication transactionnelle.|  
|**merge**|Supprime les objets de publication dans une réplication de fusion.|  
|**les deux** valeurs|Supprime tous les objets de publication de la réplication.|  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_removedbreplication** est utilisé dans tous les types de réplications.  
  
 **sp_removedbreplication** est utile lors de la restauration d’une base de données répliquée qui n’a pas d’objets de réplication nécessitant une restauration.  
  
 **sp_removedbreplication** ne peut pas être utilisé avec une base de données marquée en lecture seule.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_removedbreplication](../../relational-databases/replication/codesnippet/tsql/sp-removedbreplication-t_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_removedbreplication**.  
  
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
  
  
