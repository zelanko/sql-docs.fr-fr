---
title: sp_dropdistpublisher (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropdistpublisher
- sp_dropdistpublisher_TSQL
helpviewer_keywords:
- sp_dropdistpublisher
ms.assetid: c0bdd3de-3be0-455c-898a-98d4660e7ce3
author: stevestein
ms.author: sstein
ms.openlocfilehash: fcb1487d4291116bfb6fc0ad266b147e0fd69981
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67927836"
---
# <a name="spdropdistpublisher-transact-sql"></a>sp_dropdistpublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Supprime un serveur de publication de distribution. Cette procédure stockée est exécutée sur le serveur de distribution sur une base de données.  
  
 ![Icône de lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_dropdistpublisher [ @publisher = ] 'publisher'  
    [ , [ @no_checks = ] no_checks ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>Arguments  
`[ @publisher = ] 'publisher'` Est le serveur de publication à supprimer. *serveur de publication* est **sysname**, sans valeur par défaut.  
  
`[ @no_checks = ] no_checks` Spécifie si **sp_dropdistpublisher** vérifie que le serveur de publication a bien désinstallé le serveur comme serveur de distribution. *no_checks* est **bits**, avec une valeur par défaut **0**.  
  
 Si **0**, réplication vérifie que le serveur de publication distant a désinstallé le serveur local comme serveur de distribution. Si le serveur de publication est local, la réplication vérifie qu'il ne reste aucun objet de publication ou de distribution sur le serveur local.  
  
 Si **1**, tous les objets de réplication associés à l’éditeur de distribution sont supprimés, même si un serveur de publication distant ne peut pas être atteint. Après cette opération, le serveur de publication distant doit désinstaller à l’aide de la réplication [sp_dropdistributor](../../relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql.md) avec **@ignore_distributor**  =  **1**.  
  
`[ @ignore_distributor = ] ignore_distributor` Spécifie si les objets de distribution sont conservés sur le serveur de distribution lorsque le serveur de publication est supprimé. *ignore_distributor* est **bits** et peut prendre l’une des valeurs suivantes :  
  
 **1** = appartenant à des objets de distribution le *publisher* restent sur le serveur de distribution.  
  
 **0** = des objets de distribution pour le *publisher* sont nettoyées au niveau du serveur de distribution.  
  
## <a name="return-code-values"></a>Valeurs des codes de retour  
 **0** (réussite) ou **1** (échec)  
  
## <a name="remarks"></a>Notes  
 **sp_dropdistpublisher** est utilisée dans tous les types de réplication.  
  
 Lors de la suppression d’un serveur de publication Oracle, s’il est impossible de supprimer le serveur de publication **sp_dropdistpublisher** renvoie une erreur et les objets de serveur de distribution pour le serveur de publication sont supprimés.  
  
## <a name="example"></a>Exemple  
 [!code-sql[HowTo#sp_DropDistPub](../../relational-databases/replication/codesnippet/tsql/sp-dropdistpublisher-tra_1.sql)]  
  
## <a name="permissions"></a>Autorisations  
 Seuls les membres de la **sysadmin** du rôle serveur fixe peuvent exécuter **sp_dropdistpublisher**.  
  
## <a name="see-also"></a>Voir aussi  
 [Désactiver la publication et la distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_changedistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql.md)   
 [sp_helpdistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)   
 [Procédures stockées de réplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
