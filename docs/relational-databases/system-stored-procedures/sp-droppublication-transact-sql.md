---
title: sp_droppublication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_droppublication_TSQL
- sp_droppublication
helpviewer_keywords:
- sp_droppublication
ms.assetid: b52b37e6-4fec-40cf-abba-7dce4ff395fd
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3ef56f46696a2cb145804105d4d5f22fded6fe1f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830004"
---
# <a name="sp_droppublication-transact-sql"></a>sp_droppublication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Supprime une publication et l'Agent d'instantané qui lui est associé. Tous les abonnements doivent être supprimés avant de pouvoir supprimer une publication. Les articles de la publication sont supprimés automatiquement. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_droppublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication à supprimer. *publication* est de **type sysname**, sans valeur par défaut. Si **All** est spécifié, toutes les publications sont supprimées de la base de données de publication, à l’exception de celles qui ont des abonnements.  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_droppublication** est utilisé dans la réplication d’instantané et la réplication transactionnelle.  
  
 **sp_droppublication** supprime de manière récursive tous les articles associés à une publication, puis supprime la publication elle-même. Une publication ne peut être supprimée si elle fait l'objet d'un ou de plusieurs abonnements. Pour plus d’informations sur la suppression des abonnements, consultez [supprimer un abonnement par émission](../../relational-databases/replication/delete-a-push-subscription.md) de données et [supprimer un abonnement par extraction](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 L’exécution de **sp_droppublication** pour supprimer une publication ne supprime pas les objets publiés de la base de données de publication ni les objets correspondants de la base de données d’abonnement. Utilisez l' \<> de suppression d’objet pour supprimer ces objets manuellement si nécessaire.  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** peuvent exécuter **sp_droppublication**.  
  
## <a name="examples"></a>Exemples  
 [!code-sql[HowTo#sp_droppublication](../../relational-databases/replication/codesnippet/tsql/sp-droppublication-trans_1.sql)]  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer une publication](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addpublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
