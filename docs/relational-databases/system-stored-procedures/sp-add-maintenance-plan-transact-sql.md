---
title: sp_add_maintenance_plan (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_add_maintenance_plan
- sp_add_maintenance_plan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_maintenance_plan
ms.assetid: 01ab1834-6260-47cb-a1b7-20722217b062
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aa33e418b81cb2f77a39f20d36bba7a25caffb4c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68104584"
---
# <a name="sp_add_maintenance_plan-transact-sql"></a>sp_add_maintenance_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Ajoute un plan de maintenance et retourne l'ID du plan.  
  
> [!NOTE]  
>  Cette procédure stockée s'utilise avec des plans de maintenance de base de données. Cette fonctionnalité a été remplacée par des plans de maintenance qui n'utilisent pas cette procédure stockée. Utilisez cette procédure pour gérer des plans de maintenance de base de données sur des installations qui ont été mises à niveau à partir d'une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_add_maintenance_plan [ @plan_name = ] 'plan_name' ,   
     @plan_id = 'plan_id' OUTPUT  
```  
  
## <a name="arguments"></a>Arguments  
`[ @plan_name = ] 'plan_name'`Spécifie le nom du plan de maintenance à ajouter. *plan_name* est **de type varchar (128)**.  
  
 ** ** @plan_id = '** plan_id **'**  
 Spécifie l'identificateur du plan de maintenance. *plan_id* est de type **uniqueidentifier**.  
  
## <a name="return-code-values"></a>Codet de retour  
 0 (réussite) ou 1 (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_add_maintenance_plan** doit être exécutée à partir de la base de données **msdb** et crée un plan de maintenance, mais vide. Pour ajouter une ou plusieurs bases de données et les associer à un travail ou des travaux, exécutez **sp_add_maintenance_plan_db** et **sp_add_maintenance_plan_job**.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_add_maintenance_plan**.  
  
## <a name="examples"></a>Exemples  
 Création d'un plan de maintenance appelé Myplan.  
  
```  
DECLARE   @myplan_id UNIQUEIDENTIFIER;  
EXECUTE   sp_add_maintenance_plan N'Myplan',@plan_id=@myplan_id OUTPUT  
PRINT   'The id for the maintenance plan "Myplan" is:'+convert(varchar(256),@myplan_id);  
GO  
```  
  
 Si la création du plan de maintenance se déroule correctement, l'ID du plan est retourné.  
  
```  
'The id for the maintenance plan "Myplan" is:' FAD6F2AB-3571-11D3-9D4A-00C04FB925FC  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Plans de maintenance](../../relational-databases/maintenance-plans/maintenance-plans.md)   
 [Procédures stockées de plan de maintenance de base de données &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-maintenance-plan-stored-procedures-transact-sql.md)  
  
  
