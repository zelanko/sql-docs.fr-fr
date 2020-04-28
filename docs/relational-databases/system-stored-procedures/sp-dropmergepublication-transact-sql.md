---
title: sp_dropmergepublication (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergepublication
- sp_dropmergepublication_TSQL
helpviewer_keywords:
- sp_dropmergepublication
ms.assetid: 9e1cb96e-5889-4f97-88cd-f60cf313ce68
author: stevestein
ms.author: sstein
ms.openlocfilehash: b675b07466464f706b6503f3d017acd34822b2c8
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67933900"
---
# <a name="sp_dropmergepublication-transact-sql"></a>sp_dropmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime une publication de fusion et l'Agent d'instantané qui lui est associé. Tous les abonnements doivent être supprimés avant de supprimer une publication de fusion. Les articles de la publication sont supprimés automatiquement. Cette procédure stockée est exécutée sur le serveur de publication dans la base de données de publication.  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropmergepublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
    [ , [ @ignore_merge_metadata = ] ignore_merge_metadata ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publication = ] 'publication'`Nom de la publication à supprimer. *publication* est de **type sysname**, sans valeur par défaut. Si **tout**est le cas, toutes les publications de fusion existantes sont supprimées, ainsi que le travail agent d’instantané qui leur est associé. Si vous spécifiez une valeur particulière pour la *publication*, seule la publication et le travail de agent d’instantané associé sont supprimés.  
  
`[ @ignore_distributor = ] ignore_distributor`Permet de supprimer une publication sans effectuer de tâches de nettoyage sur le serveur de distribution. *ignore_distributor* est de **bit**, avec **0**comme valeur par défaut. Ce paramètre est également utilisé lors de la réinstallation du serveur de distribution.  
  
`[ @reserved = ] reserved`Est réservé pour une utilisation ultérieure. la valeur *réservée* est de **bit**, avec **0**comme valeur par défaut.  
  
`[ @ignore_merge_metadata = ] ignore_merge_metadata`À usage interne uniquement.  
  
## <a name="return-code-values"></a>Codet de retour  
 **0** (succès) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropmergepublication** est utilisé dans la réplication de fusion.  
  
 **sp_dropmergepublication** supprime de manière récursive tous les articles associés à une publication, puis supprime la publication elle-même. Une publication ne peut être supprimée si elle fait l'objet d'un ou de plusieurs abonnements. Pour plus d’informations sur la suppression des abonnements, consultez [supprimer un abonnement par émission](../../relational-databases/replication/delete-a-push-subscription.md) de données et [supprimer un abonnement par extraction](../../relational-databases/replication/delete-a-pull-subscription.md).  
  
 L’exécution de **sp_dropmergepublication** pour supprimer une publication ne supprime pas les objets publiés de la base de données de publication ni les objets correspondants de la base de données d’abonnement. Utilisez l' \<> de suppression d’objet pour supprimer ces objets manuellement si nécessaire.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_dropmergepublication](../../relational-databases/replication/codesnippet/tsql/sp-dropmergepublication-_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres du rôle serveur fixe **sysadmin** ou du rôle de base de données fixe **db_owner** peuvent exécuter **sp_dropmergepublication**.  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimer une publication](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
